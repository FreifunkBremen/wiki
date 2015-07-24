# VPN/Gateway Setup

Siehe https://github.com/FreifunkBremen/gateway-doku/blob/master/vpn-servers.md für die Details.

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
