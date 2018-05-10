title: Hintergrundbeleuchtung für eine analoge Wanduhr
link: https://cronj.de/2012/11/22/hintergrundbeleuchtung-fur-eine-analoge-wanduhr/
author: Alex
description: 
post_id: 127
created: 2012/11/22 10:05:01
created_gmt: 2012/11/22 09:05:01
comment_status: open
post_name: hintergrundbeleuchtung-fur-eine-analoge-wanduhr
status: publish
post_type: post

# Hintergrundbeleuchtung für eine analoge Wanduhr

Als Brillenträger habe ich Probleme die Uhr im Dunkeln zu erkennen. Da ich aber eine sehr schicke Uhr mit einem gläsernen Ziffernblatt habe, bietet es sich an diese Uhr von hinten zu beleuchten. Um aber die Beleuchtung so einfach wie möglich zu aktivieren, muss eine drahtlose Lösung her. 

## Wahl der Bauteile

Zur Verwendung kommen sollen nur schon bereits vorhandene Teile, um für diese Spielerei nicht all zu starke Kosten zu verursachen: 

  * Weiße LEDs (5mm)
  * Konstantstromquelle
  * Atmel AVR
  * <del>Relais</del>
  * IRLR024N D-PAK N-Kanal FET
  * TSOP1738
  * LM7805
  * altes Laptopnetzteil (18V)
Nach ein paar Tests mit dem Relais hat sich raus gestellt, dass es deutlich zuviel Strom zieht. Der LM7805 muss 13V * 17mA = 221mW in Wärme umwandeln (Leerlauf). Wenn das Relais schaltet, steigt der Strom auf 150mA was dann 1,95W an Wärme entspricht. Ich habe zwar einen alten Chipkühler 30x30x8 (LxBxH) vorgesehen, aber den Platz kann ich mir bei Verwendung eines FET als Schalter sparen. 

## RC-5 Protokoll

Die verwendete Fernbedienung ist von der Firma Sony und gehört zu meinem Blu-Ray Player (Model der Fernbedienung: RMT-B109P). In der Mitte befindet sich ein Steuerkreuz mit einer gut erreichbaren, runden Taste. Sony verwendet ein eigenes Protokoll für seine Fernbedienungen (SIRCS). Ein Kommando beginnt mit einem Startbit, gefolgt von 7 Befehlsbits und 12 bis 20 Adressbits. High und Low Pegel werden durch die unterschiedliche Pulsweite bestimmt. Folgende Pulsweiten sind vorhanden: 

  * Startbit - Länge: 3000µs (2400µs High; 600µs Low)
  * logische 0 - Länge: 1200µs (600µs High; 600µs Low)
  * logische 1 - Länge: 1800µs (1200µ High; 600µs Low)
Die einzelnen Kommandos werden 2-3 mal wiederholt. Dabei gibt es eine Pause von 45ms zwischen den Wiederholungen. Um den Befehl der Taste zu bestimmen, habe ich den TSOP1738 mit Spannung versorgt und das Ausgangssignal an mein Oszilloskop angeschlossen. Mit Hilfe der Cursor kann ich dann durch die einzelnen Bits gehen und mir die Zustände aufschreiben. Mein Befehl hat folgenden Aufbau: 
    
    
    Startbit;101.1110;0.1011.0100.0111;
            | Befehl |    Adresse     |
               0x5E        0x0B47

Wichtig für mich ist nur der Befehl. Ich besitze nur zwei Fernbedienungen und eine davon sendet über Funk, so dass ich keine Unterscheidung über die Adresse brauche. 

## Auswertung

Die Verarbeitung des Signals, welches aus dem TSOP1738 kommt, übernimmt ein Atmel ATmega8. Dafür wird die Input Capture Funktion des Timers verwendet. Bei einer fallenden Flanke wird hier eine Variable auf 0 gesetzt und der Timer zählt diese bis zur nächsten fallenden Flanke hoch. Die Zeit die zwischen den beiden Flanken verstreicht, wird dann unterschieden in Startbit, 0 oder 1. Fallende Flanke deshalb, da das Signal aus dem TSOP1738 invertiert ausgegeben wird. Der Timer wird hierfür entsprechend initialisiert: 
    
    
    // Initialize Timer1
    void InitTimer1()
    {
    	// Falling edge detection | clk/64= 4µs
    	TCCR1B |= ((1 << CS11) | (1 << CS10));
    
    	// Input Capture Interrupt enable
    	TIMSK |= (1 << TICIE1);
    
    	// Configure input for TSOP1738 signal
    	RC5_DDR &= ~(1 << RC5_IN);
    }

