---
layout: post
title: "3D printing goes in round two"
date: 2015-12-24 11:46:00 +0200
categories: 3d-printer
---
After printing a good amount of filament with my GRR Neo, the 3D printer is a valuable tool for me which I don't want to miss. Most of the time I create the parts which I want to print by myself. Therefor I'm using OpenSCAD or Autodesk Fusion 360.

Nach dem ich mit dem GRR Neo nun einige Kilogramm Filament verdruckt habe, kann ich für mich sagen, dass sich die Anschaffung eines solchen Werkzeuges gelohnt hat. Ab und zu drucke ich auch mal ein interessantes Teil von Thingiverse, aber hauptsächlich erstelle ich die Teile selbst, das ist schneller als etwas zu suchen (und nicht zu finden) und ich kann die Teile an die Eigenarten meines Druckers anpassen um schöne Endprodukte zu erhalten. Meine benötigten Teile erstelle ich mittlerweile mit Hilfe von OpenSCAD oder Autodesk Fusion 360.

As good as the GRR Neo is, some things are bothering me. For a good print the calibration of the print bed is essentially. How it works on the GRR Neo is described in the previous post. For most prints I'm calibrating the bed level during the printing of the skirt. The back of the printer faces a wall so changing the filament is quiet difficult to handle. After attaching the filament roll you have to insert the filament into the bowden tube, which also is on the back and not easy to reach.

So schön der GRR Neo auch ist, einige Sachen waren für mich nervig. Die Druckbettkalibrierung ist das A und O für einen funktionierenden Druck. Wie die Kalibierung funktioniert, habe ich im letzten Artikel beschrieben. Meistens habe ich aber während dem Druck vom Skirt den Abstand noch feinjustiert damit es passt. Mein Drucker steht mit der Rückseite zur Wand. Dadurch war ein Filamentwechsel immer ein Akt. Das Filament in den Bowdenzug des Extruders zu schieben, welcher sich ebenfalls hinten befindet, liess mich so manches Mal fluchen.

All in all I was very happy with this printer.

Das waren aber die einzigen beiden Sachen, die mich störten und die letzte war nur Standort bedingt. Ansonsten war ich sehr zufrieden mit dem Drucker. Die ein oder andere Verstopfung des Hotends war jedes Mal relativ leicht zu beseitigen.

##New requirements
<h2>Neue Anforderungen</h2>

With growing interests in the 3D printing topics, the requirements for the tool are also growing. Smartphone cases printed in PLA for a family member are brittle and can't be used. Flexible filament is ready to buy but can't be used with my printer. Other filaments like ABS, HIPS, nylon or filaments with wood, copper or bronze mixed into it are also available. A new printer should be capable to print this materials.

Mit steigendem Interesse an dem Thema 3D-Druck, steigen auch die Anforderungen an das Werkzeug. Testdrucke von Smartphonehüllen für Familienmitglieder zerlegte es beim Überziehen, auf Grund des festen PLA. Flexibles Material steht zum Kauf bereit aber kann von meinem Drucker nicht gedruckt werden. Auche andere Materialien wie ABS, HIPS, Nylon oder Filamente mit Holz-, Kupfer-, Bronzefüllung sind mittlerweile erwerbbar. Ein neuer Drucker sollte die Möglichkeit haben, dies alles drucken zu können.

The Lulzbot Mini from Aleph Objects was in my mind because of the automatic bed leveling feature. The printer has a metal contact in each corner of the bed. During calibration the nozzle touched the contacts to let current flow through the hotend and the contact. The bed height is than corrected in software. The nozzle gets cleaned before the calibration process. All of this is done automatically before every print.

Ein Drucker der mir direkt einfiel, ist der Lulzbot Mini von Aleph Objects. Dieser verfügt über eine automatische Druckbettkalibrierung. Dafür befinden sich an jeder Ecke des Druckbettes Metallscheiben. Die Düse des Hotends wird automatisch mit Hilfe eines Abstreifers gereinigt. Dann fährt der Drucker die Düse auf die Metallscheiben, wodurch ein Stromkreis durch die metallische Düse geschlossen wird. Die Software berechnet dann die Lage des Druckbetts und korrigiert während dem Druck die Z-Achse entsprechend. Die ganze Prozedur erfolgt vor jedem Druck und läuft komplett autark ab.

