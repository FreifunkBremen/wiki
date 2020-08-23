## Hacks (3/4B+Hex) mit dem Raspberry!

(13.1.2019 F_H) Die folgenden Spielereien dienen der Unterhaltung und Bildung. Der Artikel beschreibt meine ersten Schritte mit dem kleinen Kumpel, einem Raspberry 3&4B+. Da es einige Stolpersteine gibt, kann dies evtl. hilfreich sein. Rückschläge machen keinen Spass und können vermieden werden. Bei älteren Modellen können die Einstellungen ggf. anders sein.

Hier sind also nur ein paar _Stolpersteine_ erwähnt, die unserer `Aufmerksamkeit` bedürfen!

Eine wichtige Quelle ist: https://www.raspberrypi.org/documentation/

## Inhalt:
- [Kaufberatung](#kaufberatung)
- [Erstinstallation](#erstinstallation)
- [Virenscanner ClamAV installieren](#virenscanner-clamav-installieren)
- [Netzteil](#netzteil)
- [Monitor](#monitor)
- [Serielle Schnittstelle](#serielle-schnittstelle)
- [LAN Interface feste IP-Adresse](#lan-interface-feste-ip-adresse)
- [LAN Interface Fallback](#lan-interface-fallback)
- [WLAN Verbindung einrichten](#wlan-verbindung-einrichten)
- [WLAN Access Point einrichten](#wlan-access-point-einrichten)
- [SSH Login auf dem Raspi](#ssh-login-auf-dem-raspi)
- [SAMBA Verzeichnisfreigabe](#samba-verzeichnisfreigabe)
- [Projekt Taster](#projekt-taster)
- [Projekt Webserver](#projekt-webserver)
- [Projekt Nextcloud](#projekt-nextcloud)
- [Projekt DynDNS](#projekt-dyndns)
- [Projekt Lets Encrypt Zertifikat](#lets-encrypt-zertifikat)
- [Umzug auf neuere Hardware](#umzug-auf-neuere-hardware)

### Kaufberatung
Soll es nur ein Gerät sein, lohnt sich ein Bundle, damit habe ich alles zusammen, was für den Betrieb eines Raspberry benötigt wird. Werden es evtl. mehrere Geräte oder es werden ein paar Besonderheiten gewünscht, lohnen sich Einzelteile.

Warum Einzelteile?
- Micro-SD: wird mehr Speicher benötigt lohnt eine große Karte. Die kleine Karte aus einem Bundle wäre übrig.
- Netzteil: Das originale Netzteil ist sehr groß und verdeckt benachbarte Steckdosen einer Leiste. Das schmale EU-Netzteil 2,5A 5,1V ist besser.
- Netzteil: Anker USB Netzteil, 6A 6*5,0V Kabel mit Flachgeräte-Stecker.
- Netzteil: bei Netzteilen < 5,1V ist ein Raspi Hack erforderlich (s.u.)
- Gehäuse: von Formschön bis Wasserdicht alles möglich.
- Gehäuse: evtl. nicht präzise für 3B+ passend, Dremel erfordelich.
- Kühlkörper: sind immer gut und es gibt sie in Schick, Kupfer / vergoldet.
- Lüfter: Es gibt besonders Geräuscharme Lüfter, Lüfter sind aber nicht erforderlich.
- Kühlkörpergehäuse, aus meiner Sicht, der Burner :-) [(3B+)](https://www.elv.de/joy-it-armor-gehaeuse-block-fuer-raspberry-pi-3-schutz-und-kuehlung-zugleich.html?utm_source=google&utm_medium=cpc&refid=GShopping?Gads_Shopping&gclid=CjwKCAjwqZPrBRBnEiwAmNJsNvANtVXfqRuPLPLzGS2CqQdZXWmnE5eZbqIZUJrgTrRyzrFxdivcWRoC7MEQAvD_BwE) [(4B)](https://www.reichelt.de/gehaeuse-fuer-raspberry-pi-4-alu-schwarz-rpi-case-alu07-p261677.html?&trstct=pos_13)

### [-------------------------------------------------------------------------------------- Zurück zum Inhalt:](#inhalt)

### Erstinstallation
Ich möchte nicht jedesmal einen Monitor und Tastatur anklemmen. Es funktioniert auch alles per serieller Schnittstelle oder über **SSH**.
Ab 2016 sind jedoch beide Zugänge deaktiviert. In diesem Beispiel verwende ich 2018-11-13-raspbian-stretch-full.img oder neuer. Dieses Image wird auf die Mikro-SD geschrieben. Die Mikro-SD wird in einem Dateieditor geöffnet. Dort wird die Datei `config.txt` um den Eintrag `enable_uart=1` ergänzt. Jetzt steht nach dem Booten die serielle Schnittstelle zur Verfüfung. Für den sofortigen SSH Zugang wird eine leere Datei `ssh` (ohne .txt am Ende) angelegt. Nach dem Booten sehen wir auf unserem Heimrouter den angeschlossenen Pi und seine IP-Adresse. Jetzt SSH Zugriff starten. Beispiel pi@192.168.178.101 -p 22 unter Windows mit Putty/Kitty. user:`pi` pw:`raspberry`

Die weiteren Konfigurationen im Terminal mit sudo `raspi-config` vornehmen.
### [-------------------------------------------------------------------------------------- Zurück zum Inhalt:](#inhalt)

### Erstinstallation Hinweise
Image auf Micro-SD Karte schreiben. -> 2 Partitionen /boot & /rootfs & freier Platz je nach SD Größe.
2 Varianten: mit gParted das rootfs vergrößern oder neue Partition anlegen, die später gemounted wird. Beide Varianten haben ihre Vor- und Nachteile. Die bessere Lösung ist die neue Partition einzuhängen. Zum Spielen und Programme installieren ist die Variante 1 besser, da die Partition mit /rootfs im Neuzustand bereits fast voll ist.
Wenn die SD Karte gerade noch im Lesegerät steckt, gleich die Einstellugen für Netzteil, Monitor und serielle Konsole in die `/boot/config.txt` eintragen, leere Datei ssh anlegen (aktiviert den SSH Zugang).

Natürlich können die Grudeinstellungen auch in der Image-Datei vorgenommen werden. Unter Windows evtl. mit dem Tool https://www.winimage.com/ das Image Bearbeiten.
### [-------------------------------------------------------------------------------------- Zurück zum Inhalt:](#inhalt)

#### Virenscanner ClamAV installieren 
Wenn der Raspi mit dem Internet verbunden ist, sollte ein Virenscanner installiert werden.
Weitere Infos unter: https://www.clamav.net/
~~~
sudo apt-get update
sudo apt-get upgrade

sudo apt-get install clamav
sudo freshclam
~~~
Autoupdate einrichten über crontab, hinten anhängen:
~~~
sudo crontab -e
00 00 * * * clamscan -r /
~~~
### [-------------------------------------------------------------------------------------- Zurück zum Inhalt:](#inhalt)

### Netzteil
Wird auf dem Monitor ein roter Blitz rechts oben eingeblendet, so liegt eine Unterspannung vor. Eine schlimme Folge ist, die Taktfrequenz wird runtergesetzt und der Pi ist deutlich langsamer.
Kann das Netzteil nicht genug Strom liefern, bzw. hat weniger als 5,1V so kann die Überwachung auf Unterspannung abgeschaltet werden.
Mit den Editor nano im Terminalfenster die Datei `config.txt` öffnen
~~~
sudo nano /boot/config.txt

avoid_warnings=2
~~~
Achtung: Bei zu geringer Betriebsspannung funktionieren keine externen USB Festplatten. Hier ist ein Raspi Netzteil mit 5,1V zu Verwenden.
Laut Spezifikation benötigt der Raspberry Pi eine Spannung von 4,75 – 5,25 Volt. Meine Empfehlung ist folgendes Netzteil: [(3B+ USB)](https://www.reichelt.de/raspberry-pi-ladegeraet-5-v-2-5-a-micro-usb-schwarz-rasp-nt-25-sw-e-p240934.html?&trstct=pos_5) oder [(4B USB-C)](https://www.reichelt.de/raspberry-pi-netzteil-5-1-v-3-0-a-usb-type-c-eu-stecker-s-rpi-ps-15w-bk-eu-p260010.html?&trstct=pos_3)
### [-------------------------------------------------------------------------------------- Zurück zum Inhalt:](#inhalt)

### Monitor
Viele Monitore funktionieren nicht korrekt am Raspi. Der häufigste Fehler ist der schwarze Rand, also ein kleiners Bild. Viele Monitorprobleme können über die Datei /boot/config.txt korrigiert werden. Probleme mit dem ZERO liegen häufig am Mini-HDMI-Adapter. Es sollen nur wenige funktionieren. Bitte auf den richtigen Adapter achten. https://www.rasppishop.de/Raspberry-Pi-Zero-Hdmi-Adapter-mini-Hdmi-zu-Hdmi
~~~
sudo nano /boot/config.txt

disable_overscan=1
~~~
### [-------------------------------------------------------------------------------------- Zurück zum Inhalt:](#inhalt)

### Serielle Schnittstelle
Die serielle Schnittstelle auf der GPIO Leiste wird mit folgendem Eintrag aktiviert.
~~~
sudo nano /boot/config.txt

enable_uart=1
~~~
Kontrolle, ob der UART aktiv ist. In der Datei cmdline.txt hierzu den Wert dwc_otg.lpm_enable=0 setzen.
~~~
sudo nano /boot/cmdline.txt
~~~

Weitere Informationen zur seriellen Schnittstelle unter: http://www.netzmafia.de/skripten/hardware/RasPi/RasPi_Serial.html

Das serielle Kabel, bzw. USB-2-Serial-Adapter auf den GPIO 14 = Pin 8 TX & GPIO 14 = Pin 10 RX, sowie GND (irgend ein freier GND Pin)

### LAN Interface feste IP-Adresse
Wird der Raspi per Kabel an einen Router angeschlossen macht eine statische IP-Adresse Sinn. Ok, am Router lässt sich auch eine feste Adresse per DHCP zuweisen.
Im Terminalfenster wie folgt vorgehen.
~~~
sudo nano /etc/dhcpcd.conf

# Konfiguration feste IP-Adresse
interface eth0
static ip_address=192.168.178.100/24
static routers=192.168.178.1
static domain_name_servers=192.168.178.1

sudo /etc/init.d/networking restart
~~~

### LAN Interface Fallback
Der Pi bekommt normalerweise eine IP Adresse per DHCP zugewiesen. Es gibt eine Möglichkeit, das LAN-Interface so zu konfigurieren, das der Pi vom Router eine IP per DHCP bekommt und wenn er an einen PC angesteckt wird, eine statische IP hat. Dazu wird in der Datei: `sudo nano /etc/dhcpcd.conf` am Ende die Fallbackeinstellung aktiviert. Die Fallbackadresse muss außerhalb des DHCP Bereiches des Routers liegen.
~~~
sudo nano /etc/dhcpcd.conf

# It is possible to fall back to a static IP if DHCP fails:
# define static profile
profile static_eth0
static ip_address=192.168.1.2/24
static routers=192.168.1.1
static domain_name_servers=192.168.1.1 8.8.8.8
# fallback to static profile on eth0
interface eth0
fallback static_eth0

sudo /etc/init.d/networking restart
~~~

### WLAN Verbindung einrichten
Damit sich der Raspi 3B+ mit einem WLAN verbindet, folgende Einstellungen mit eigenen Daten ändern.
~~~
sudo nano /etc/wpa_supplicant/wpa_supplicant.conf

network={
    ssid="TestNetzwerk"
    psk="Mein1SuperGeheimesWLANPasswort!"
    key_mgmt=WPA-PSK
}
~~~
Damit die Änderungen wirksam werden, muss der Netzwerkadapter neu gestartet werden. Für mehrere Netzwerke, den Abschnitt network={...} mehrfach untereinander schreiben.
~~~
Möglichkeit 1, das Interface ab- und wieder anzuschalten.

    sudo ifconfig wlan0 down
    sudo ifconfig wlan0 up

Möglichkeit 2, den ganzen Netzwerkstack neu starten.

    sudo service networking restart
~~~
Damit ist die Einrichtung abgeschlossen und der Raspberry Pi verbindet sich mit deinem WLAN-Netzwerk.

WLAN Netwerke scannen mit:
~~~
sudo iwlist wlan0 scan
~~~
siehe auch: https://www.raspberrypi.org/documentation/configuration/wireless/wireless-cli.md

### WLAN Access Point einrichten
Den Pi als WLAN Access Point nutzen und über den LAN Anschluß mit einem Router verbinden. Für dieses Scenario gibt es viele Anwendungsfälle, wie z.B. über den PI Medien verwenden (Bilder / Video / Musik) wenn er nicht am Netz hängt.
Dieses Thema wird sehr häufig im Netz diskutiert und es gibt nur wenig brauchbare Lösungen. Eine recht gute ist hier zu finden:
https://github.com/damiencaselli/rpi3-hotspot

http://www.linux-ratgeber.de/den-raspberry-pi-als-wlan-hotspot-einrichten/

Zur Beachtung:
Der Pi 3B+ ist Dualbandfähig, kann als Hotspot nur auf 2,4 oder 5 Ghz funken. Eine Konfiguration für WLAN0 = 2,4Ghz & WLAN1=5Ghz existiert noch nicht.
Die Einstellparameter für 2,4 oder 5 Ghz sich hier zu finden:
https://wiki.gentoo.org/wiki/Hostapd#Access_Point

Damit die oben beschriebene Lösung auf dem 3B+ funktioniert ist eine Änderung in /usr/bin/rpi-access-point notwendig.
Zeile 61:
~~~
  if pgrep wpa_supplicant; then
    log "Stopping wpa_supplicant"
    wpa_pid=$(pgrep wpa_supplicant)  ## liefert beim 3B+ 2 PIDs in wpa_pid zurück
    #kill "$wpa_pid"                 ## diable Line 61
    pkill -x wpa_supplicant          ## beende Gruppe wpa_supplicant
  fi
~~~


#### FILE /etc/hostapd/hostapd.conf 2,4 Ghz
~~~
interface=wlan0       # the interface used by the AP
hw_mode=g             # g simply means 2.4GHz band
channel=10            # the channel to use
ieee80211d=1          # limit the frequencies used to those allowed in the country
country_code=DE       # the country code
ieee80211n=1          # 802.11n support
wmm_enabled=1         # QoS support

ssid=somename         # the name of the AP
auth_algs=1           # 1=wpa, 2=wep, 3=both
wpa=2                 # WPA2 only
wpa_key_mgmt=WPA-PSK  
rsn_pairwise=CCMP
wpa_passphrase=somepassword
~~~
802.11a/n/ac with WPA2-PSK and CCMP. A simple but secure AP for recent hardware:

#### FILE /etc/hostapd/hostapd.conf 5 Ghz
~~~
interface=wlan0       # the interface used by the AP
hw_mode=a             # a simply means 5GHz
channel=0             # the channel to use, 0 means the AP will search for the channel with the least interferences 
ieee80211d=1          # limit the frequencies used to those allowed in the country
country_code=DE       # the country code
ieee80211n=1          # 802.11n support
ieee80211ac=1         # 802.11ac support
wmm_enabled=1         # QoS support

ssid=somename         # the name of the AP
auth_algs=1           # 1=wpa, 2=wep, 3=both
wpa=2                 # WPA2 only
wpa_key_mgmt=WPA-PSK 
rsn_pairwise=CCMP
wpa_passphrase=somepassword
~~~

### SSH Login auf dem Raspi
Funktioniert wie auf dem Freifunkrouter. SSH Server aktivieren über:
~~~
sudo raspi-config
~~~
In den Homeverzeichnissen der angelegten Benutzer das Verzeichnis .ssh erstellen. Dorthin die Datei authorized_keys mit unserem Schlüssel kopieren.

Die Konfigurationen unter /etc/ssh werden nicht angefasst. Deren Funktion ist für den SSH Zugriff nicht genau geklärt, alle Einstellungen sind auskommentiert. (Forschungsarbeit notwendig). So wie es aussieht, sind diese Konfigdateien für ältere Raspbian-Versionen gedacht. Auf der aktuellen Version ist es schon automatisch aktiv.

### SAMBA Verzeichnisfreigabe
Ordner für den Netzwerkzugriff freigeben, geht einfach über Samba. Hinweis: Viedo-Stream geht nicht bei hochauflösenden Videos. Auch über LAN werden nicht genug Daten geliefert.
Installieren:
~~~
sudo apt-get install samba
~~~

Das Paket hat jede Menge Abhängigkeiten, die Installation dauert etwas.

- Konfiguration:
Die gesamte Konfiguration von Samba beziehungsweise dem SMB Dienst funktioniert über dessen Konfigurationsdatei /etc/samba/smb.conf.

Freier Zugriff. Am Ende folgendes erweitern:

~~~
sudo nano /etc/samba/smb.conf
~~~

~~~
[Videos]
path = /home/pi/Videos
writeable = no
public = yes
guest ok = yes
guest only = yes
guest account = nobody
browsable = yes
~~~
Dienst neu starten, fertig: 	`sudo /etc/init.d/samba restart`
Passwort Zugriff. Am Ende folgendes erweitern:
~~~
[Privat]
path = /home/pi/MeineDaten
available = yes
guest ok = no
browsable = yes
writeable = no
valid users = neuerbenutzer
~~~
Wenn es ein Benutzer sein soll, der sich nicht am System anmelden kann, diesen einrichten und deaktivieren. (–disable-login): (Benutzer darf den Samba-Share nutzen aber nicht auf dem Raspi arbeiten. Normalfall)
~~~
sudo adduser --disabled-login neuerbenutzer
sudo smbpasswd -a neuerbenutzer
sudo /etc/init.d/samba restart
~~~

### Projekt Taster
Ein Aus Reboot Taster. Tolle Sache, wenn der Pi hängt, kann mit dem Taster neu gestartet werden. Eleganter als den Netzstecker zu ziehen. Taste unter 3 Sekunden drücken, Pi bootet. Taster über 3 Sekunden drücken, Pi fährt runter. Erneutes Drücken im Aus Zustand, Pi startet.

Originalbeiträge: 
https://gilyes.com/pi-shutdown-button/
https://www.heise.de/ct/hotline/Ein-Ausschalter-fuer-Raspberry-Pi-und-Raspi-Zero-3892620.html
Download ftp://ftp.heise.de/pub/ct/listings/1722-144.zip


Systemd-Job für den Ausschalt-Jumper (GPIO-Pins 5+GND).
Installation: Die Datei pishutdown.py nach /usr/local/bin
und pishutdown.service nach /etc/systemd/system kopieren.
Starten des Service mit:
~~~
sudo systemctl enable pishutdown.service
sudo systemctl start pishutdown.service
~~~
pishutdown.py
~~~
#!/usr/bin/python
# shutdown/reboot(/power on) Raspberry Pi with pushbutton

import RPi.GPIO as GPIO
from subprocess import call
from datetime import datetime
import time

# pushbutton connected to this GPIO pin, using pin 5 also has the benefit of
# waking / powering up Raspberry Pi when button is pressed
shutdownPin = 5

# if button pressed for at least this long then shut down. if less then reboot.
shutdownMinSeconds = 3

# button debounce time in seconds
debounceSeconds = 0.01

GPIO.setmode(GPIO.BOARD)
GPIO.setup(shutdownPin, GPIO.IN, pull_up_down=GPIO.PUD_UP)

buttonPressedTime = None


def buttonStateChanged(pin):
    global buttonPressedTime

    if not (GPIO.input(pin)):
        # button is down
        if buttonPressedTime is None:
            buttonPressedTime = datetime.now()
    else:
        # button is up
        if buttonPressedTime is not None:
            elapsed = (datetime.now() - buttonPressedTime).total_seconds()
            buttonPressedTime = None
            if elapsed >= shutdownMinSeconds:
                # button pressed for more than specified time, shutdown
                call(['shutdown', '-h', 'now'], shell=False)
            elif elapsed >= debounceSeconds:
                # button pressed for a shorter time, reboot
                call(['shutdown', '-r', 'now'], shell=False)


# subscribe to button presses
GPIO.add_event_detect(shutdownPin, GPIO.BOTH, callback=buttonStateChanged)

while True:
    # sleep to reduce unnecessary CPU usage
    time.sleep(5) 
~~~
pishutdown.service
~~~
[Service]
ExecStart=/usr/bin/python /usr/local/bin/pishutdown.py
WorkingDirectory=/usr/local/bin/
Restart=always
StandardOutput=syslog
StandardError=syslog
SyslogIdentifier=pishutdown
User=root
Group=root

[Install]
WantedBy=multi-user.target 
~~~

### Projekt Webserver
Viele tolle Projekte verwenden ein Webinterface und jedes Projekt einen anderen Webserver. Wenn mehrere Webseiten auf dem Pi laufen sollen, kommen wir um Virtualhosts nicht herum. Damit verschiedene Webseiten vernünftig funktionieren, bedarf es einer sauberen Konfiguration. Deshalb ist hier die erste Wahl: Apache2
Wer also mehr als nur eine Webseite auf dem Pi hosten möchte, sollte sich mit dem Apache Webserver beschäftigen.

### Projekt Nextcloud
Eine Nextcloud auf dem Pi zu istallieren ist eine recht einfache Sache. Damit die Nextcloud auch vernünftig funktioniert, bedarf es tiefergehenden Fachwissens. Hier gibt es Abhilfe durch ein vorkonfiguriertes System, in dem bereits alle relevanten Einstellungen vorgenommen wurden.
Meine Empfehlung: nextcloudpi
https://github.com/nextcloud/nextcloudpi
https://ownyourbits.com/nextcloudpi/
Hinweis: Ehrlich, brecht euch nicht die Finger. Verwendet das fertige NectCloudPi. Das ist Frustschonend.

### Projekt DynDNS
Zwei Möglichkeiten für DynDNS als Vorschlag.

DynDNS Domain bei spdyn.de
Registriert euch zuerst bei spdyn.de und fügt über 
euer Profil bei Hosts von Benutzer einen IPv4 Host hinzu.

DynDNS-Funktion der FRITZ!Box nutzen:
Meldet euch unter fritz.box auf eurer FRITZ!Box an und geht auf Internet > Freigaben > DynDNS
Gebt dort folgende Daten ein:

**Update-URL:**
https://update.spdyn.de/nic/update?hostname=<domain>&myip=<ipaddr> 
Domain: Eure Domain bei spdyn
Benutzername: euer Benutzername bei spdyn
Passwort: euer Passwort


Alternativ: spdyn-updater installieren:
Alternativ könnt ihr auch den spdynu verwenden. Der spdynu wurde von canox.net für die Verwendung mit spdyn angepasst und sollte auch mit den alternativen Dynamic-DNS Anbietern funktionieren.
~~~
cd /home/pi/Download
wget https://apt.canox.net/apt.canox.net.gpg.key
sudo apt-key add apt.canox.net.gpg.key
wget https://gitlab.com/CANOXNET/sources-lists/raw/master/ubuntu/canoxnet.list

sudo mv canoxnet.list /etc/apt/sources.list.d/
sudo apt update
sudo apt install spdynu
sudo systemctl enable spdynu.service
sudo systemctl enable spdynu.timer
sudo systemctl start spdynu.service
sudo systemctl start spdynu.timer
~~~

Anschließend müsst ihr mit`sudo nano /etc/spdynu.conf` die Datei /etc/spdynu.conf anpassen. 
~~~
Host (euer bei spdyn erstellter Host)
Username (euer Benutzername bei spdyn)
Passwort (falls ihr über die Webseite einen Token generiert habt müsst ihr diesen statt des Passwortes eintragen. Wenn ihr stattdessen euer Passwort verwendet muss isToken = 1 zu isToken= 0 geändert werden)
Das ganze sollte am Ende wie folgt aussehen:

Domain: Eure Domain bei spdyn
Benutzername: euer Benutzername bei spdyn
Passwort: euer Passwort
~~~
Mit Strg + O, Enter & Strg + X speichert ihr die Datei
Eure IP-Adresse findet ihr in der Datei /tmp/spdynuIP.cnf

cat /tmp/spdynuIP.cnf
zeigt externe IP des Routers. (geht.)

### Lets Encrypt Zertifikat
Let’s Encrypt Zertifikat erstellen:
Damit ihr über HTTPS auf eure Nextcloud usw. des Pi, zugreifen könnt benötigt ihr ein Zertifikat. Dies geht mit dem folgenden Befehl (Hinweis: Ihr müsst domain.spdns.de mit eurer bei spdyn angelegten Domain und die E-Mail Adresse user@domain.tld ersetzen!)
~~~
sudo certbot certonly --webroot -w /var/www/html/ -d domain.spdns.de -m user@domain.tld --agree-tos
~~~
Let’s Encrypt Zertifikat automatisch aktualisieren:
Die von Let’s Encrypt ausgestellten Zertifikate sind nur 3 Monate gültig. Mit einem Cronjob wird wöchentlich ein neues Zertifikat generiert.
~~~
sudo nano /etc/crontab
# Dort vor der abschließenden Raute folgenden Befehl einfügen:

@weekly root certbot renew
~~~
Das geht mit anderen DNS Anbietern ähnlich und lässt sich auch mehrfach einsetzen.

Falls das Zertifikat abgelaufen ist und/oder nicht erneuert wurde, kann dieses durch folgenden Befehl aktualisiert werden.
~~~
cd /etc/letsentcrypt
./certbot-auto
~~~

### Umzug auf neuere Hardware
Buster - die neue Version von Raspbian

Der Rapberry 4 benötigt Buster, Buster ist zu älterer Hardware abwärtskompatibel.

Es gibt keine großen Unterschiede zwischen Debian Stretch und Debian Buster. 
Die meisten Unterschiede sind unter der Haube, überwiegend Sicherheitsänderungen, 
die Buster schwerer zu hacken machen sollen. 

Einfach die SD Karte umstecken funktioniert nicht sauber, es ist auf dem alten System
ein Umstieg auf Buster durchzuführen.

Das zu wechselnde System auf der alten Hardware booten.
Dann editieren wir:
 /etc/apt/sources.list replacing "stretch" by "buster"
 /etc/apt/sources.list.d/raspi.list replacing "stretch" by "buster"
sudo apt update
sudo apt dist-upgrade
reboot, check it works OK.
Remove SD, USB HD etc, Wechsel auf RPi 4
Boot fertig.
NEXTCLOUDPI-Image. Das Nextclougimage wird etwas anders auf Buster angehoben. Das Team von Nextcloud hat den Upgradeprozess automatisiert. Hier wird der hauseigene Upgradebefehl ausgeführt.
~~~
sudo ncp-update
sudo ncp-dist-upgrade
~~~
fertig.