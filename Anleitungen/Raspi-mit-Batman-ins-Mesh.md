# Raspberry Pi mit batman-adv ins Freifunk-Mesh bringen

### Worum es geht

Neulich wollte ich an meinem Freifunk-Router einen [Raspberry Pi](https://www.raspberrypi.org/) anschließen, so daß er im [FFHB-Netz](http://bremen.freifunk.net) hängt. Allerdings hab ich auf dem Router die [Mesh-on-LAN](http://gluon.readthedocs.org/en/latest/features/wired-mesh.html#mesh-on-lan)-Funktion eingeschaltet, weil da noch weitere Freifunk-Router per Kabel angeschlossen sind.

Wenn man Mesh on LAN angeschaltet hat, müssen alle per Kabel an dem Router angeschlossenen Geräte direkt das "[batman-adv](http://www.open-mesh.org/projects/batman-adv/wiki/Doc-overview)"-Protokoll sprechen, um über den Router ins Netz zu kommen. Geräte, die das Protokoll nicht unterstützen, bekommen einfach keine IP zugewiesen.

Raspbian bringt zwar schon Unterstützung für das batman-adv-Protokoll mit, aber leider nur in Version 2015. Bei Freifunk Bremen wird aber die ältere (inkompatible) Version 2013 verwendet, so dass ich das batman-adv-Kernelmodul in der richtigen Version von Hand installieren musste.

Die alte Version von batman-adv setzt allerdings eigentlich einen alten Linux-Kernel voraus; deshalb muss man einige Patches für batman-adv anwenden, damit es auch mit dem Kernel von Raspbian 8 funktioniert.

Diese Anleitung beschreibt, wie ich das batman-adv-Kernelmodul installiert und das batman-adv-Interface eingerichtet habe. Vieles wurde dabei von diesen beiden Seiten abgeschaut:
* http://wiki.freifunk-flensburg.de/wiki/Ein_Gateway_einrichten_auf_Raspbian
* http://viisauksena.de/blog/raspberry-pi-und-freifunk-freiburg-or-batman-adv-mesh-network

### batman-adv-Kernelmodul installieren

Ich gehe von einem frisch installierten Raspbian 8 aus.

Anmerkung ec8or: *Mit dem Raspbian 7 gibt das ein oder andere [Problem](https://github.com/raspberrypi/linux/issues/758), da der Kompiler 4.8 in den Quellen zu buggy ist. Ich hab zunächst ein [update auf Raspbian 8/Jessie](http://linuxconfig.org/raspbian-gnu-linux-upgrade-from-wheezy-to-raspbian-jessie-8) gemacht.*

Vorbereitung:
```
# für "make menuconfig" vom Kernel:
sudo apt-get install libncurses5-dev

# Kernel ist mit GCC 4.8.3 kompiliert (steht in /proc/version), aber Raspbian installiert 4.9;
# also muss GCC 4.8 zusätzlich installiert werden...
sudo apt-get install gcc-4.8 g++-4.8
# ... und dann als Standardcompiler gesetzt werden:
sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-4.9 20
sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-4.8 50
sudo update-alternatives --install /usr/bin/g++ g++ /usr/bin/g++-4.9 20
sudo update-alternatives --install /usr/bin/g++ g++ /usr/bin/g++-4.8 50

# weiß nicht mehr, wofür das genau gebraucht wurde:
apt-get install libnl-3-dev

# Firmware und Kernel aktualisieren:
sudo rpi-update

# Skript installieren, um die Kernel-Quellen runterzuladen:
sudo wget https://raw.githubusercontent.com/notro/rpi-source/master/rpi-source -O /usr/bin/rpi-source && sudo chmod +x /usr/bin/rpi-source

# Kernel-Quellen runterladen und installieren:
rpi-source
```
Bei Problemen mit `rpi-source` hier nachschauen: https://github.com/notro/rpi-source/wiki

Quellen für batman-adv Version 2013.4.0 runterladen:
```
cd ~
git clone http://git.open-mesh.org/batman-adv.git
cd batman-adv
git checkout -b V14 v2013.4.0
```

Jetzt die ganzen Änderungen von https://cccfr.de/wiki/freifunk:debian#batman_advanced anwenden (bis hin zu Kernel 4.1.0). Evtl. kann man alternativ auch die Quellen von https://github.com/freifunk-gluon/batman-adv-legacy nehmen - hab ich nicht ausprobiert.

Dann mit
```
make
sudo make install
```
das Kernelmodul kompilieren und installieren.

Jetzt mit `modinfo batman-adv` nachschauen, ob das Modul jetzt tatsächlich die richtige Version hat (2013.4.0-dirty). Dann mit `modprobe batman-adv` laden, und außerdem `batman-adv` in `/etc/modules` eintragen, damit es beim nächsten Booten automatisch geladen wird.

### Mesh-Verbindung einrichten

Tools für das batman-adv-Interface runterladen:
```
sudo apt-get install batctl bridge-utils
sudo wget -O /etc/network/if-pre-up.d/batadv https://raw.githubusercontent.com/FreifunkBremen/ansible/master/roles/batman-adv-interface/files/if-pre-up && chmod +x /etc/network/if-pre-up.d/batadv
```

Das batman-adv-Interface konfigurieren, indem man `/etc/network/interfaces.d/bat-ffhb` mit diesem Inhalt anlegt:
```
auto bat-ffhb
iface bat-ffhb inet manual
	batadv-ports eth0
	batadv-hw XX:XX:XX:XX:XX:XX
	up ip link set $IFACE up
	down ip link set $IFACE down
auto ffhb-mesh
iface ffhb-mesh inet dhcp
    bridge-ports bat-ffhb
    bridge-maxwait 0
```
(Inhalt basiert auf https://github.com/FreifunkBremen/ansible/blob/master/roles/batman-adv-interface/templates/interfaces)

In dieser Datei dann noch anpassen:
* statt eth0 das Netzwerkinterface angeben, das verwendet werden soll
* statt `XX:XX:XX:XX:XX:XX` die MAC-Adresse-vom-physikalischen-Interface plus zwei angeben (ja, ist etwas kryptisch). Also mit `ifconfig` die MAC-Adresse z.B. von eth0 holen, dann die letzten zwei Stellen nehmen (sind in hexadezimal), 2 dazuzählen, und das ganze dann als Hex-Zahl hinter `batadv-hw` eintragen.

Jetzt das System an den FF-Router anschließen, und mit `/etc/init.d/networking restart` die neuen Interfaces aktivieren (dauert ein bißchen). Wenn alles glatt gelaufen ist, sollte `ifconfig` hinterher die neuen Interfaces `bat-ffhb` und `ffhb-mesh` anzeigen; letzteres sollte automatisch IPv4- und IPv6-Adressen bekommen haben.

Mit `ping 8.8.8.8` und `ping6 2001:4860:4860::8888` kann man dann prüfen, ob man tatsächlich im Internet ist.