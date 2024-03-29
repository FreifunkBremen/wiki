## Inhalt
## Freifunk Router Image in VM-Ware/VM-Player betreiben 
(Windows Umgebung, mit Linux geht es ähnlich)

[[_TOC_]]

### Warum sollte ich das tun?
- Es wird keine reale Hardware benötigt, ich kann direkt auf meinem PC damit arbeiten.
- keine Beschränkung des Speicherplatzes
- stärkere Perfomence
- komplexes virtuelles Netzwerk möglich
- Es kann nichts kaputt gehen

VM-Player installieren, der Player schlägt ein Arbeitsverezichnis vor wo wir die Images ablegen.
Bei mir ist es das Verzeichnis "Virtual Machines" unter Benutzer/Documents. Mein Benutzer ist FFHB, damit
lautet der absolute Pfad: c:\Users\FFHB\Documents\Virtual Machines\

Dort erstelle ich mir einen Unterordner "gluon-ffhb-2016.2.7+bremen1", das ist momentan das aktuelle Image der Community Bremen ffhb.

Über die Freifunkseite lade ich mir das benötigte X86.64 vmware Image herunter "gluon-ffhb-2016.2.7+bremen1-x86-64-vmware.vmdk"
und lege es in das Verzeichnis \Virtual Machines\. (https://downloads.bremen.freifunk.net/firmware/stable/factory/)

Vm-Player oder Workstation starten und neue virtuelle Maschine erstellen (Ctrl-N). Als Hardware wird die höchste Version des Players 
angezeigt. Diese Angabe wird übernommen, da keine VM für eine ältere Version erstellt werden soll.
Den Player gibt es unter : https://my.vmware.com/de/web/vmware/free#desktop_end_user_computing/vmware_workstation_player/12_0
oder über Google suchen.

Die Limits zeigen die maximal mögliche Leistung an, ist nur informativ. 
Gluon bis Kernel 3.18 ab LEDE Kernel 4.4
Select Guest Operation System (Linux & Other Linux 3.x kernel)
Virtual machine name: gluon-ffhb-2016.2.7
Location: ..\Documents\Virtual Machines\gluon-ffhb-2016.2.7 (unser erstelltes Verzeichnis mit dem Image) kopiere/verschiebe das Image.vdmk in dieses Verzeichnis.
Processors: 1er reicht
Memory: 1024Mb
Network connection: Use bridged networking
I/O controller: LSI Logic
Virtual Disk type: IDE
Select Disk: Use an existing virtual disk (Auswahl von:gluon-ffhb-2016.2.7+bremen1-x86-64-vmware.vmdk) oder anderes.
Convert existing virtual disk to newer format?: Keep existing format
Finish

Über Customize Hardware können alle Änderungen auch später vorgenommen werden. Hier mal ein bischen spielen, die VM-Player verändern ihr Aussehen und Einstellmöglichkeiten in jeder neuen Version.

Start der neuen virtuellen Maschine, nach ca. 10-14 Sekunden ist der Bootvorgang abgeschlossen, die letzten Meldungen sind: bt-setup: port 1(eth0) entered forwarding state.

Einmal Enter drücken und die Meldung BusyBox v1.23.2 mit dem OPENWRT Wireless Freedom ASCII Logo erscheint.
Wir sind jetzt als root@000c29afeec3:/# in der Shell und können auf dem Router Arbeiten.

**[------------------------------------------------------------------------------------------------------------------------- Zurück zum Inhalt:](#inhalt)**

### Der Router steht im Konfigmode und macht erst mal nichts mehr.
Vom PC aus können wir nicht auf die Konfigurationsoberfläche 192.168.1.1 wegen des Bridgemode. Eingaben in die Shell kopieren, oder Netzwerk auf NAT ändern (Anleitung fehlt, zweite Netzwerkkarte hinzufügen) und per SSH zugreifen.
Der VM Player stellt ein Terminal zur Verfügung. Folgende Konfigurationsschritte führen wir nun durch.
- Passwort ändern / neu Anlegen
- Konfiguration über Gluon UCI und Eingabekonsole konfigurieren. Wir legen fest , dass dieser Router fertig und Konfiguriert ist.
- Wir aktivieren Mesh on Lan.
- Wir legen einen Namen für den Knoten fest.
- Wir schalten wir den Fastd Tunnel ein.
 
~~~
uci set gluon-setup-mode.@setup_mode[0].configured=1
uci commit gluon-setup-mode
uci set network.mesh_lan.auto=1
uci commit network
uci set system.@system[0].hostname=gluon-ffhb-2016.2.7+bremen1-x86-64-vmware
uci commit system
uci set fastd.mesh_vpn.enabled=1
uci commit fastd
~~~

**[------------------------------------------------------------------------------------------------------------------------- Zurück zum Inhalt:](#inhalt)**

### Damit der Router auf der Karte sichtbar wird, können die GEO Daten konfiguriert werden. Diese Daten aus der Freifunkkarte kopieren.
~~~
uci set gluon-node-info.@location[0]='location'
uci set gluon-node-info.@location[0].share_location='1'
uci set gluon-node-info.@location[0].latitude='_Breitengrad_'
uci set gluon-node-info.@location[0].longitude='_Längengrad_'
uci commit gluon-node-info
~~~
Nachdem wir den Router Konfiguriert haben starten wir diesen mit dem Befehl **reboot -n**  neu. 
Der Router ist nun in der Grundkonfiguration fertig. Die Geodaten mit dem uci Befehlssatz, kann auf der Freifunkkarte mit dem Pin erstellt werden.

**[------------------------------------------------------------------------------------------------------------------------- Zurück zum Inhalt:](#inhalt)**