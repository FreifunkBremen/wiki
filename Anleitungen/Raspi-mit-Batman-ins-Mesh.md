# Raspberry Pi mit batman-adv ins Freifunk-Mesh bringen

[[_TOC_]]

## Worum es geht

Neulich wollte Oliver an seinem Freifunk-Router einen [Raspberry Pi](https://www.raspberrypi.org/) anschließen, sodass der PI im [FFHB-Netz](http://bremen.freifunk.net) hängt. Allerdings hat er auf dem Router die [Mesh-on-LAN](http://gluon.readthedocs.org/en/latest/features/wired-mesh.html#mesh-on-lan)-Funktion eingeschaltet, weil da noch weitere Freifunk-Router per Kabel angeschlossen sind.

Wenn man Mesh on LAN angeschaltet hat, müssen alle per Kabel an dem Router angeschlossenen Geräte direkt das "[batman-adv](http://www.open-mesh.org/projects/batman-adv/wiki/Doc-overview)"-Protokoll sprechen, um über den Router ins Netz zu kommen. Geräte, die das Protokoll nicht unterstützen, bekommen einfach keine IP zugewiesen.

Raspbian bringt zwar schon Unterstützung für das batman-adv-Protokoll mit, aber leider nur in Version 2015. Bei Freifunk Bremen wird aber die ältere (inkompatible) Version 2013 verwendet, so dass ich das batman-adv-Kernelmodul in der richtigen Version von Hand installieren musste.

Die alte Version von batman-adv setzt allerdings eigentlich einen alten Linux-Kernel voraus; deshalb muss man einige Patches für batman-adv anwenden, damit es auch mit dem Kernel von Raspbian 8 funktioniert.

Diese Anleitung beschreibt, wie ich das batman-adv-Kernelmodul installiert und das batman-adv-Interface eingerichtet habe. Vieles wurde dabei von diesen beiden Seiten abgeschaut:
* http://wiki.freifunk-flensburg.de/wiki/Ein_Gateway_einrichten_auf_Raspbian
* http://viisauksena.de/blog/raspberry-pi-und-freifunk-freiburg-or-batman-adv-mesh-network

## Batman Installation und Konfiguration

Die folgende Anleitung geht von einem frisch installierten Raspbian 8 aus.

Mit dem Raspbian 7 gibt das ein oder andere [Problem](https://github.com/raspberrypi/linux/issues/758), da der Kompiler 4.8 in den Quellen zu buggy ist. Es ist scheinbar erforderlich zunächst ein [update auf Raspbian 8/Jessie](http://linuxconfig.org/raspbian-gnu-linux-upgrade-from-wheezy-to-raspbian-jessie-8) zu machen.

### Vorbereitungen

Zunächst müssen ein paar Abhängigkeiten erfüllt werden. Bei Problemen mit `rpi-source` [hier](https://github.com/notro/rpi-source/wiki) nachschauen.
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

# Firmware und Kernel aktualisieren
sudo rpi-update

# Skript installieren, um die Kernel-Quellen runterzuladen:
sudo wget https://raw.githubusercontent.com/notro/rpi-source/master/rpi-source -O /usr/bin/rpi-source && sudo chmod +x /usr/bin/rpi-source

# Kernel-Quellen runterladen und installieren:
rpi-source
```

### Quellen besorgen

Um den an den Code für das Kernelmodul in Version 2013.4.0 zukommen gibt es zwei Wege.

**Batman Legacy Projekt**

Das Repository [batman-adv-legacy](https://github.com/freifunk-gluon/batman-adv-legacy) klonen.
```
cd ~
git clone https://github.com/freifunk-gluon/batman-adv-legacy.git
cd batman-adv-legacy
```

**ODER**

**Branch aus git.open-mesh.org**

Repository klonen, den Branch 2013.4.0 auschecken und Anschließend alle Änderungen bis hin zu Kernel 4.1.0 aus dem Artikel [Batman Advanced Anwenden](https://cccfr.de/wiki/freifunk:debian#batman_advanced anwenden) vom ccrf anwenden. 
```
cd ~
git clone http://git.open-mesh.org/batman-adv.git
cd batman-adv
git checkout -b V14 v2013.4.0
```

### Kompilieren und installieren

Nun können wir das Modul kompilieren:
```
make
sudo make install
```

Jetzt mit `modinfo batman-adv` nachschauen, ob das Modul jetzt tatsächlich die richtige Version hat (2013.4.0-21-ga854277-dirty, bzw. 2013.4.0-dirty). Dann mit `modprobe batman-adv` laden, und außerdem `batman-adv` in `/etc/modules` eintragen, damit es beim nächsten Booten automatisch geladen wird.

## Mesh-Verbindung einrichten

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

## Sonstiges

### Statische IPv6 umziehen
Wenn du dein PI/Server zuvor per statischer IPv6-Adresse erreichbar gemacht hast, funktioniert das nun nicht mehr. Diese Adresse muss du nun `ffhb-mesh` zuweisen. Dazu fügst du folgenden Block an die `/etc/network/interfaces.d/bat-ffhb` an. Ersetzte XX mit deinem Wert.

Bestehender Eintrag in `/etc/network/interfaces`:

```
iface eth0 inet6 static
  address 2a06:8782:ffbb:1337::XX
  netmask 64
```

Neuer Eintrag am Ende der `/etc/network/interfaces.d/bat-ffhb`:

```
iface ffhb-mesh inet6 static
  address 2a06:8782:ffbb:1337::XX
  netmask 64
```
