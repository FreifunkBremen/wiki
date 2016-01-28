# Einrichtung eines x86 Rechners als Offloader

Für größere Freifunk-Installationen ist es sinnvoll, einen dedizierten Router für das Aufbauen der VPN-Verbindung zu nutzen. Da die herkömmlichen Plastik-Router relativ leistungsarm sind, ist Hardware mit etwas mehr Rechenleistung nötig. Hier wird man schnell bei herkömmlichen x86-Rechnern fündig.

Großer Beliebtheit erfreut sich der Fujitsu-Siemens Futro S550 Thin-Client. Mit seinen kompakten Ausmaßen, 15 Watt Stromverbrauch und genug Rechenleistung für über 50MBit VPN-Durchsatz wird dieser natürlich jetzt auch in Bremen getestet.

Es gibt grundsätzlich zwei mögliche Setups. Eine Möglichkeit ist das Nachrüsten einer zusätzlichen PCI-Netzwerkkarte oder mit nur einer Netzwerkkarte und VLANs.

## Das Dual-NIC-Setup
Die technisch einfachere Variante ist das Einbauen einer zusätzlichen Netzwerkkarte. Dazu ist eine um 90° gewinkelte Risercard nötig (Freifunker anon6789 hat noch einige passende über). Sobald die Netzwerkkarte eingebaut ist, hat der Router eine LAN und eine WAN Schnittstelle (WAN ist die PCI-Karte).

## Das VLAN-Setup
Das VLAN-Setup ist technisch anspruchsvoller und es ist noch ein zusätzlicher Freifunkrouter nötig (oder andere VLAN-Hardware).

tbc