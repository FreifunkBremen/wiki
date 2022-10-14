Evtl. wird das der neue Butter & Brot Freifunk Router.

## Inhalt

[[_TOC_]]

### 1.) "Xiaomi Mi Router 4A"

Information: gibt's in zwei Varianten (100Mbit und Gigabit)
kostet zwischen 15€ (100MBit) und 35€ (Gbit)
https://www.mi.com/de/product/mi-router-4a-gigabit-edition/
https://openwrt.org/toh/xiaomi/mi_router_4a_mir4a_100m
https://openwrt.org/inbox/toh/xiaomi/xiaomi_mi_router_4a_gigabit_edition
Verfügbarkeit:
    gibt's derzeit bei Amazon, Ebay
    gibt's derzeit aber nicht bei MediaMarkt etc.
wird von der neusten Gluon-Version unterstützt (s. https://gluon.readthedocs.io/en/latest/releases/v2022.1.html#added-hardware-support)
es gibt auch eine inoffizielle Freifunk-Bremen-Firmware für dieses Gerät: https://code.bremen.freifunk.net/ffhb/firmware/gluon-site-ffhb/-/jobs/1497/artifacts/file/gluon/output/images/sysupgrade/gluon-ffhb-2019.1.3+bremen9-build137-xiaomi-mi-router-4a-gigabit-edition-sysupgrade.bin


~~~
mehr in Kürze
~~~

Text

**[------------------------------------------------------------------------------------------------------------------------- Zurück zum Inhalt:](#inhalt)**

### 2.) Xiaomi Mi Router 4A (MIR4A) Gbit

Achtung: Unterschiedliche Routerhardware. (Xiaomi Mi Router 4A (MIR4A) 100M) ist nicht (Xiaomi Mi Router 4A (MIR4A) Gbit)

Warnung Xiaomi liefert seit 2020 Mi Router 4A Gigabit Edition-Geräte ohne angemessene Abschirmung aus. Beachten Sie, dass diese aufgrund von Funkstörungen Probleme verursachen können. Trotzdem ist es flashbar.

Warnung 03/2022 OpenWrt funktioniert derzeit nicht auf Geräten mit Eon- oder CFeon-Flash-Chips. [Klicken Sie auf den Link.](https://openwrt.org/inbox/toh/xiaomi/xiaomi_mi_router_4a_gigabit_edition#unable_to_install_openwrt_to_new_r4a_gigabit_edition) 
Es wurden keine Probleme mit Winbond- oder GigaDevice-Flash-Chips gemeldet, die in früher hergestellte Einheiten eingebaut wurden. Andere Unterschiede wurden auch bei dem chinesischen Modell beobachtet, das im September 2021 hergestellt wurde. [Klicken Sie auf Link](https://forum.openwrt.org/t/observations-on-xiaomi-mir4ag-newer-firmware/127373)

Warnung 10/2022 Xiaomi liefert derzeit v2 der 4A-Gigabit-Edition aus, die anhand der FW-Version 2.30.20 und des Namens identifiziert werden kann, wenn ihr eine IP von einem DHCP (nicht Ihren ISPs) über den WAN-Port, MiWiFi-R4AV2, zugewiesen wird. Dieses Modell kann nicht mit Openwrt geflasht werden. [Klicken Sie auf Link.](https://forum.openwrt.org/t/support-for-xiaomi-router-ac1200-rb02/124962)

Achtung: Gbit ports sind 3 (1x WAN, 2x LAN) und nicht 2xWAN, 1xLAN

Achtung: Die Buchsen haben keine Aussparung für das LAN Kabel, könnte eng werden.



**[------------------------------------------------------------------------------------------------------------------------- Zurück zum Inhalt:](#inhalt)**

### 3. SSH Zugang

ssh root@<RouterIP> password is admin.

**[------------------------------------------------------------------------------------------------------------------------- Zurück zum Inhalt:](#inhalt)**

### 4. TTL UART
Als erstes löte ich einige Kabel an die UART-Pins auf der Platine und verbinde sie mit einem TTL-zu-USB-Adapter. 
Ich kann die übliche Linux-Ausgabe von einem Router sehen, aber leider kann ich nicht damit interagieren: 
Ich kann U-Boot nicht daran hindern, automatisch zu booten, und ich kann die Befehlszeilenschnittstelle 
nicht aufrufen, sobald die Standard-Firmware gebootet hat.


**[------------------------------------------------------------------------------------------------------------------------- Zurück zum Inhalt:](#inhalt)**


**Diese Anleitung ist wie immer ohne Gewähr. Für Anregungen und Tipps immer offen.**
