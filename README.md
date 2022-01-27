Was nett wäre, Vergesst bitte nicht meinen Kanal zu abonnieren und zu liken ;-) ... wann disliken gut wär, dann das auch :-))

https://www.youtube.com/c/BavarianSuperGuy


Ich übernehme keine Haftung für Schäden, die aufgrund der Nutzung 
der Software entstehen oder entstanden sind. 
Jeder ist für sein tun selber verantwortlich.
Mir sind keine Probleme bekannt.

GANZ UNTEN IST DAS ANSCHLUSSSCHEMA (Bastelplan3000)

3 Dinge sind wichtig für die Umsetzung dieses Projekts:
- 3,3V
- Guter Wlan Empfang(Keine Leerzeichen in der SSID vom Router)
- Readme vollstandig lesen, dann nochmal
wann readme gelesen wurde und ihr daraufhin gemerkt habt
aufgrund der Methode die beschrieben wird ,
der wlan empfang ist schlecht und lässt sich nicht ändern

... https://www.google.com/search?q=esp8266+antennenhack

ich kann keinen besseren Empfang programmiern!
und der esp kann auch nix anderes machen 
wann er ständig versucht sich  ins Wlan einzuloggen


Internet Explorer wird nicht unterstützt!(die kochen wieder eigenes Sueppchen bei Slider funktion)

<img src="Seplos.png" alt="Soyosource Controller by BavarianSuperGuy"/>


# Seplos Controller mit Webseite
Der Esp8266 ist über ein Rs485 Modul mit dem Seplos BMS verbunden und kann diesem seine Daten entlocken.
Shutdown Button: Das BMS wird ausgeschaltet , selbe Art als ob man länger auf dem BMS tastschalter bleibt.

Kurzum die Firmware die es hier zum Download gibt, liest das Bms aus und es lässt sich per Button Klick abschalten.
Es fehlen derzeit  noch die Warnings .

Die Firmware(firmware_vX.X.X.X.bin") ist im Verzeichnis espflasher.
Diese kann unkompliziert auf einen 4Mbyte Esp mit dem im Verzeichnis enhaltenen
Tool "FlashESP8266.exe" geflasht werden. 
Dieses Tool FlashESP8266.exe ist nicht von mir , aber hat schon hevorragende Dienste geleistet.

<img src="Webseite SEPLOS Controller.png" alt="Seplos Controller by BavarianSuperGuy"/>

Was kann der ESP8266 Seplos Controller :

- Mqtt Schnittstelle, Payload ist ein Json Array , die Topic Addressen werden in der ESP Weg UI angezeigt und sind für jeden Esp induviduell unique.
- Http Schnittstelle, Daten werden als Json Array ausgegeben
- SAVE CONTROLER Button ist für spätere Funktionen reserviert
- Derzeit kann nur ein BMS damit ausgelesen werden, Multipackreading ... coming soon

- Die SOC Zeile blinkt wann es einen Discharge oder Charge übers BMS gibt, ansonsten bei Current==0 , bleibt die Zeile weiss und blinkt nicht.
- Die SOC Spalte ist wie im Batteriemonitor farbig 0-30% red, 30-50% yellow,  50-100% green!
- Esp Herzschlag bekommt die zusätzliche Bezeichnung DIS anghängt wann die Batterie Leistung abgeben muss!




RS485 ttl Adapter (2 verschiedene getestet)
- rs485 adapter A an A von Soyo anschliessen und B an B

<img src="rs485.png" alt="Soyosource Controller by BavarianSuperGuy"/>
- Beim "DI DE RE RO" Rs485 Modul
werden die mittleren Rs485 Pins "DE RE" auf einen Pin gebrückt an Esp GPIO0 angeschlossen.
Dann Rs485 "DI" auf Esp TX  und Rs485 "RO" auf Esp RX 

<img src="rs485_2 .png" alt="Soyosource Controller by BavarianSuperGuy"/>
- Beim RX TX Rs485 Modul
wird der Rs485 TX mit Esp TX verbunden und Rs485 RX mit Esp RX verbunden , also nicht kreuzen!

!Vcc ist bei beiden Modulen 3.3volt!

Keinen USB/TTL Adapter als 3,3v Poduktiv Stromquelle verwenden, für erstflashen is es OK!

ESP:

EINRICHTUNG##############################################################################################
- 0.Bei Nutzung von Mqtt: Mqtt.fx Client öffnen mit Broker verbinden und Topic : 'Soyosource/#' abonnieren
- 0.1 Es kommt nach Schritt 8. ein Info Publish vom Esp mit der IP adresse.
- 0.2 Man kann die Ip Adresse nat. auch auf dem herkömmlichen Weg herausfinden
- 1.Firmware auf den gelöschten Esp8266 flashen
- 2.Esp Neustart
- 3.Im Wlan nach SOYO_... suchen
- 4.Wlan mit Passwort 12345678 verbinden
- 5.Es öffnet sich automatisch Browser Fenster mit 192.168.4.1
- 6.Unter Configuration
- 6.1 Wifi auswählen oder eingeben und Passwort eingeben
- 6.2 Mqtt kann derzeit nur ohne ssl und seit Version 1.0.1.1 mit  Benutzer/Passwort benutzt werden
- 7.Speichern mit dem Button ganz unten
- 8.Esp Neustart
- 9.Ipadresse in Mqtt Client oder Router ausfindig machen
EINRICHTUNG#############################################################################################

INBETRIEBNAHME##########################################################################################
- 1.Ipaddresse im browser aufrufen
INBETRIEBNAHME##########################################################################################

CONFIGPORTAL############################################################################################
Um im Nachhinein wieder ins Configportal zu kommen um die Wlan und Mqtt Daten zu ändern muss der 
- Pin RST vom ESP innerhalb 10sekunden 2X auf GND getippt werden
- Anwendungsbispiel: Taster 2mal hintereinander drücken
Daraufhin startet der ESP neu ins Configportal(EINRICHTUNG Punkt 3) , dort trägt man dann alle Daten neu ein, die fehlen
und klickt auf Save (Button ganz unten)
CONFIGPORTAL############################################################################################


DER BASTELPLAN3000 MOD passt 100%.
Vorab schon mal erwähnt am RS45 Kabel das zum BMS führt sind ´es die ersten 2 litzen die A und B darstellen 
braun-weiss = A
braun = B

Anschluss : A zu A und B zu B


Falls Ihr mich unterstützen wollt, Spenden sind herzlich willkommen und würde mich sehr freuen :-)
Hier bitte - https://paypal.me/armerprogrammer

<img src="BastelPlan3000_Soyosource_Controller_by_BavarianSuperGuy.png" alt="Soyosource Controller by BavarianSuperGuy"/>
