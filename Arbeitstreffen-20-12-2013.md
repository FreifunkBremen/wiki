**Wann/Wo:**
***
**Datum:**   20.12.2013 </br>
**Uhrzeit:** 18 Uhr </br>
**Ort:**     Hackspace Bremen http://www.hackerspace-bremen.de/ </br>

**Was wird benötigt?(Tagesordnung)**
***
* Öffentlichkeitsarbeit
 * Wann ist der richtige Zeitpunkt? Erstmal noch in technik-affinen Kreisen     
testen wäre wohl keine doofe Idee
</br></br>
* Bildmaterial (Bild von der Skyline der Stadt mit einem Router z.B.) siehe z.b. Franken https://netmon.freifunk-franken.de/networkstatistic.php oder Oldenburg www.freifunk-ol.de <-- wer wills machen
 * msquare ist dran

* Facebook (Administratoren)??? 
 * macht danielwf, sobald die neue Seite online ist. Es wird dann per IFTTT.com eingebunden, wenn's nicht vielleicht auch anders geht.

* Twitter(Administratoren)???

* stand des Servers?
 * läuft erstmal, Ideen und TODOs s.u.

* Spontanes meshing zwischen Ol und HB soll das so ? 
 * (gefixed, andere BSSID für Bremen)

* Router einkaufen?
 * Sollte jeder erstmal selbst kaufen, wir bieten dann wöchentliche Flash-Parties vor einem evtl. regelm.(?) Freifunk-Treffen an. Nebenbei gibt es dann noch eine Wiki-Anleitung.

* Kosten? 
 * evtl. über gesammelte Spenden an "Förderverein Freie Netzwerke e. V."

**Firmware/Infrastruktur Ideen:**
***
* verteilte DHCP-Server auf den Routern 

* /16 unterteilen in /26 und jedem Router ein Subnet zuordnen

* DHCP Discover per ebtables am Erreichen "anderer" Router hindern
 * Das macht Roaming nicht kaputt, da ein Client der bereits eine Adresse hat kein Discover sondern einen DHCP Request sendet, der dann von Routern ignoriert wird die das entsprechende Subnet nicht bedienen
Ein Client der bereits eine Adresse hat, fragt gar nicht erst. Auch bei AP Wechsel nicht, weil es das selbe Netz bleibt.
Doch, er fragt periodisch, ob er die Adresse behalten darf (nach Ablauf der Lease-Time)
Würde die Funkwolke intern zumindest operabel halten, wenn der Server weg ist
Das würde aber bedeuten, dass man die Subnetze konfigurieren muss.
Ich glaube, dass dies bei >100 nodes ein nicht unerheblicher aufwand ist
Es soll doch eh eine Config-Infrastruktur aufgebaut werden. Warum können dann nicht die Subnetze an zentraler Stelle zugeteilt werden?
Dies bezieht sich auf die (absehbar nicht obsolete) ipv4 konfiguration. Also auch die Frage welches (internet-)gateway benutzt werden soll. Die Router müssen diese Information beziehen. Es gibt schon ansätze ([gatewaymode]) um bei vorhandensein mehrerer gateways den router einen auswählen zu lassen. auch dies läuft über die filterung der antworten der dhcp server. Es ist aber denke ich nicht kompatibel mit dem hier angedachten ansatz.

* Trafficlimitierung: In netmon einstellbar machen, wie viel über WAN gehen darf, um den Internetanschluss nicht über die Maßen zu belasten

 * Grundsätzlich ist die Idee derzeit eher möglichst weit von Einstellungen aus Netmon zu gehen, ergo Einstellungen direkt am Router machen, oder ggfs über ein Webinterface welches SSH sprechen kann oder sowas. Netmon selber soll aber rein passiv bleiben.
Ja, netmon und die konfiguration der router sollen getrennt werden. Ich (marc - suaefar@googlemail.com) habe dazu bereits auf der routerseite ein paar konfigurationsvorschläge gemacht. Ein Skript, das einfache und idiotensichere konfiguration erlaubt soll "admin.sh" werden [admin.sh]. zB: "/etc/admin.sh 2000 8000" setzt das trafficshaping auf 2 Mbit up und 8 Mbit downstream. Dieser befehl könnte per remote-ssh oder von einem konfigurationsdaemon ausgeführt werden
Und wo setzt man diese Einstellung dann? Netmon kennt eh schon alle Router, daher sehe ich den Gewinn nicht, wenn man noch eine weitere Seite einführt, auf der man dann Router-Einstellungen vornehmen kann...
Das Problem hat mehrere Aspekte

* Sicherheit: Wer den status lesen darf darf noch lange nicht die konfig ändern.

*  Performance: Wie oft wird gelesen/geschrieben? Typischerweise wird haufig der status abgerufen und das muss schnell gehen war beim setzen der konfig keine so große rolle spielt weil diese relativ selten geändert wird

* Implementierung: Lesen und schreiben sind zwei grundverschiedene vorgänge. Netmon kann zur Zeit nicht schreiben. Es stellt konfigurationsinfo zur verfügung die sich die router holen und anwenden können (sicher ist das ohne ssl nicht).
 * Technisch soll es getrennt werden. Das bedeutet, dass die konfigurationsseite trotzdem im netmonlook erscheinen kann und der user davon nichts merkt.
gemeinsame authorized_keys mit ausliefern und Checkbox in netmon erstellen, um sie zu deaktivieren und stattdessen ein Passwort zu setzen ("Router selbst administrieren")
Das wäre auch meine bevorzugte variante. Ein opt-out. Wer nicht will, dem wird der router dann eben fernadministriert. Wobei EIN schlüssel schon kopfschmerzen macht (falls er "abhanden" kommt).

* [admin.sh] http://git.freifunk-ol.de/projects/ffol/firmware.git/blobs/cd0d5fa53db7f7aecf8d3e9ba4cc7382e05a23fd?hb=dc6d8b2cc3964bc04748ef6e471ac0ac30e2c3f6&f=bsp%2Fdefault%2Froot_file_system%2Fetc%2Fadmin.sh </br>
* [gatewaymode] http://www.open-mesh.org/projects/batman-adv/wiki/Gateways
