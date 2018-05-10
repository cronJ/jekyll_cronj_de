---
layout: post
title: "NodeMcu auf ESP8266  (ESP-01 Modul)"
date: 2015-01-31 21:52:32 +0200
categories: electronic
---
# [There is an updated article to get the NodeMCU firmware running in the year 2016! >> click me <<](/electronic/2016/01/24/getting-nodemcu-running-on-an-ESP-01-module-in-2016.html)

# Änderungen:
24.01.2016 - Bild mit (selbst definierten) Pinnummern eingefügt und Signale den Nummern zugeordnet. Hat mich selbst gerade wieder Zeit gekostet, das zusammen zu suchen. 

* * *

Kleines Protokoll für das Flashen von [NodeMcu](http://www.nodemcu.com/index_en.html) auf das ESP-01 Modul.

Benötigte Hardware: 
* ESP-01 Modul
* FTDI UM232R

Benötigte Software: 
* Git
* Python 2
* Hterm (Zur späteren Kontrolle)

# Modulverbindung
Definition der Nummerierung und Zuordnung der Pinnamen:

{% include image.html path="/images/2015/01/" img="ESP-01_PinNumber" type="png" desc="ESP-01_PinNumber" %}

1. GND
2. UTXD
3. GPIO2
4. CH_PD
5. GPIO0
6. RST/GPIO16
7. URXD
8. VCC

Folgende Verschaltung hat bei mir auf Anhieb funktioniert:
{% highlight text %}
VCC   -> 3V3
GND   -> GND
RST   -> 3V3
CH_PD -> 3V3
URXD  -> DB0 (UM232R)
UTXD  -> DB1 (UM232R)
GPIO0 -> GND
GPIO2 -> 3V3
{% endhighlight %}

JP1 auf dem UM232R auf 1-2 gesetzt (3V3 IO). Die 3,3V Spannungsversorgung erfolgt mit einem Labornetzteil. 

# Vorbereitung für das Flashen
Das benötigte Tool zum Flashen laden: 

{% highlight text %}
git clone https://github.com/themadinventor/esptool.git
{% endhighlight %}

Dann NodeMcu laden: 

{% highlight text %}
git clone https://github.com/nodemcu/nodemcu-firmware.git
{% endhighlight %}

Dort die Datei **nodemcu_latest.bin** aus dem Ordner ./pre_build/latest/ in das esptool Verzeichnis kopieren. Es würde auch ausreichen, nur das Binary von Github zu laden. 

# Neue Firmware flashen
Nun kann die neue Firmware auf das Modul geladen werden. Das Modul hat hier die Portnummer 11. Gegebenenfalls im Gerätemanager die korrekte Portnummer ausfindig machen. 

{% highlight text %}
python esptool.py --port COM11 write_flash 0x0000 nodemcu_latest.bin
{% endhighlight %}

Bei Problemen mit dem serial Modul (Modul nicht gefunden): 

{% highlight text %}
pip install pyserial
{% endhighlight %}

Bei Verbindungsproblemen, den CH_PD Pin von den 3V3 trennen und wieder verbinden. Evtl. so lange wiederholen, bis der Flash-Vorgang beginnt. 

# Firmware testen
Mit Hterm eine Verbindung zu dem Modul aufbauen. Dafür den passenden Port auswählen (hier COM11) und die Übertragungsrate auf 9600Baud setzen. Newline auf CR+LF (Carriage Return und Line Feed). Bei "Input control" den Typ auf ASCII und CR-LF bei "send on enter" einstellen. Nach einem Modulreset sollte dann folgender Text erscheinen, je nach Version: 
    
{% highlight text %}
NodeMCU 0.9.5 build 20150127 &nbsp;powered by Lua 5.1.4
lua: cannot open init.lua>
{% endhighlight %}

Für einen einfachen Test wurde eine LED mit Vorwiderstand zwischen GPIO0 und GND geschaltet. Mit folgenden Befehlen kann sie nun über das Terminal gesteuert werden: 
    
{% highlight lua %}
gpio.mode(3, gpio.OUTPUT) -- GPIO als Ausgang setzen
gpio.write(3, 1)          -- GPIO HIGH schalten
gpio.write(3, 0)          -- GPIO LOW schalten
{% endhighlight %}

Die 3 steht für den IO Index. GPIO0 hat den IO Index 3 und nicht 0 wie zu erwarten wäre. Weitere IO Indizes findet man hier: [GPIO Map](https://github.com/nodemcu/nodemcu-firmware/wiki/nodemcu_api_en#new_gpio_map) Weitere Tests mit komplexeren LUA Skripten folgen...