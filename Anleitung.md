    Diesen Artikel sollten noch mal zwei drei Personen überprüfen, bevor wir den Text nutzen können.
    Bitte daher hier ein entsprechendes OK oder Änderungwünsche angeben (Stand: 24.05.2014): 



Auf dieser Seite findest du eine sehr ausführliche Anleitung zur **Vorbereitung**, zum **Aufspielen der Freifunk-Firmware** und zur **Konfiguration des Freifunk-Routers**.

## Vorbereitung

Wenn du dich dazu entschieden hast beim Freifunk mitzumachen, hast du anfangs die Qual der Wahl beim Aussuchen eines Routers. Welche Router und Versionen die Freifunk-Firmware unterstützen findest du unter http://wiki.bremen.freifunk.net/Unterstuetzte-Router.   

Wir empfehlen den  **TP-Link TL-WR841N**, wovon es noch ein fast baugleiches Model mit einem „D“ im Namen, gibt. Bei dieser kann man noch die Antennen abnehmen (d steht für „detach“).

Hat man sich nun für einen Router entschieden, muss man noch die richtige Firmware aussuchen und [runter laden](http://downloads.bremen.freifunk.net/firmware/testing/factory/).  

In diesem Beispiel laden wir uns also für den  _TP-Link TL-WR841N v8.x_ die Datei _gluon-ffhb-*FW-VERSION*-tp-link-tl-wr841n-nd-v8.bin_ herunter.

>**Achtung**: Es kommt vor, dass die neusten Versionen der Modelle von der Freifunk-Firmware noch nicht unterstützt werden! Das Aufspielen einer falschen Version kann das Gerät unbrauchbar machen

## Firmware aufspielen  

**Achtung!  
Fehler können dazu führen, dass das Gerät unbrauchbar wird, bzw. man einen erhöhten Aufwand der Wiederherstellung hat.**

Das Aufspielen der Firmware auf den neuen Router erfolgt über die Weboberfläche.

Nun die folgenden Schritte abgehen:

1. Router ans Stromnetz anschließen
2. Router per LAN-Kabel (LAN-Port 1/gelb) mit einem Rechner verbinden.
3. Den Rechner in den Netzwerkeinstellungen auf DHCP stellen oder folgende Einstellungen vornehmen:
  1. IP-Adresse: 192.168.0.2
  2. Subnetzmaske: 255.255.255.0
  3. Gateway: 192.168.0.1
4. 	Im Browser deiner Wahl folgendes aufrufen: http://192.168.0.1
5. Die Zugangsdaten stehen auf der Rückseite des Routers (in der Regel admin/admin)
6. Nun unter System Tools -> Firmware Upgrade, die vorhin runter geladene  Datei auswählen und einspielen  
(_gluon-ffhb-*FW-VERSION*-tp-link-tl-wr841n-nd-v8.bin_)  

> Wichtig ist hier, dass man nun den Router jetzt nicht vom Strom trennt oder anders das Aufspielen unterbricht!

7. Wenn der Vorgang abgeschlossen ist, ruft man nun http://192.168.1.1 auf (Achtung, wenn vorhin die Netzwerkeinstellungen manuell vorgenommen wurden, muss nun die IP-Adresse und der Gateway angepasst werden!).  
Wenn nun alles gut verlaufen ist, sieht du nun unsere Seite für die Einstellungen des Freifunk-Routers.


## Freifunk-Router konfigurieren

Auf der ersten Seite (dem Wizzard) kann man verschiedene Einstellungen für den Router vornehmen. Darunter sind zum Beispiel die Bandbreitenbegrenzung oder die Standortangabe. Alle Einstellungen lassen sich später wieder ändern.

Aber gehen wir jeden Punkt durch:

1. Als erstes kann man dem Router einen Namen geben, der dann in unserer Knotenliste steht (optional).
2. Danach kann man entscheiden ob die Firmware des Routers automatisch aktualisiert wird oder ob man das lieber selbst macht. Hier empfehlen wir die automatische Aktualisierung. Andernfalls müsstest du dich in Sachen Firmware Updates selbst um Aktualität kümmern.
3. Beim nächsten Punkt musst du dich entscheiden wie du den Router einsetzen willst bzw. kannst. Wenn du einen Zugang zum Internet hast und den Router hinter dem entsprechenden DSL-Router anschließt, solltest du einen Haken bei „Mesh-VPN aktivieren“ setzen. Danach kannst du auch noch die Bandbreite einstellen, die du dem Freifunk Netz maximal zur Verfügung stellen möchtest. Wenn kein Haken bei „Mesh-VPN aktivieren“ machst, verbindet sich der Router nur noch mit anderen in der Umgebung befindlichen Freifunk-Routern.
4. Den Standort des Routers kann man ebenfalls in Form von Koordinaten eintragen. Diese sollte man sich vor der Konfiguration ggf. zwischenspeichern. Auf unserer [Freifunkkarte](http://bremen.freifunk.net/map/geomap.html) kannst du dir die gewünschten Koordinaten anzeigen lassen.
5. Im letzten Feld kannst du Kontaktdaten angeben, die aber von jedem abrufbar sind. Darüber kannst du dich aber auch informieren lassen, wenn der Router mal keine Verbindung mehr zum Freifunk-Netz hat. Dazu kannst du dich per Mail, XMPP/Jabber und/oder per Twitter benachrichtigen lassen.

Da wir nun erstmal den Router das erste mal betriebsbereit nehmen wollen, lassen wir den Expertenmodus aus. Dieser wird weiter unten noch erklärt.

Wurden nun alle gewünschten Einstellungen vorgenommen, klickt man auf „**Fertig**“ und der Router startet zum ersten mal in den produktiven Modus und du wirst auf eine neue Seite weitergleitet. Verbinde dich zuerst wieder mit deinem eigenen Netzwerk und klicke dann den Link. Dadurch wird die Node im VPN angemeldet bzw. bekannt gemacht.

Den Freifunk-Router verbindet man nun über den WAN-Port (blau) mit dem LAN-Port eines DSL-Routers und nach kurzer Zeit solltest du auch ein W-LAN mit der SSID **bremen.freifunk.net** finden 

## Testen

Um zu überprüfen ob sich der Router richtig mit dem Freifunk-Netz verbunden hat, rufst du einmal über deinen DSL-Router eine Seite auf, die dir deine aktuelle IP-Adresse anzeigt und verbindest dich dann mit dem Freifunk-Netz. Wenn die Adressen unterschiedlich sind, ist der Router richtig mit dem Freifunk verbunden. Ebenfalls wird nach kurzer Zeit der Name deines Routers in der [Knotenliste](http://bremen.freifunk.net/map/list.html) auftauchen. 

## Expertenmodus  

Dieser sollte immer vor den Änderungen im Wizzard vorgenommen werden, da beim Verlassen der Seite die Informationen nicht automatisch gespeichert werden.

Im Expertenmodus ist es zudem noch möglich einen SSH-Zugriff einzurichten, damit man auch im produktiven Betrieb auf den Freifunk-Router, per SSH zugrreifen kann. Bitte dieses nur durchführen, wenn man sich damit auskennt!  
Desweiteren kann man sich für einen Versionszweig entscheiden, der auf dem Router immer automatisch aufgespielt wird. Wir empfehlen die Standard-Einstellung.  

Solltest du vorhin das automatische Aktualisieren deaktiviert haben, kannst du bei „Firmware aktualisieren“ eine andere Version einspielen oder aber auch gar eine ganz andere Firmware.
