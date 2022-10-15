Evtl. wird das der neue Butter & Brot Freifunk Router. Es wird ein Nachfolger für 4Mb Geräte wie den TP-Link WR841 gesucht.
Preis und Leistung des Xiaomi 4A Gigabit Edition sind Beeindruckend. Hier mein Eindruck zu dem Gerät.

### Mein Ergebnis vorab: Als Bürgergerät ungeeignet, Bastelkiste. Das Gerät ist was für Freifunkbastler. Stand 15.10.2022

## Inhalt

[[_TOC_]]

### 1.) "XR4A XIAOMI Mi Router 4A Gigabit Edition"

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

Warnung Xiaomi liefert seit 2020 Mi Router 4A Gigabit Edition-Geräte ohne angemessene Abschirmung aus. Beachten Sie, dass diese aufgrund von Funkstörungen Probleme verursachen können. 

Warnung 03/2022 OpenWrt funktioniert derzeit nicht auf Geräten mit Eon- oder CFeon-Flash-Chips. [Klicken Sie auf den Link.](https://openwrt.org/inbox/toh/xiaomi/xiaomi_mi_router_4a_gigabit_edition#unable_to_install_openwrt_to_new_r4a_gigabit_edition) 
Es wurden keine Probleme mit Winbond- oder GigaDevice-Flash-Chips gemeldet, die in früher hergestellte Einheiten eingebaut wurden. Andere Unterschiede wurden auch bei dem chinesischen Modell beobachtet, das im September 2021 hergestellt wurde. [Klicken Sie auf Link](https://forum.openwrt.org/t/observations-on-xiaomi-mir4ag-newer-firmware/127373)

Warnung 10/2022 Xiaomi liefert derzeit v2 der 4A-Gigabit-Edition aus, die anhand der FW-Version 2.30.20 und des Namens identifiziert werden kann, wenn ihr eine IP von einem DHCP (nicht Ihren ISPs) über den WAN-Port, MiWiFi-R4AV2, zugewiesen wird. Dieses Modell kann nicht mit Openwrt geflasht werden. [Klicken Sie auf Link.](https://forum.openwrt.org/t/support-for-xiaomi-router-ac1200-rb02/124962)

Achtung: Gbit ports sind 3 (1x WAN, 2x LAN) und nicht 2xWAN, 1xLAN

Achtung: Die Buchsen haben keine Aussparung für das LAN Kabel, könnte eng werden. Die Abbildungen in der Bedienungsanleitung sind Spegelverkert und habenen einige Schreibfehler.



**[------------------------------------------------------------------------------------------------------------------------- Zurück zum Inhalt:](#inhalt)**

### 3. SSH FTP Telnet Zugang

Alle Zugänge sind deaktiviert.

**[------------------------------------------------------------------------------------------------------------------------- Zurück zum Inhalt:](#inhalt)**

### 4. TTL UART
Als erstes löte ich einige Kabel an die UART-Pins auf der Platine und verbinde sie mit einem TTL-zu-USB-Adapter. 
So sollte man die übliche Linux-Ausgabe von einem Router sehen, aber leider kommt da nichts: 
Ich kann U-Boot nicht daran hindern, automatisch zu booten, und ich kann die Befehlszeilenschnittstelle 
nicht aufrufen, sobald die Standard-Firmware gebootet hat.

Der Start mit gedrücktem Reset Knopf soll den TFTP Ladevorgang anstossen, ist nicht genau verifiziert.

**[------------------------------------------------------------------------------------------------------------------------- Zurück zum Inhalt:](#inhalt)**

### 5. Grundkonfiguration & Downgrade auf Version 3.0.24 der Xiaomi Firmware
Bereits die normale Inbetriebnahme kann nur erfolgreich durchgeführt wenn der Router
an einen Internetanschluss mit DHCP verkabelt ist. Es wird ein zweites LAN Kabel benötigt.
An den beiden LAN Schnittstellen hört dieser nach dem Booten auf die IP 192.168.31.1. 

Hier bitte eine Basiskonfiguration durchführen - auch um die Firmware Version zu checken. 
Sollte diese nicht 3.0.24 sein, kann nach der initialen Konfiguration über das Admin 
Interface ein Downgrade vorgenommen werden. Eine passende Firmware findet ihr hier:
https://github.com/ffrgb/stockimages/blob/master/xiaomi-4a-gige/miwifi_r4a_all_03233_3.0.24_INT.bin

Sollte sich die SW Version nicht aktivieren lassen, bitte im OpenWRT Forum nach der Geräte-SW suchen und Prüfen ob es eine Möglichkeit zum flashen für diese Version gibt. Es ist dem Hersteller überlassen, die Gerätefirmware abzusichern, das diese nicht durch freie Software ersetzt werden kann.


**[------------------------------------------------------------------------------------------------------------------------- Zurück zum Inhalt:](#inhalt)**

### 6. Exploit für den Hack unter Linux vorbereiten
Als Windwos Bemutzer habe ich eine Ubuntu VM, ein USB Netzwerkadapter an den Router angeschlossen.
Das Linuxsystem aktualisieren und ein paar Pakete nachinstallieren.
Pakete (gegebenfalls mit sudo apt install nachinstallieren):
~~~
    python3 pip3
    git
    telnet
~~~

Die Aktualisierung könnte so aussehen.
~~~

ffhb@ffhb:~$ sudo apt update && sudo apt upgrade
...
Paketlisten werden gelesen... Fertig
...
Alle Pakete sind aktuell.

ffhb@ffhb:~$ sudo apt install python3-pip git telnet 
...
Paketlisten werden gelesen... Fertig
...
python3-pip ist schon die neueste Version (20.0.2-5ubuntu1.6).
0 aktualisiert, 0 neu installiert, 0 zu entfernen und 0 nicht aktualisiert.
~~~
Noch mal gucken, ob der Router noch da ist:
~~~
ffhb@ffhb:~$ ping 192.168.31.1
PING 192.168.31.1 (192.168.31.1) 56(84) Bytes Daten.
64 Bytes von 192.168.31.1: icmp_seq=1 ttl=64 Zeit=1.38 ms
~~~

Invasion durchführen (hier die Verlinkung auf FF-Dresden)

Auf Linux-PC Console öffnen und folgende Befehle ausführen:
Tools zum 'Öffnen' des Routers für Freifunk-Firmware installieren

~~~
git clone https://github.com/Freifunk-Dresden/OpenWRTInvasion
cd OpenWRTInvasion
pip3 install -r requirements.txt 
~~~

Gerät per Tool öffnen

~~~
python3 remote_command_execution_vulnerability.py
~~~

Router IP eintippen, zuvor gewähltes Passwort Eingeben, default Option 1 wählen und warten bis das Script durchgelaufen ist.

Beispiel:

Router IP address [press enter for using the default 'miwifi.com']: 192.168.31.1
Enter router admin password: test1234
There two options to provide the files needed for invasion:
  1. Use a local TCP file server runing on random port to provide files in local directory `script_tools`.
  2. Download needed files from remote github repository. (choose this option only if github is accessable inside router device.)
Which option do you prefer? (default: 1)

****************
router_ip_address: 192.168.31.1
stok: 7508040b98e1b16255c465cf2f5a947c
file provider: local file server
****************
start uploading config file...
start exec command...
local file server is runing on 0.0.0.0:57765. root='script_tools'

Hinweis: Es müssen folgende beide Zeilen zu sehen sein.

local file server is getting 'busybox-mipsel' for 192.168.31.1.
local file server is getting 'dropbearStaticMipsel.tar.bz2' for 192.168.31.1.

Wenn nicht, ist wahrscheinlich eine lokale Firewall (Ubuntu -> ufw / Fedora -> firewalld etc.) aktiv, die Verbindungen blockiert. Diese muss dann temporär deaktiviert werden (sudo ufw disable / sudo systemctl stop firewalld). 

done! Now you can connect to the router using several options: (user: root, password: root)
* telnet 192.168.31.1
* ssh -oKexAlgorithms=+diffie-hellman-group1-sha1 -c 3des-cbc -o UserKnownHostsFile=/dev/null root@192.168.31.1
* ftp: using a program like cyberduck
ffhb@ffhb:~/OpenWRTInvasion$ 



ffhb@ffhb:~/OpenWRTInvasion$ telnet 192.168.31.1
Trying 192.168.31.1...
Connected to 192.168.31.1.
Escape character is '^]'.

XiaoQiang login: root
Password: 


BusyBox v1.19.4 (2020-08-18 11:07:27 UTC) built-in shell (ash)
Enter 'help' for a list of built-in commands.

 -----------------------------------------------------
       Welcome to XiaoQiang!
 -----------------------------------------------------
  $$$$$$\  $$$$$$$\  $$$$$$$$\      $$\      $$\        $$$$$$\  $$\   $$\
 $$  __$$\ $$  __$$\ $$  _____|     $$ |     $$ |      $$  __$$\ $$ | $$  |
 $$ /  $$ |$$ |  $$ |$$ |           $$ |     $$ |      $$ /  $$ |$$ |$$  /
 $$$$$$$$ |$$$$$$$  |$$$$$\         $$ |     $$ |      $$ |  $$ |$$$$$  /
 $$  __$$ |$$  __$$< $$  __|        $$ |     $$ |      $$ |  $$ |$$  $$<
 $$ |  $$ |$$ |  $$ |$$ |           $$ |     $$ |      $$ |  $$ |$$ |\$$\
 $$ |  $$ |$$ |  $$ |$$$$$$$$\       $$$$$$$$$  |       $$$$$$  |$$ | \$$\
 \__|  \__|\__|  \__|\________|      \_________/        \______/ \__|  \__|


root@XiaoQiang:~# 


curl -4 -k http-link auf mein communityfile

curl -4 -k https://download.freifunk-dresden.de/firmware/.nightly/firmware/ramips.mt7621.generic/openwrt-ramips-mt7621-xiaomi_mi-router-4a-gigabit-initramfs-kernel.bin --output firmware.bin 

mtd -e OS1 -r write firmware.bin OS1

Wenn das funktioniert, ist der Router nach dem Neustart auf dem OpwnWRT Image.
Ich habe mir die Images per FTP ins /tmp Verzeichnis gelegt.




**[------------------------------------------------------------------------------------------------------------------------- Zurück zum Inhalt:](#inhalt)**

### 7. Systemupgrade

Nun gibt es zwei Optionen das Sysupgrade auszuführen.
1. via Webinterface

Die Website auf http://192.168.1.1 aufrufen und in die Firmware Verwaltung wechseln.

Menü: Verwalten > Wartung > Firmware

Nun das Sysupgrade-Image auswählen und "Firmware laden".

2. via SSH

Mit SSH (ssh root@192.168.1.1) anmelden und Systemupgrade durchführen: Vorher auf OpenWRT einloggen, für den User root ein PW festlegen. Also root/root ist ok.

cd /tmp
wget -4 https://download.freifunk-dresden.de/firmware/.nightly/firmware/ramips.mt7621.generic/openwrt-ramips-mt7621-xiaomi_mi-router-4a-gigabit-squashfs-sysupgrade.bin -O sysupgrade.bin
sysupgrade -n sysupgrade.bin

oder per SCP in das /tmp Verzeichnis kopieren.

Dieser Vorgang dauert ca. 10 Minuten, es werden Neustarts durchgeführt.
Danach ist der Router fertig installiert und über die IP 192.168.1.1 erreichbar. (benötigt statische IP Konfiguration, also mein Rechner bekommt 192.168.1.2) 

Hier Links zu weitern Anleitungen: 

[https://wiki.bremen.freifunk.net/Anleitungen/Firmware/Flashen_Xiaomi-mi_router_4a.md ](https://wiki.bremen.freifunk.net/Anleitungen/Firmware/Flashen_Xiaomi-mi_router_4a.md )
[https://regensburg.freifunk.net/news/article/xiaomi-4a-gigabit-edition-support/](https://regensburg.freifunk.net/news/article/xiaomi-4a-gigabit-edition-support/) 
[https://wiki.freifunk-dresden.de/index.php/Router_einrichten_Xiaomi#Xiaomi_MI_Router_4A_Gigabit ](https://wiki.freifunk-dresden.de/index.php/Router_einrichten_Xiaomi#Xiaomi_MI_Router_4A_Gigabit )
[https://openwrt.org/toh/xiaomi/mi_router_4](https://openwrt.org/toh/xiaomi/mi_router_4)




**[------------------------------------------------------------------------------------------------------------------------- Zurück zum Inhalt:](#inhalt)**


**Diese Anleitung ist wie immer ohne Gewähr. Für Anregungen und Tipps immer offen.**

