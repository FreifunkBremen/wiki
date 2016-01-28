# Einrichtung eines x86 Rechners als Offloader

Für größere Freifunk-Installationen ist es sinnvoll, einen dedizierten Router für das Aufbauen der VPN-Verbindung zu nutzen. Da die herkömmlichen Plastik-Router relativ leistungsarm sind, ist Hardware mit etwas mehr Rechenleistung nötig. Hier wird man schnell bei herkömmlichen x86-Rechnern fündig.

Großer Beliebtheit erfreut sich der [Fujitsu-Siemens Futro S550 Thin-Client](http://sp.ts.fujitsu.com/dmsp/Publications/public/ds-FUTRO-S550-2.pdf). Mit seinen kompakten Ausmaßen, 15 Watt Stromverbrauch und genug Rechenleistung für über 50MBit VPN-Durchsatz wird dieser natürlich jetzt auch in Bremen getestet.

Es gibt grundsätzlich zwei mögliche Setups. Eine Möglichkeit ist das Nachrüsten einer zusätzlichen PCI-Netzwerkkarte oedr mit nur einer Netzwerkkarte und VLANs.

## Installation
Grundsätzlich bieten wir für alle x86-Rechner ein generisches Image an. Solange keine Spezialhardware verbaut ist, die extra Treiber benötigt, kann dieses ohne Probleme installiert werden. Der CF-Cardreader des Futro benötigt leider zusätzliche Treiber. Die Firmware muss also neu gebaut werden:

```
 make -j6 V=s GLUON_TARGET=ar71xx-generic && make -j6 V=s GLUON_TARGET=mpc85xx-generic && make -j6  V=s GLUON_TARGET=x86-kvm_guest && echo "CONFIG_PATA_ATIIXP=y" >> openwrt/target/linux/x86/generic/config-3.10 && make -j6 V=s GLUON_TARGET=x86-generic
```

Wichtig ist hierbei, den Paramter vor dem Bauen zu setzten. So kann der Futro dann auch auf seine CF-Karte zugreifen.

Wer einen CF-Cardreder Zuhause hat, überspielt das Image einfach auf die Karte des Futro. Es gibt auch eine Möglichkeit, ohne den Futro öffnen zu müssen. Dazu ein kleines Zitat aus dem [Freifunk-Forum](https://forum.freifunk.net/t/einfache-loesung-um-einen-futro-s550-offloader-zu-flashen-windows-linux-os-x/8988):
> 
> Ladet Euch das Gluon2Futro-USB-Stick-Image von [Github](https://raw.githubusercontent.com/oszilloskop/Gluon2Futro/master/gluon2futro.img) herunter, und transferiert es auf einen USB-Stick ( mit 'dd' oder 'Win32 Disk Imager12' ). Auf dem USB-Stick befindet sich danach ein Mini Linux1 auf einer FAT32 Partition.
> Der USB-Stick muss mind. 64MB groß sein. Alle bisher gespeicherte Daten auf dem USB-Stick gehen verloren!
> 
> Dann einfach euer gewünschtes Gluon-x86-Factory-Image (die gepackte Version *.img.gz) auf den vorbereiteten USB-Stick kopieren (das geht mit jedem Win/Linux/Mac PC per Datei-Manager des jeweiligen Betriebsystems). Wenn jetzt der Futro mit diesem USB-Stick gebootet wird, so wird das Gluon-x86-Image vollautomatisch auf die interne CF-Karte des Futros übertragen.
>
> Es gibt nach ca. 20-60 Sekunden auf jeden Fall eine akustische Rückmeldung:
> Alles okay = 5 x Piepen
> Nix okay = 10 Sekunden wildes Gepiepse
> 
> Das war's schon.

Jetzt bootet der Futro in den Configmode und kann entsprechend konfiguriert werden.

## Das Dual-NIC-Setup
Die technisch einfachere Variante ist das Einbauen einer zusätzlichen Netzwerkkarte. Dazu ist eine um 90° gewinkelte Risercard nötig (Freifunker anon6789 hat noch einige passende über). Sobald die Netzwerkkarte eingebaut ist, hat der Router eine LAN und eine WAN Schnittstelle (WAN ist die PCI-Karte).

## Das VLAN-Setup
Das VLAN-Setup ist technisch anspruchsvoller und es ist noch ein zusätzlicher Freifunkrouter nötig (oder andere VLAN-Hardware). Dabei wird das WAN-Netz vom Router über ein VLAN an den Offloader weitergereicht und in einem weiteren tagged VLAN wird gemesht. Der Freifunkrouter schleift das WAN also nur durch, ohne selbst das VPN aufzubauen.

Zuerst wird der Futro wie folgt konfiguriert:

```
uci set network.wan.ifname=eth0.7
uci set network.mesh_lan=interface
uci set network.mesh_lan.auto=1
uci set network.mesh_lan.ifname=eth0.8
uci set network.mesh_lan.macaddr=DENKDIRWASAUS !!!!
(http://www.miniwebtool.com/mac-address-generator/)
uci set network.mesh_lan.mesh=bat0
uci set network.mesh_lan.proto=batadv
uci commit
```
Auf VLAN 7 ist also das WAN-Netz und auf VLAN 8 das LAN, worüber gemescht wird.

Auf dem zusätzlichen Freifunkrouter muss die /etc/config/network angepasst werden:

```
config switch
option name 'switch0'
option reset '1'
option enable_vlan '8'

config switch_vlan
option device 'switch0'
option vlan '8'
option ports '0 1t 3 4'

config switch_vlan
option device 'switch0'
option vlan '7'
option ports '1t 2'
```

Und anschließend Mesh-On-Lan auf dem Router aktivieren:

```
uci set network.mesh_lan.auto=1
uci commit
```

Eventuell muss etwas herumgespielt werden mit den Ports, da diese sich je nach Router unterscheiden. Dabei hilft der Befehl

```
swconfig dev switch0 show
```


tbc