Die Interrupt Routine sieht so aus: 
    
    
    // Calculate time between two falling edges in the interrupt
    ISR(TIMER1_CAPT_vect)
    {
    	// Set counter to zero (TCNT1 is now in ICR1)
    	TCNT1 = 0;
    
    	// Read the Input Capture Registers
    	ICRValue = ICR1;
    
    	// go through the bits
    	if (CmdDone == 0 && CmdMatch != 1)
    	{
    		// Wait until startbit detected
    		if (StartBit == 0)
    		{
    			if (ICRValue > 740 && ICRValue < 760)
    			{
    				StartBit = 1;
    			}
    		}
    		// If startbit is detected, sample new command
    		else
    		{
    			// If time between two falling edges is 1800µs (range: 1760us - 1840us)
    			if (ICRValue > 440 && ICRValue < 460)
    			{
    				// Set bit at this position to 1
    				RC5_cmd_val |= (1 << --CmdBitNumber);
    			}
    			else
    			{
    				// CmdBitNumber minus 1 -> bit at this position stays 0
    				CmdBitNumber--;
    			}
    			// If 7 bits are sampled, set CmdDone to 1
    			if (CmdBitNumber == 0)
    			{
    				CmdDone = 1;
    			}
    		}
    	}
    }

Die Routine wartet bis es ein Startbit erkennt um nicht mitten im Kommando anzufangen. Wenn dies erkannt wurde geht es die nächsten 7 Bits (ich möchte ja nur den Befehl haben) durch und setzt jeweils das entprechende Bit auf 0 oder 1. Es wartet dann bis die Hauptschleife den Befehl geprüft hat. Wenn die Hauptfunktion keine Übereinstimmung mit dem gewünschten Befehl erkennt, gibt sie über die Variable CmdDone der Interruptroutine Bescheid, dass ein neuer Befehl zusammen gesetzt werden darf. Wenn der gewünschte Befehl erkannt wurde, wird dies der Interruptroutine mit der Variable CmdMatch mitgeteilt. Gleichzeitig wird ein zweiter Timer gestartet und der Ausgang für die Beleuchtung eingeschaltet. Der Timer schaltet nach 5 Sekunden den Ausgang wieder aus und bereitet alles vor, so dass ein neuer Befehl zusammen gesetzt werden kann. Den kompletten und aktuellen Code gibt es auf GitHub: [RC5ControlledClocklight (GitHub)](https://github.com/cronJ/RC5ControlledClocklight)

## Schaltung

Der aktuelle Eagle-Schaltplan sieht so aus (Änderung am FET): ![version1](/wp-content/uploads/2012/11/version1-300x165.png) Das aktuelle Layout sieht so aus: 

![](/wp-content/uploads/2012/11/version1_brd-300x226.png)

Es wird ein 1-seitiges PCB erstellt. Das bedeutet die beiden Leiterbahnen auf dem Top-Layer sind anschließend als Drahtbrücken ausgeführt. Die beiden Befestigungsbohrungen sind nicht auf ein spezielles Gehäuse angepasst. Werden also später einfach mit zwei Abstandhaltern und Heißkleber im Gehäuse befestigt. Zur Sicherheit drucke ich das Layout immer im Maßstab 1:1 aus, um die Positionierung der Bauteile zu prüfen. Diese Vorgehensweise hat sich schon oft bewährt und auch diesmal fallen einem zwei Probleme auf. Es ist allerdings kein Problem mit der Positionierung, sondern das auf dem Board verwendete Package des FET und Spannungswandler, ist falsch: ![IMG_20121202_160539](/wp-content/uploads/2012/11/IMG_20121202_1605391-225x300.jpg) Ich werde nun also die beiden fehlerhaften Packages korrigieren, und den 7805 um 90° drehen. Dann hat er etwas mehr Platz. Und so sieht das geänderte Layout aus: ![](https://cronj.de/wp-content/uploads/2012/11/version1_brd2-300x226.png) Und der Test nach dem Ausdruck: ![IMG_20121202_170523](https://cronj.de/wp-content/uploads/2012/11/IMG_20121202_170523-300x225.jpg)