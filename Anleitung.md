# Anleitung Freifunkrouter Flashen und Einrichten #
Damit dein Router Teil des Freifunk-Netzes werden kann, muss er mit dem Freifunk-Betriebssystem (der „Firmware“) **bespielt**, **eingerichtet** und entsprechend **angeschlossen** werden. Im folgenden leiten wir dich durch diese drei kurzen Schritte durch. 

Aber eins vorweg: falls du dir unsicher bist, richten wir dir auch gerne einen Router bei einem der nächsten Freifunktreffen ein!

## Vorbereitung ##

Wenn du dich dazu entscheidest beim Freifunk mitzumachen, hast du anfangs die Qual der Wahl beim Aussuchen eines Routers. Welche Router und Versionen die Freifunk-Firmware unterstützen findest du unter http://wiki.bremen.freifunk.net/Unterstuetzte-Router.   

Wir empfehlen den  **TP-Link TL-WR841N** für knapp 20€, oder das etwas besser ausgestattete Modell **TP-Link TL-WDR4300**, für ca. 50€.


## Neue Firmware ##
### Firmware downloaden ###
Zuerst brauchst du die passende Freifunk-Firmware für deinen Router. Die **Rückseite** deines Gerätes verrät dir, welche Firmware du genau brauchst.

<img src="http://jel.to/ff_pics/router_rueckseite.jpg" title="Rückseite deines Routers" />

