Es gibt endlich wieder eine [Breminale](https://breminale-festival.de/), und wir bauen ein kostenloses WLAN auf!

- Breminale-Beginn: Mi, 13.7., nachmittags
- Breminale-Ende: So, 17.7., nachts

## Kommunikation
- IRC: [#ffhb_events im Hackint](irc://irc.hackint.org/ffhb_events)
    - im Browser: [Webchat](https://webirc.hackint.org/#ircs://irc.hackint.org/#ffhb_events?nick=Gast_?)
- Hackmd-Pad: <https://md.darmstadt.ccc.de/9yPqMGH3RCWF7bqqu77Zeg>

# Freifunk Bremen: Breminale 2022

## Überblick
- Breminale-Beginn: Mi, 13.7., nachmittags
- Breminale-Ende: So, 17.7., nachts
- Programm: https://breminale-festival.de/
- Wiki-Seite: https://wiki.ffhb.de/Events/Breminale/2022/Freifunk-Bremen-auf-der-Breminale-2022.md
- IRC-Channel: [#ffhb_events im Hackint](irc://irc.hackint.org/ffhb_events)
    - Webchat: <https://webirc.hackint.org/#ircs://irc.hackint.org/#ffhb_events?nick=Gast_?>
    - Matrix: <https://matrix.to/#/#ffhb_events:hackint.org>
- Dudle: https://dudle.hackerspace-bremen.de/FFHB_Breminale_2022/
- PMR Funkkanal: 4, Subkanal 2

## Termine
- Sa., 9.7., 10:30 am Bauwagen: Treffen!


## Zu Besorgen:
- [ ] Eisfach (ist schon in Arbeit?)
- [ ] Eis!
- [x] Mini-PC
    - PI v4 [name=olli]
    - SD [name=geno]
- [ ] Telefon für den Bauwagen
- [ ] SIM-Karte für das Bauwagen-Telefon (am besten die vom letzten Mal!)
- [x] Müllsäcke

## TODO
Neu Liste:

"Hardware":
- [ ] AC-Mesh Recht in der RadioBremen macht immer wieder Probleme bei Pings ...
    - bin mir unsicher ob es solved ist
- [ ] AC-Mesh Recht bei 3M (offline seit 18h)
- [ ] AC-Mesh auf Kuechen (KLO) macht Probleme ggf. Archer dazustellen

"Software":
- [x] SNMP Monitoren (NanoBeam und Switch)
- [ ] Well-label Logs in Promtail (nicht nur IP, sondern auch Namen)
- [ ] **Bessere** Channel-Verteilung
- [ ] Pings auf <map.onffhb.de> der NanoBeams
- Firmware:
  - [ ] ebtables for status-page
  - [ ] LLDP
    - [ ] fix that module (do not crash) https://github.com/freifunk-gluon/packages/pull/189
  - [ ] watchdog refactoren -> see SSID-Changer


----
Alte Liste:
- [ ] Breminale-Plan in handlichem Format besorgen (A4, A3 oder so)
- [x] geojson aktualisieren? 
  - alte Version: https://github.com/FreifunkBremen/internal-maps
  - karte: https://map.onffhb.de/#!/en/map und Dashboard: [Grafana: Breminale 2022](https://grafana.ffhb.de/d/_HkU4Yenk/breminale-2022?orgId=1) 
  - also: Zelt-Positionen und so neu eintragen, damit wir unsere Knoten darauf anzeigen können
- [ ] Treffpunkt für reguläres Freifunk-Treffen am Freitag (15.7.) festlegen
    - [ ] und im Kalender etc. anpassen
- [ ] wo sind die ganze AC-Mesh hin? Sollten wir nicht ca. 20 Stück haben??
- [ ] Outdoor-Boxen im Pad eintragen (s.u., Abschnitt "Outdoor-Boxen"): mit Box-Nr, und Inventar-Nummern und MAC-Adressen der Geräte
- [x] sobald wir beim Bauwagen das öffentliche Netz "gut" ausstrahlen: den Freifunk-Knoten ffhb-18d6c7f9e1fc (https://map.bremen.freifunk.net/#!/de/map/18d6c7f9e1fc) abschalten
    - [x] und ebenso den Knoten bei der Küche (breminale-kueche / https://map.bremen.freifunk.net/#!/de/map/6466b36f8f8c) durch einen Breminale-Knoten ersetzen
--- 
### Hardware TODOs
- [x] Archer C7 beim Papp fixen (damit die auf der Karte auftauchen)
    - haben die auch noch eine alte Firmware?
    - Welche C7 gelöst ?
- [x] AC-Mesh in der Flut links abbauen -> Firmware broken oder so? Not Reachable
- [ ] Ac-Mesh Recht in der RadioBremen macht immer wieder Probleme bei Pings ...
    - bin mir unsicher ob es solved ist
- [x] AC-Mesh auf Kuechen (KLO) macht Probleme ggf. Archer dazustellen

### Optimisung TODOs
- [x] Channel Verteilung [name=geno]
    - [ ] geht noch besser ... 
- [x] fremde FFHBs abschalten (Roaming)
- [x] kaputte Geräte entfernen (siehe Hardware TODOs)
- [ ] NanoBeams monitoren
- [x] Airtime monitoren

## Zugangsdaten
- dieser SSH-Key soll auf alle Breminale-Knoten drauf: https://downloads.bremen.freifunk.net/keys/ssh-nodes/id_rsa.ffhb_breminale_2022.pub
    - der Private Key dazu liegt im Ticket-System

## Inventur
Archer C7:
- 1x vmtl. defekt (N0057)
- 3x Testgeräte auf dem Tisch (N0070, N0052, N0068)
- graue Kiste: 8x geflasht
- transparente Kiste: 11x geflasht
- Modell-Outdoorbox ("Kochtopf"): 1x geflasht

AC Mesh:
- 2x kaputter Reset-Knopf
- 10x geflasht
- 1x am Baum hinterm Bauwagen (im Betrieb)


### Outdoor-Boxen
Übertragen in Ansible-Inventory:
https://github.com/FreifunkBremen/ansible-events/blob/master/inventories/breminale2022

## Firmware
- wird generell auf <code.bremen.freifunk.net> gebaut: https://code.bremen.freifunk.net/ffhb/firmware/gluon-site-ffhb/-/pipelines?ref=breminale

### ISSUES
- [ ] ebtables for status-page
- [ ] LLDP
  - [x] prebuild without `respondd-module-lldp` till work
  - [ ] fix that module (do not crash) https://github.com/freifunk-gluon/packages/pull/189
- [x] switch to client without VLAN
- [ ] watchdog refactoren -> see SSID-Changer

### CHANGELOG / Image Links:
- [BuildNr **82**](https://code.bremen.freifunk.net/ffhb/firmware/gluon-site-ffhb/-/jobs/431/artifacts/browse/gluon/output/images/sysupgrade/):
  - install gluon-ebtables correct
  - switch to client native (ISSUE maybe solved)
- **Build 81 - broken -> do not use**
  - new version naming 
  - disable temporary respondd-module-lldp
- **Build 80 - broken -> do not use**
  - fix LLDP
- [BuildNr **79**](https://code.bremen.freifunk.net/ffhb/firmware/gluon-site-ffhb/-/jobs/428/artifacts/browse/gluon/output/images/sysupgrade/):
  - disable old ssid-changer
- [BuildNr **78**](https://code.bremen.freifunk.net/ffhb/firmware/gluon-site-ffhb/-/jobs/427/artifacts/browse/gluon/output/images/sysupgrade/):
  - fix logging Server 
- [BuildNr **77**](https://code.bremen.freifunk.net/ffhb/firmware/gluon-site-ffhb/-/jobs/426/artifacts/browse/gluon/output/images/sysupgrade/):
  - first release \o/
  - fix mgmt vlan

## Management
- Ansible für Nodes
  - [x] generate Address from NodeID
  - [x] group by Owner
  - [x] "random" Node-Position around group
  - [x] "random" Channels in Group 
      - [ ] geht noch besser
- Dashboards
  - [Map.onffhb.de](https://map.onffhb.de/#!/en/map) <- IPv6 only (z.B. von der Breminale xD) 
  - [Grafana: Breminale 2022](https://grafana.ffhb.de/d/_HkU4Yenk/breminale-2022?orgId=1)
  - TODOs
    - ~~mit Geojson von Yanic (Grafana soll nur PINGs darstellen)~~
    - [x] mit Geojson vom Gelände
    - [ ] Logs (finding strange behavour ...)
    - Clustered nach Owner
      - [x] Nodes mit vielen **Airtime**
      - [x] Nodes mit vielen **Clients**
    - [ ] Traffic darstellen (SNMP)
    - [x] Yanic Prometheus-Exporter refactoren -> just give current cached state
- Karte
  - [x] Yanic forward (auf PI-Vorort)
- Logging
  - [x] Loki (bei [name=genofire] - in Container ... ggf. Datalost)
  - Promtail (auf PI-Vorort mit syslog-ng)
    - [x] Installiert
    - [ ] Well-label Logs
      - https://vikaspogu.dev/posts/loki-rsyslog-k3s/ (relabels -> which labels are known by syslog-ng?)
      - stripe time infront of Log-Message
- Metriken
  - [x] Prometheus
- Alerting
  - Blackbox-Exporter / Ping
    - [x] Yanic-Stats
    - [x] RiFu
  - [x] Alertmanager (ggf. von [name=genofire] : https://alerts.sum7.eu)
  - [x] Matrix-Bot [name=genofire]
    - Criticial (Backbone):
      - IRC-Channel: [#ffhb_status im Hackint](irc://irc.hackint.org/ffhb_status)
      - Webchat: <https://webirc.hackint.org/#ircs://irc.hackint.org/#ffhb_status?nick=Gast_?>
      - Matrix: <https://matrix.to/#/#ffhb_status:hackint.org>
    - Normal (Nodes / Collected per Yanic:
      - IRC-Channel: [#ffhb_status im Hackint](irc://irc.hackint.org/ffhb_status)
      - Webchat: <https://webirc.hackint.org/#ircs://irc.hackint.org/#ffhb_status?nick=Gast_?>
      - Matrix: <https://matrix.to/#/#ffhb_status:hackint.org>
### LWLcom - Uplink
- [x] an MikroTik
- [x] IPv6 verteilen
- [x] PI-Anbindung per nativem IPv6 optimieren

## Installationen

### Richtfunk
#### Liste mit IP-Adressen für RiFu

Range: 10.100.15.x (/20; Netzmaske: 255.255.240.0; Gateway: 10.100.0.1)

- https://192.168.1.19 :no_bell:
  - NanoBeam Provisorium Bürocontainer
- https://192.168.1.20  :no_bell:
  - NanoBeam Breminale Büro Gebäude
- https://10.100.15.5 :bell:
  - TP-Link PoE-Switch im Bauwagen
  - Modell: TP-Link SG-2210P V1.0
  - Inventar-Nr: N0021
  - User: admin
- https://10.100.15.6 :bell: 
  -  PoE-Switch im Bauwagen 
- https://10.100.15.10 :no_bell:
  - PowerBeam am Bauwagen
  - SSID: noc2bremen10
  - AP: :white_check_mark: 
- https://10.100.15.11 :no_bell:
  - PowerBeam am Schwimmverein
  - SSID: noc2bremen10
  - AP: :x:
- https://10.100.15.12 :bell:
  - NanoBeam Bauwagen -> Schleuse
  - SSID: bauwagen2schleuse
  - AP: :white_check_mark:
- https://10.100.15.13 :bell:
  - NanoBeam Schleuse -> Bauwagen
  - SSID: bauwagen2schleuse
  - AP: :x: 
- https://10.100.15.14 :bell:
  - NanoBeam Bauwagen -> Flut
  - SSID: bauwagen2flut
  - AP: :white_check_mark: 
- https://10.100.15.15 :bell:
  - NanoBeam Schleuse -> Laterne
  - SSID: schleuse2laterne
  - AP: :white_check_mark: 
- https://10.100.15.16 :bell:
  - NanoBeam Laterne -> Schleuse
  - SSID: schleuse2laterne
  - AP: :x:
- https://10.100.15.17 :bell:
  - NanoBeam Flut -> Bauwagen
  - SSID: bauwagen2flut
  - AP: :x: 
- https://10.100.15.18 :bell:
  - NanoBeam Gastro -> Bauwagen
  - SSID: bauwagen2schleuse
  - AP: :x:
- https://10.100.15.19 :bell:
  - NanoBeam Bauwagen -> RadioBremen
  - SSID: noc2radiobremen
  - AP: :white_check_mark: 
- https://10.100.15.20 :bell:
  - NanoBeam RadioBremen -> Bauwagen
  - SSID: noc2radiobremen
  - AP: :x:
- https://10.100.15.21 :bell:
  - NanoBeam Neuland -> Bauwagen
  - SSID: bauwagen2flut
  - AP: :x: 
- https://10.100.15.22 :bell:
  - NanoBeam MitteLichtmast -> x
  - :warning: noch kein WIFI configuriert
- https://10.100.15.23 :bell:
  - NanoBeam 3mBretter -> Schleuse
  - SSID: schleuse2laterne
  - AP: :x:
- https://10.100.15.24 :bell:
  - NanoBeam FahnenMast -> Schleuse
  - SSID: schleuse2laterne
  - AP: :x:
- https://10.100.15.25 :no_bell:
  - frei, nicht vergeben
- https://10.100.15.26 :bell:
  - NanoBeam Eis -> Bauwagen
  - SSID: bauwagen2schleuse
  - AP: :x: 
 
#### NanoBeam
- Default: 
    - https://192.168.1.20
    - username: ubnt
    - password: ubnt
- PW ändern
- SSID
- Channel über 5500
- Advance:
    - OutPower auf Max
    - Auto Adjust Distance: off
    - Distance auf Max (22.5km)
    - PowerControll aus
- VLAN `100` mit IP siehe oben, eine freie
- SNMP aktivieren `public`, Ort `...`, Kontakt `ffhb`
- Syslog / Remote Logging: `10.100.0.10` mit Port `1514`
- Auf PI in `/home/ffhb/scrape/ping_unifi.yml` eintragen:
    - group: backbone 
    - type: rifu 
    - SSID: ?
    - falls, er die SSID austrahlt:
        - ap: true
    - Hostname: ?
    - Latitude: ?
    - Longitude: ?
    - IP-Adresse: ?

### Zelte

### Weiteres

## Um auf die alten Nodes draufzukommen
### Vorbereitungen:
In `.ssh/config` eintragen (falls nötig, legt den Ordner und die Datei neu an):

```toml
Host *
    HostkeyAlgorithms +ssh-rsa
    PubkeyAcceptedKeyTypes +ssh-rsa

Host fe80::1441:95ff:fe40:f7dc
    ## nicht in known_keys übernehmen (da IP-Adresse von allen Routern unterstütz werden)
    StrictHostKeyChecking no
    UserKnownHostsFile /dev/null
```

Und holt euch die privaten SSH-Key für die alten Geräte: ladet die ganzen Dateien von https://downloads.bremen.freifunk.net/keys/ssh-nodes/
und legt die unter .ssh/ ab.

Und ladet euch den _privaten_ SSH-Key für die Breminale 2022 runter. Den findet ihr im Ticketsystem unter <https://tasks.ffhb.de/K16> (falls ihr keine Zugriff darauf habt, fragt jemanden im Bauwagen).
Klickt auf der Ticket-Seite auf "Show Secret" und speichert den Text in einer neuen Datei unter `.ssh/id_rsa.ffhb_breminale_2022`

Dann setzt die Berechtigungen für die SSH-Keys: `chmod go-r ~/.ssh/id_rsa*`

Und sucht euch den Namen von eurem LAN-Interface raus: schaut bei der Ausgabe von "ip a" nach einer Zeile, die mit "en" oder "eth" anfängt, z.B. so:
`2: enp2s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000`
Dann ist enp2s0 euer Netzwerk-Interface.


### Knoten erreichen:
- stöpselt das LAN-Kabel bei dem Knoten in den blauen Port
- versucht, den Knoten per "Link-Local IPv6" anzusprechen: ping -L ff02::1%enp2s0 (nehmt da den Namen von eurem Netzwerkinterface).
- Da werden dann hoffentlich Antworten angezeigt, z.B. so:
```bash
# ping -L ff02::1%enp2s0
PING ff02::1%enp2s0(ff02::1%enp2s0) 56 Datenbytes
64 Bytes von fe80::1ad6:c7ff:fefc:dd25%enp2s0: icmp_seq=1 ttl=64 Zeit=0.412 ms
64 Bytes von fe80::1441:95ff:fe40:f7dc%enp2s0: icmp_seq=1 ttl=64 Zeit=0.521 ms (DUP!)
64 Bytes von fe80::1ad6:c7ff:fefc:dd25%enp2s0: icmp_seq=2 ttl=64 Zeit=0.388 ms
64 Bytes von fe80::1441:95ff:fe40:f7dc%enp2s0: icmp_seq=2 ttl=64 Zeit=0.506 ms (DUP!)
```

Dann kopiert euch eine dieser Adressen und versucht, per SSH darauf zu kommen: `ssh root@fe80::1441:95ff:fe40:f7dc%enp2s0`

Falls ihr eine Fehlermeldung bekommt:
- lest euch die Fehlermeldung durch! Die kann durchaus sinnvolle Hinweise geben!
- falls ihr die Meldung "Permission denied (publickey)." bekommt, benutzt ihr die falsche Key-Datei.
    - startet dann den ssh-Befehl mit "-i" und dem Namen einer anderen Key-Datei! Z.B.: `ssh root@fe80::1441:95ff:fe40:f7dc%enp2s0 -i .ssh/id_rsa.ffhb_breminale_2019`
    - Und stellt sicher, dass ihr die Änderungen in der .ssh/config drin habt
    - Sollte das Gerät mit original Firmware geflashed sein ist der Benutzewrname: ubnt, das Passwort: ubnt

- sobald ihr erfolgreich per SSH auf dem Knoten seid, könnt ihr weitermachen und das Image auf den Knoten kopieren:
- weiteroben unter "Firmware" steht, wo die aktuelle Firmware zu finden ist. Ladet euch da die Datei für euer Router-Modell runter (achtet auf den Modellnamen und evtl. die Versionsnummer)
- kopiert die heruntergeladene .bin-Datei per "scp" auf den Knoten: `scp -O -i ~/.ssh/id_rsa.ffhb_breminale_2019 gluon-ffhb-breminale2022-13-g347e8fd~HEAD77-tp-link-archer-c7-v2-sysupgrade.bin "root@[fe80::1441:95ff:fe40:f7dc%enp2s0]:/tmp/gluon.bin"`
    - benutzt in dem Befehl den richtigen Dateinamen und die richtige Adresse
    - falls ihr bei `ssh` vorher auch eine `-i`-Option verwendet habt, müsst ihr die gleiche Option hier auch wieder verwenden!
- geht wieder per `ssh` auf den Knoten und führt das Upgrade durch: `sysupgrade -n /tmp/gluon.bin`
    - während das Upgrade läuft, dürft ihr den Router nicht ausschalten!
- nach ein paar Minuten solltet ihr wieder eine Netzwerk-Verbindung bekommen (am blauen Port)
    - und die WLAN-Leuchten am Knoten sollten dann leuchten
### Flashen bei original firmware
Bei neuer original firmware muss ggf. erst ein downgrade durchgeführt werden, bevor die freifunk Firmware mit sysupgrade geflashed werden kann:
https://wiki.freifunk-franken.de/w/Firmwareinstallation/UbiquitiUnifiACMesh#Downgrade_der_Originalfirmware


## AC Mesh
### Ralf
- [x] x9ij
- [x] o89N
- [x] R6R8 (9B7B) N0098
- [X] DtuU (D548) 
- [x] GZdT (D505)
- [ ] Vtri (D2C6)
- [x] 1guB (D581)
- [x] Kyvw 
- [ ] Eine noch bei Bremen 10
- [x] Eine bei Olli (N0125)

### Freifunk
- [x] fH4a (N0097) -> Plutexe
- [ ] R6R8 (N0098) -> Plutex?
- [ ] N0099 -> ggf. schon da
- [ ] N0100 -> ggf. schon da
- [ ] seld (77DC) N0101
- [ ] N0102 -> In Bremerhaven (JEO fragt nach)
- [X] N0103 -> Olli
- [ ] N0104 -> ggf. schon da
- [x] 2ymf (7863) N0105
- [X] d2GH (7763) N0106
- [X] (D3EE) hing oben am Baum beim Bauwagen
- [x] 77C2
