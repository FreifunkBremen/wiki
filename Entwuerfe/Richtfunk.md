### Entwurf vom 18.6.2016

Aufgrund von Firmwareänderungen der Originalgeräte und der Freifunksoftware, sowie
anderer kleinerer Stolperfallen, entsteht hier eine eigene Info- & Flashanleitung
zu den Richtfunkgeräten.


## Inhalt:


[1.) Allgemeines](#inhalt_1-allgemeines)

[2.) Voraussetzungen](#inhalt_2-voraussetzungen)

[3.) Installation ](#inhalt_3-installation)

[4.) Konfiguration ](#inhalt_4-konfiguration)

[5.) FAQ](#inhalt_5-faq)



----


### 1.) Allgemeines
Richtfunkgeräte im Freifunk werden auf 2,4 Ghz und 5 Ghz betrieben. Die besonderheit eines Richtfunkgerätes ist die schmale gebündelte Richtwirkung der Antenne und die dadurch entstehende höhere Reichweite des Signals. Ein einfacher Vergleich wäre eine freistehende Glühlampe, die das Licht Kugelförmig abstrahlt zu einer Taschenlampe, die einen Lichtkegel abstrahlt.

Zur Versogrung eines schmalen Bereiches, wie eines Straßenzuges oder der Anbindung eines zu weit entfernten Freifunkrouters, wird ein Richtfunkgerät mit der Freifunksoftware bespielt. Um eine Strecke, also Punkt zu Punkt Verbindung zu bauen, verbleibt die original Firmware auf dem Gerät.

Besonderheiten der Originalfirmware:
Automatische Leistungsregelung bei bestehender Funkverbindung. D.h. die Geräte regeln ihre Sendeleistung so weit herunter, das eine optimale VErbindung besteht und der dahinterliegende Raum nicht überstrahlt wird.



### 2.) Voraussetzungen
Richtfunkgerät mit POE Injektor (POE Buchse) verbinden, die andere Buchse mit dem Rechner verbinden. Das Richtfunkgerät hat eine feste IP Adresse. Dem angeschlossenen PC muss manuell eine IP Adresse aus dem Bereich des Richtfunkgerätes zugewiesen werden. Beispiel: Rifu hat 192.168.1.20, PC bekommt 192.168.1.21
Später wird der PC wieder auf DHCP umgestellt. 

Das RiFu Gerät hat deutlich mehr Einstellmöglichkeiten als ein Router. Eine Skizze, was wir verbinden wollen und welche Konfigurationen zusätzlich an den Freifunkroutern eingestellt werden müssen, ist in jedem Fall hilfreich.

### 3.) Installation


### 4.) Konfiguration



SSH Zugang mit Key oder Passwort einrichten

**Neustart im Configmode**

Manchmal ist es Notwendig in den Configmode zu starten. Dies beinhaltet die Weboberfläche des Systems zum ersten Einrichten eines Freifunk-Routers. Für gewöhnlich hält man ein paar Sekunden lang die Reset Taste gedrückt. Folgende Ausführung würde den gleichen Effekt erzielen:
~~~
uci set gluon-setup-mode.@setup_mode[0].enabled=1
uci commit gluon-setup-mode
reboot
~~~


### 5.) FAQ

**Die Kiste hängt, wie kann ich einen Reset machen ohne aufs Dach zu klettern?**
- Das kleine Fernspeisenetzteil für POE hat eine Befestigungsplatte am Gehäuse. Wird diese Platte entfernt sehen wir ein kleines Resetknöpfchen. Drücken mit z.B. Büroklammer, löst den Reset aus.

**Gibt es eine Zusammenstellung zum Thema Outdoor CPE´n ohne alles ergooglen zu müssen?**
- Teilweise, einige Systemhersteller haben umfaangreiche Dokumentationen erstellt. Siehe am Beispiel LanCom https://www.lancom-systems.de/fileadmin/pdfs/products/WLAN_OUTDOOR_MANUAL_DE.pdf
Durch den technischen Wandel bleibt dir Google nicht erspart.

**Der nächste FF-Knoten ist gerade aus der Reichweite, brauch ich zusätzlich eine Outdoor-CPE?**
- Jein, es gibt verschiedene Möglichkeiten. Über eine CPE die Verbindung zum Knoten herstellen, sofern möglich, an deinem Router etwas bessere Antennen verwenden. Richtantennen am Router verwenden. Eine modifizierte CPE verwenden, an einer der beiden Richtantennen einen Rundstrahler anschliessen. ModAnleitungen im Freifunkforum https://forum.freifunk.net hier ein Beispielbild: https://forum.freifunk.net/t/picostation-aufs-dach-gebaut-ich-bin-begeistert/2822
Beim Gerätemodding auch immer die OpenWRT Seiten beachten. Beispiel: https://wiki.openwrt.org/doku.php?id=oldwiki:openwrtdocs:hardware:ubiquiti:nanostation2

**Ich habe auf meine neue CPE das FF-Image eingespielt, jetzt geht gar nichts mehr.**
- Ubiquity-Geräte mit AirOS XM.v5.6.X / XW.v5.6.X (oder neuer): Bevor du die Freifunk-Firmware (oder OpenWRT generell) aufspielst, ist es notwendig, zuerst ein Firmwaredowngrade auf die Version AirOS XM.v5.5.X oder XW.v5.5.X durchzuführen! Ohne diesen Firmwaredowngrade WIRD DAS GERÄT NICHT BOOTEN

**Wiederbeleben einer einer CPE (unbrick)**
- Zum Thema unbrick gibt es eine schöne Anleitung
https://wiki.md.freifunk.net/Anleitungen/Unbrick-Nanostation

**Ich kann mich nicht mit admin/admin auf die CPE einloggen**
- dann versuche es mit ubnt/ubnt
- Für fast alle Routermodelle sind hier die Daten zu finden: https://wikidevi.com/wiki/Main_Page


Bitte diesen Entwurf Ergänzen, traut euch :-)