Unter **„1.“** findest du die **Modellnummer** und unter **„2.“** die **Revisionsnummer**. „Ver 8.1“ steht dabei allgemein für Version 8, „Ver 7.4“ für Version 7 usw..
Auf der [Downloadseite](http://downloads.bremen.freifunk.net/firmware/testing/factory/) suchst du dir nun die Datei, die genau deinem Modell und deiner Revision entspricht und **lädst diese herunter**.

In oberen Fall wäre es die Datei mit dem Namen gluon-ffhb-0.x~VERSION-tp-link-tl-**wr841n**-nd-**v8**.bin. Achte bitte unbedingt darauf, dass Modellbezeichnung und Revisions genau zu deinem Gerät passen. Einzig das N bzw. ND im Modellnamen ist irrelevant, die Firmware für den wr841n ist auch zum wr841nd kompatibel.

**Eine falsche Firmware kann dazu führen, dass wir den Router mit sehr großem Aufwand reanimieren müssen.**

### Firmware aufspielen
Nachdem du dir die neue Firmware besorgt hast, musst du deinen **Computer mit dem Freifunkrouter verbinden**. Dazu setzt du den Router unter Strom (**„1.“**, Knopf ganz links rein drücken bei 841). Das „LAN“-Kabel steckst du in eine der **gelben Buchsen („2“)**. Die blaue Buchse brauchst du erst später. Verbinde das andere Ende des LAN-Kabels mit deinem Computer.
Am besten du verwendest das graue LAN-Kabel, was schon im Karton deines Routers dabei war.

<img src="http://jel.to/ff_pics/router_anschluesse.jpg" title="Anschlüsse deines Routers" />

Das Menü deines Router, über den wir die neue Firmware aufspielen erreist du über den **Webbrowser**. Tippe dazu folgende Adresse in deine Navigationsleiste **(„1.“) : 192.168.0.1**

Standardmäßig musst du dich mit einem Benutzernamen und einem Password **authentifizieren**, diese lauten im Auslieferungszustand **„admin“** und **„admin“**.

<img src="http://jel.to/ff_pics/menu_stock_1.jpg" title="Standard Weboberfläche">

Den für uns interessanten  Menüpunkt erreichst du links unter **„System Tools“ („2.“) → „Firmware Upgrade“ („3.“)**. Hier musst du nurnoch die richtige **Firmwaredatei aus dem vorherigen Schritt auswählen („4.“)** und **hochladen („5.“)**. Prüfe bitte noch einmal, ob die Firmware wirklich zu deinem Routermodell passt, bevor du auf „Upgrade“ klickst! 

<img src="http://jel.to/ff_pics/menu_stock_2.jpg" title="Standard Weboberfläche">

Nach wenigen Minuten sollte dein Router folgende Meldung anzeigen und neu starten.

<img src="http://jel.to/ff_pics/success.png" width="300px" title="Erfolgreich geflasht">

## Freifunk-Router konfigurieren

Nach dem Neustart des Routers ist dieser unter einer **anderen IP** zu erreichen, daher hat es sich bewährt, das LAN-Kabel zwischen Computer und Router für einen kurzen Augenblick zu entfernen, damit der Computer danach eine neue Adresse beziehen kann.

Um das neue Menü des Routers zu erreichen, tippst du diesmal die **Adresse 192.168.1.1 in deine Navigationsleiste des Browsers ein**. Dort lassen sich verschiedene Einstellungen für den Router vornehmen. 

<img src="http://jel.to/ff_pics/gluon_1.jpg" title="Neue Weboberfläche">

Zuerst kannst du dir einen **beliebigen Namen** für deinen  Freifunkrouter ausdenken (oder ihn so lassen).
Außerdem musst du festlegen, ob die Firmware des Routers sich automatisch aktualisieren soll. In den meisten Fällen ist eine automatische Aktualisierung sinnvoll, so ist dein Router immer auf dem neusten Stand und unerwartete  Netzausfälle bleiben aus.

<img src="http://jel.to/ff_pics/gluon_2.png" width="350px" title="Mesh-VPN">

Im folgenden musst du noch angeben, ob dein Freifunkrouter sich über das Internet mit anderen Routern verbinden soll (**Mesh-VPN**). Diese Option ist immer nötig, außer der Router fungiert rein als Repeater und verbindet sich über andere Router ins Freifunk-Netz. Zum Beispiel für den Router im Gartenhäuschen ohne direkten Zugang zum Internet ist dies sinnvoll. 
Falls gewünscht, kann die **Bandbreite**, die der Freifunkrouter maximal nutzten darf, über die darauf folgende Option **eingeschränkt werden** (optional).

<img src="http://jel.to/ff_pics/gluon_5.png" width="350px" title="Geo-Koordinaten">

Damit andere Freifunker oder Nachbarn den Router auch auf der **Freifunk-Karte** finden, können die **Koordinaten** des Routers eingetragen werden. Lässt man den Haken weg, so erscheint der Router nicht auf der Karte.
Die Koordinaten sollte man sich vor der Konfiguration ggf. zwischenspeichern. Auf unserer [Freifunkkarte](http://bremen.freifunk.net/map/geomap.html) kannst du dir die gewünschten Koordinaten anzeigen lassen (ganz oben "Koordinaten beim nächsten Klick anzeigen").

<img src="http://jel.to/ff_pics/gluon_3.png" width="350px" title="Geo-Koordinaten">

Nachdem du, natürlich auch **optional**, deine **Kontaktadresse** eingetragen hast, schließt du die Konfiguration mit einem Click auf den **„Fertig“-Button** ab. Der Kontakt dient dazu, dass du du dich informieren lassen kannst, wenn der Router mal keine Verbindung mehr zum Freifunk-Netz hat.
Der Folgende Bildschirm bestätigt dir die erfolgreiche Einrichtung. Dein Router ist fertig eingerichtet und startet neu in den produktiven Modus. Deinen Schlüssel musst du **nicht** mehr, wie beschrieben, über einen Link übertragen.

Wenn du zu einem späteren Zeitpunkt nochmal Einstellungen im Config-Mode vornehmen möchtest, musst du den Reset-Button gedrückt halten. Nach einigen Sekunden blinken die Status-LEDs kurz auf und erlöschen wieder, der Router startet neu in den Config-Mode. Jetzt kannst du, wie unter "Freifunk-Router einrichten" beschrieben, erneut vorgehen.

## Anschluss an den Heimrouter
Jetzt, wo dein Router geflasht und eingerichtet wurde, musst du ihn einfach nur noch **an deine Heimrouter anschließen**. Nehme dazu das graue LAN-Kabel aus dem Karton und stecke es in den **blauen „WAN“-Anschluss** deines Freifunkrouters **(„1.“)**. **Nicht die gelben Ports** verwenden, dann kann der Router keine Verbindung zum Freifunknetz über das Internet aufbauen!

<img src="http://jel.to/ff_pics/ff_an_fritz.jpg" title="Anschluss Freifunkrouter">

Das andere Ende des grauen LAN-Kabels kommt in den (oft) **gelben LAN-Port deines Providerrouters** (Fritzbox, Speedport, Easybox usw.) **(„2.“)**. An dem Kabel, was aus der Wand (TAE-Dose) zu deinem Providerrouter führt und im blauen Port steckt, musst du **nichts weiter verändern** (in diesem fall das orangene Kabel). 
Sobald beide Geräte mit Strom versorgt werden, hast du nach wenigen Minuten deinen Freifunkrouter am Netz! Ebenfalls wird nach kurzer Zeit der Name deines Routers in der [Knotenliste](http://bremen.freifunk.net/map/list.html) auftauchen. 

## Expertenmodus  

Dieser sollte immer vor den Änderungen im Wizzard vorgenommen werden, da beim Verlassen der Seite die Informationen nicht automatisch gespeichert werden.

Im Expertenmodus ist es zudem noch möglich einen SSH-Zugriff einzurichten, damit man auch im produktiven Betrieb auf den Freifunk-Router, per SSH zugrreifen kann. Bitte dieses nur durchführen, wenn man sich damit auskennt!  
Desweiteren kann man sich für einen Versionszweig entscheiden, der auf dem Router immer automatisch aufgespielt wird. Wir empfehlen die Standard-Einstellung.  

Solltest du vorhin das automatische Aktualisieren deaktiviert haben, kannst du bei „Firmware aktualisieren“ eine andere Version einspielen oder aber auch gar eine ganz andere Firmware.

# Diagnose und Fehlerbehebung

in Arbeit ;)
