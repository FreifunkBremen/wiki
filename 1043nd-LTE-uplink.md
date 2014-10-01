# Freifunk Bremen

## Einrichtung eines Freifunk-Router mit Uplink über Tethering

(Notizen, wird noch ausführlicher)

<code>opkg update</code>

<code>opkg install kmod-usb2 kmod-usb-net </code>

eventuell Pakete: <code> kmod-usb-net-rndis kmod-usb-net-cdc-ether usbutils udev </code>

<code>insmod ehci-hcd</code>

<code> uci del network.wan </code>

<code>uci set network.wan=interface</code>

<code>uci set network.wan.ifname=usb0</code>

<code>uci set network.wan.proto=dhcp</code>

<code>uci commit network </code>

<code> ifup wan </code>

aus:

http://wiki.openwrt.org/doc/howto/usb.tethering

http://wiki.openwrt.org/doc/howto/usb.essentials