So with this printer the bed calibration is not a problem anymore. But what are the other properties of the printer? The volume for printing is 152mm x 152mm x 158mm (l x w x h) which is currently sufficient for me. Until now I had only two parts 150mm long on one side. The filament holder is on top of the printer and therefor easy to reach. The Lulzbot Mini comes with a full metal hotend which can reach temperatures of 300°C. So it can be used to print many of the new available materials. Some of the new materials also need a heated print bed. The Lulzbot Mini has one which can be heated until 120°C. Filament can be inserted directly into the extruder which sits on top of the hotend. So no bowden tube neccessary. For controlling the printer there is an USB connector to connect an PC. If you don't want to attach a PC the whole time there is the possibility to connect an Raspberry Pi with OctoPrint installed. The filament size is now 3mm, so I can't use my old 1.75mm filament with this printer.

Mit diesem Drucker wäre die Kalibrierung kein Thema mehr, aber wie sehen die weiteren Eigenschaften des Druckers aus? Der Druckraum beträgt 152 x 152 x 158 (L x B x H), welcher ungefähr meinem GRR Neo entspricht. Dieser Druckraum war mit immer ausreichend, ich hatte erst zwei Teile die auf einer Seite 150mm lang waren. Der Spulenhalter befindet sich über dem Druckraum und ist somit einfach zu erreichen. Der Lulzbot Mini wird mit einem Vollmetall-Hotend ausgeliefert was bis 300°C aufgeheizt werden kann. Dadurch kann es für viele der neuen Materialien verwendet werden, wie zum Beispiel Nylon (225°C - 270°C Drucktemperatur). Allerdings erfordern diese Materialien auch ein beheiztes Druckbett, welches der Mini ebenfalls besitzt (bis zu 120°C heizbar). Der Extruder sitzt direkt über dem Hotend, was den Filamentwechsel vereinfacht. Der Drucker besitzt nur einen USB-Anschluss, mit Hilfe von OctoPi kann er aber unabhängig von einem PC betrieben werden. Der Lulzbot Mini benötigt 3mm Filamentdurchmesser, wodurch mein 1,75mm PLA Vorrat nicht mit dem Drucker verwendbar ist.

So I bought this printer as my new tool and until now I'm very happy with it.

Alles in allem, habe ich mich für den Drucker entschieden und es bis jetzt noch nicht bereut.

##The new one
<h2>Der Neue</h2>


Das gute Stück hat die Position seines Vorgängers erhalten.

<a href="https://cronj.de/2015/12/24/3d-druck-geht-in-die-zweite-runde/_dsc5166/" rel="attachment wp-att-378"><img class="alignnone size-medium wp-image-378" src="https://cronj.de/wp-content/uploads/2015/12/DSC5166-234x300.jpg" alt="_DSC5166" width="234" height="300" /></a>

Hier wird gerade eine Halterung für den Kofferraum gedruckt. Als Material verwende ich schwarzes HIPS, was eine mattere Oberfläche als PLA hat.

<a href="https://cronj.de/2015/12/24/3d-druck-geht-in-die-zweite-runde/_dsc5169/" rel="attachment wp-att-379"><img class="alignnone size-medium wp-image-379" src="https://cronj.de/wp-content/uploads/2015/12/DSC5169-300x200.jpg" alt="_DSC5169" width="300" height="200" /></a>

Nach dem Druck fährt das Druckbett zur Rückseite, wenn es dann die 60°C unterschreitet kommt es nach vorne. Dann kann man das gedruckte Teil leicht vom Druckbett lösen.

<a href="https://cronj.de/2015/12/24/3d-druck-geht-in-die-zweite-runde/_dsc5172/" rel="attachment wp-att-380"><img class="alignnone size-medium wp-image-380" src="https://cronj.de/wp-content/uploads/2015/12/DSC5172-300x200.jpg" alt="_DSC5172" width="300" height="200" /></a>

Dieser Oktopus liegt dem Drucker bei. Er wurde zu Kalibrierungszwecken auf diesem Drucker im Werk gedruckt.

<a href="https://cronj.de/2015/12/24/3d-druck-geht-in-die-zweite-runde/_dsc5178/" rel="attachment wp-att-381"><img class="alignnone size-medium wp-image-381" src="https://cronj.de/wp-content/uploads/2015/12/DSC5178-300x200.jpg" alt="_DSC5178" width="300" height="200" /></a>

Der Rocktopus liegt als Objekt auf dem mitgelieferten USB-Stick und wird als erster Druck nach Anleitung erzeugt. Dafür liegt dem Drucker ein Meter gelbes HIPS bei. Die Druckeinstellungen sind auf mittlerer Geschwindigkeit.