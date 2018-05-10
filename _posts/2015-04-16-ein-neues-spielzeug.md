title: Ein neues "Spielzeug"
link: https://cronj.de/2015/04/16/ein-neues-spielzeug/
author: Alex
description: 
post_id: 112
created: 2015/04/16 21:29:31
created_gmt: 2015/04/16 19:29:31
comment_status: open
post_name: ein-neues-spielzeug
status: publish
post_type: post

# Ein neues "Spielzeug"

Vor zwei Tagen war es endlich soweit. Nach einer gefühlten Ewigkeit und mehreren Monaten Recherche, habe ich meinen ersten 3D Drucker bestellt. Es ist ein Komplettgerät von German RepRap geworden, der Neo. Da ich den Drucker gerne als Werkzeug für meine Basteleien einsetzen möchte und nicht all zu viel an ihm selbst basteln wollte, sollte es ein Fertiggerät werden. Am Ende fiel die Wahl auf den Ultimaker 2 und den GRR Neo. Der Preis hat dann am Ende entschieden, auch wenn ein paar Abstriche gemacht werden mussten. Momentan ist der Drucker um 7% reduziert bei Reichelt zu haben, also habe ich ihn bestellt. 

## Aufbau

Heute ist er dann gut verpackt angekommen. Mit hinten angehängter Filamentrolle ist er nur 40cm tief, 34cm breit und 34cm hoch. So hat er einen schönen Platz neben meinem Schreibtisch gefunden. [ ](/wp-content/uploads/2015/04/IMG_20150416_202238023.jpg) ![Standort GRR Neo](https://cronj.de/wp-content/uploads/2015/04/IMG_20150416_203451043_HDR-300x169.jpg) Der Aufbau ist sehr einfach. Beim mitgelieferten Netzteil, muss der passende Adapter aufgesteckt werden. Der Filamentrollenhalter muss hinten eingehängt werden. Fertig. Nur noch das Filament in den Transportschlauch einführen und der Aufbau ist beendet. 

## Druckbettkalibrierung

Bevor man den ersten Druck startet, soll das Druckbett kalibriert werden. Dazu befinden sich drei gefederte Rändelschrauben an der Unterseite. Zur Kalibrierung wird mit der beigelegten Software, mit dem Hotend in jede Ecke gefahren. Dann soll man mit einem Stück Papier den Abstand von Druckbett zu Düse einstellen. Dies scheint allerdings abhängig von der Papierdicke zu sein. Beim ersten Druck war der Abstand zwischen Druckbett und Düse wohl zu gering. Die ersten Schichten wurden ziemlich unsauber. ![Erster Testdruck](/wp-content/uploads/2015/04/IMG_20150416_163200968-300x169.jpg) Man kann deutlich den unsauberen Boden erkennen. Ab ein paar Schichten, wurde es aber besser ... sogar richtig gut. Als Vergleich habe ich einen Stratasys Dimension Elite Drucker, der zur Prototypen- und Kleinteilproduktion auf der Arbeit verwendet wird. Einen riesen Unterschied gibt es in der Qualität zwar nicht mehr, aber es gibt Einen. Für meine Zwecke ist die gebotene Qualität aber völlig ausreichend. 

## Weitere Drucke

Als zweiter Testdruck entstand ein Skoda-Schlüsselanhänger für meinen Bruder. Ich wollte ja nicht einen Stapel Würfel produzieren. Hier sei noch einmal betont, das es sich wirklich um das zweite Teil aus dem Drucker handelt. ![Skoda Schlüsselanhänger](/wp-content/uploads/2015/04/IMG_20150416_172424404_HDR-169x300.jpg) Der erste Druck wurde per USB-Verbindung von meinem Desktop-PC getätigt. Ab dem zweiten Druck habe ich den Drucker an meinen Raspberry Pi 2 angeschlossen, auf dem ich Gestern schon OctoPrint installiert habe. OctoPrint erlaubt es mir über das Netzwerk auf meinen Drucker zu zugreifen. Dort kann ich dann meine Dateien über den Browser hochladen und den Druck starten. Außerdem bietet es mir die Möglichkeit den aktuellen Stand zu überwachen, falls der Drucker mal nicht mehr in Sichtweite stehen sollte. Auch einen Livestream gibt es. Hier wird auch das Raspberry Pi Kameramodul unterstützt. Timelapse-Videos können dort auch erstellt werden. Um diese zu nutzen muss ich allerdings erst eine passende Halterung drucken, damit mein Pi einen schönen Blick in den Druckraum hat. ![OctoPrint Screenshot](https://cronj.de/wp-content/uploads/2015/04/OctoPrint_Screenshot1-300x296.png) Das letzte Bild zeigt das Webinterface während einem Druck. Dann habe ich mich an ein Teil mit Stützmaterial gewagt. Das lief allerdings nicht so wie gewollt. Das Stützmaterial ist sehr schwer zu entfernen. ![Stützmaterial](https://cronj.de/wp-content/uploads/2015/04/IMG_20150416_202238023-300x169.jpg) Hier muss ich noch etwas mehr experimentieren, damit ich sauber entfernbares Stützmaterial erhalte. Beim Druck habe ich kurz nach dem Start meine Sony davor gestellt und ein Timelapse-Video vom restlichen Druck erstellt. [embed]https://www.youtube.com/watch?v=7E6ZWa6PXmA&feature=youtu.be[/embed] Jetzt heißt es probieren, probieren und nochmal probieren, bis alle Einstellungen passen und ich möglichst ohne viel Ausschuss meine gewünschten Teile drucken kann.