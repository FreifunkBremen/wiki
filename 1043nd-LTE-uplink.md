# Freifunk Bremen

## Einrichtung eines mobilen Freifunk-Router mit Uplink über Tethering

### Hardware

Zum mobilen Betrieb ist zum einen ein Akkupack mit passendem Hohlstecker-Adapter nötig. Außerdem ist ein Router mit USB-Schnittstelle nötig. Hier exemplatisch ein TP-Link TL-WR1043ND. Zum Tethern wird außerdem ein Android-Smartphone nötig.

### Einrichtung USB-Tethering
Zuerst Paketquellen aktualisieren und nötige Pakete installieren : 

```
opkg update
opkg install kmod-usb2 kmod-usb-net
```
eventuell Pakete ist es notwendig, folgende Pakete auch zu installieren [1] 

<code> kmod-usb-net-rndis kmod-usb-net-cdc-ether usbutils udev </code>

USB-Modul laden:

<code>insmod ehci-hcd</code>

WAN-Interface auf USB-Schnittstelle legen:

```
uci del network.wan 

uci set network.wan=interface

uci set network.wan.ifname=usb0

uci set network.wan.proto=dhcp

uci commit network
```
WAN-Schnittstelle aktivieren

<code> ifup wan </code>


### Einrichtung GPS

Unter Android läuft die App "GPS Logger", welcher nicht nur in Dateien schreiben kann, sondern auch parametrisierte http-Anfragen versenden kann. Längen- und Breitengrat werden also über eine spezielle URL an ein CGI-Script im uhttpd gesendet.

Die URL kann wie folgt aussehen:

<code>http://node.ffhb/cgi-bin/setGeo?10?20</code>

Folgendes Script liegt in <code>lib/gluon/status-page/www/cgi-bin</code> und nimmt Breiten- und Längengrad entgegen:

```
#!/bin/sh 
echo "Content-type: text/html"
echo ""
long=$(env | grep REQUEST_URI | cut -d"?" -f2 )
lat=$(env | grep REQUEST_URI | cut -d"?" -f3 )
echo ""
$(/bin/sed -i "s/.*latitude.*/option latitude \'$lat'/" /etc/config/gluon-node-info)
$(/bin/sed -i "s/.*longitude.*/option longitude \'$long'/" /etc/config/gluon-node-info)
```

In der Androidapp unter Protokollierungseinstellungen muss nun als "Logge zu einem Server" folgender Link angegeben werden:

<code>http://NODE_IP/cgi/setGeo?%LON?%LAT</code>

Der Haken bei "Logge zu einem Server" muss gesetzt werden.


aus:

http://wiki.openwrt.org/doc/howto/usb.tethering

http://wiki.openwrt.org/doc/howto/usb.essentials

Android-App:

https://play.google.com/store/apps/details?id=com.mendhak.gpslogger&hl=de
