# VPN/Gateway Setup

[[_TOC_]]

## Dienste die auf den Gateways laufen:

### fastd (Knoten VPN)
* VPN für Verbindung zwischen Knoten und Gateway
* Verbindung zwischen Gateways (mit Batman)

### tinc ([IC-VPN](http://wiki.freifunk.net/IC-VPN))

* VPN P2P Daemon für Verbindung zu allen Rechner im ICVPN
* Dynamisch vollvermascht, keine Server
* Verbindung wird vorgehalten zu allen Teilnehmern
* Layer2 10.207/16
* Pubkeys anderer in [Git Repo](https://github.com/freifunk/icvpn/tree/master/hosts) + IP-Netz
* Uplink ipv6 nach Berlin

### bird (Routen)
* Routing Daemon für Routen aus ICVPN
* Spricht über Layer2 Netz aus TINC BGP und tauscht Routen aus
* Wird generiert ([Script](https://github.com/freifunk/icvpn-scripts))

### openvpn (hide.me/Berlin uplink)

* mit Defaulroute wird Traffic über VPN-Uplink 
* Roule-Based-Routing je nachdem ob aus Freifunk-Netz oder nicht
* ca. 5TB (VPN01) und 1.25TB ca. 4MB/s rx und 7MB/s

### unbound (DNS-Server)
* alle anderen DNS Anfragen

### ntpd (NTP-Server)
* Verteilt Zeit an Router (die haben keine Batterie)
* wichtig aufgrund Abhängigkeiten (z.B. Update usw.)

### BATMAN advanced
* v2013.4 und andere sind Inkompatibel zueinander
* Es muss manuell die ältere Version installiert werden z.B. bei Debian jessy
* Gatewayselection: wird in Packet mit Annouced (Gateway-mode), funktioniert schlecht
* Router sucht sich das aktuell beste Gateway aus und leitet Broadcast als Unicast an das Gateway

### ALFRED master

* Master/Slave
 * Master sammeln Daten ein und tauschen Daten unterneinander
 * Slave lauscht auf Master und schickt Daten dahin
 * Slaves senden alle Daten eigenständig
* Server
 * Server muss auf jedem Gerät laufen entweder im Master oder Slave mode
 * Client speist Daten in den Server auf jedem Gerät

### dnsmasq (DHCP-Server)
* Verteilt Adresse, Gateways, DNS (Gateways verteilen sich selbst)
* vpn0x : 10.196.x.0 - 10.196.x9.255 = 2500 pro VPN Server 
* ist todo, da Routen nicht genau (Bitmuster) über Bird verteilt werden können
 * eventuell /20 verteilen, um "kleinster Bereich gewinnt", da die anderen Server nur /16 accouncen

### nds (authorativer DNS-Server)
* Auflösung für ffhb.de Zone



## Anderes:

### ansible
* Server automation system
* Werden aus Rezepten gefüttert
* z.B. fastd installation und Einrichten
* Kann als Doku genutzt werden
* Rollen können Rechner spezifizieren (z.B. Rechner für Website, ein für ICVPN...)

### /etc/network/interfaces

### diverse Scripte (mkbgp mkdns mkroa mksmoekping)

### Script um Gatewaydaten auch in Alfred zu speisen (ffnord-gateway-alfred)


## Grundlegend:

### Layer:
* 1: Ethernet / 802.11
* 2: MAC-Adresse
* 3: IP-Adressen
 * 10.196.0.0/16 IPv4 (im Mesh /17)
 * 2001:bf7:540 IPv6

### Knoten und Endgeräte über WLAN, BATMAN Routing (Layer 2)
* LAN erstreckt sich von CLient zu Gateway
* VPN01 muss wissen, wo sich MAC von Client X befindet (das macht Batman)
* BATMAN speichert in Routingtabelle Wege zu Rechnern + Matrik (TQ 0-255)
 * sehr schnelle Aktualisierung für Roaming & Failover und Berechnung von Metrik
* Hop-Penalty zu Gateways relativ hoch, damit die VPN Verbindung nicht der Mesh-Funkverbindung bevorzugt wird
