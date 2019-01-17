## Hacks (3B+Hex) mit dem Raspberry! 3B+

(13.1.2019 F_H) Die folgenden Spielereien dienen der Unterhaltung und Bildung. Der Artikel beschreibt meine ersten Schritte mit dem kleinen Kumpel, einem Raspberry 3B+. Da es einige Stolpersteine gibt, kann dies evtl. hilfreich sein. Rückschläge machen keinen Spass und können vermieden werden. Bei älteren Modellen können die Einstellungen ggf. anders sein.

Hier sind also nur ein paar Stolpersteine erwähnt, die unserer Aufmerksamkeit bedürfen!

Eine wichtige Quelle ist: https://www.raspberrypi.org/documentation/

## Inhalt:
[Kaufberatung](#inhalt_kaufberatung)

[Netzteil](#inhalt_netzteil)

[Monitor](#inhalt_monitor)

[Serielle Schnittstelle](#inhalt_serielle-schnittstelle)

[LAN Interface feste IP-Adresse](#inhalt_lan-interface-feste-ip-adresse)

[LAN Interface Fallback](#inhalt_lan-interface-fallback)

[WLAN Verbindung einrichten](#inhalt_wlan-verbindung-einrichten)

[WLAN Access Point einrichten](#inhalt_wlan-access-point-einrichten)

[SSH Login auf dem Raspi](#inhalt_ssh-login-auf-dem-raspi)

[Projekt Taster](#inhalt_projekt-taster)

[Projekt Webserver](#inhalt_projekt-webserver)

[Projekt Nextcloud](#inhalt_projekt-nextcloud)

[Projekt DynDNS](#inhalt_projekt-dyndns)

[Projekt Lets Encrypt Zertifikat](#inhalt_lets-encrypt-zertifikat)


###Kaufberatung
Soll es nur ein Gerät sein, lohnt sich ein Bundle, damit habe ich alles zusammen, was für den Betrieb eines Raspberry benötigt wird.

Werden es evtl. mehrere Geräte oder es werden ein paar Besonderheiten gewünscht, lohnen sich Einzelteile.

Warum Einzelteile?
Micro-SD: wird mehr Speicher benötigt lohnt eine große Karte. Die kleine Karte aus einem Bundle wäre übrig.

Netzteil: Das originale Netzteil ist sehr groß und verdeckt benachbarte Steckdosen einer Leiste. Das schmale EU-Netzteil 2,5A 5,1V ist besser.

Netzteil: Anker USB Netzteil, 6A 6*5,0V Kabel mit Flachgeräte-Stecker.

Netzteil: Netzteile < 5,1V Raspi Hack erforderlich (s.u.)

Gehäuse: von Formschön bis Wasserdicht alles möglich.

Gehäuse: evtl. nicht präzise für 3B+ passend, Dremel erfordelich.

Kühlkörper: sind immer gut und es gibt sie in Schick, Kupfer / vergoldet.

Lüfter: Es gibt besonders Geräuscharme Lüfter, Lüfter sind aber nicht erfordelich.

###Netzteil
Wird auf dem Monitor ein roter Blitz rechts oben eingeblendet, so liegt eine Unterspannung vor. Eine schlimme Folge ist, die Taktfrequenz wird runtergesetzt und der Pi ist deutlich langsamer.

Kann das Netzteil genug Strom liefern, so kann die Überwachung auf Unterspannung abgeschaltet werden.

Mit den Editor nano im Terminalfenster die Datei config.txt öffnen
~~~
sudo nano /boot/config.txt

avoid_warnings=2
~~~
###Monitor
Viele Monitore funktionieren nicht korrekt am Raspi. Der häufigste Fehler ist der schwarze Rand, also ein kleiners Bild. Viele Monitorprobleme können über die Datei /boot/config.txt korrigiert werden.
~~~
sudo nano /boot/config.txt

disable_overscan=1
~~~
###Serielle Schnittstelle
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

###LAN Interface feste IP-Adresse
Wird der Raspi per Kabel an einen Router angeschlossen macht eine statische IP-Adresse Sinn.
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

###LAN Interface Fallback
Der Pi bekommt normalerweise eine IP Adresse per DHCP zugewiesen. Es gibt eine Möglichkeit, das LAN-Interface so zu konfigurieren, das der Pi vom Router eine IP per DHCP bekommt und wenn er an einen PC angesteckt wird, eine statische IP hat. Dazu wird in der Datei: /etc/dhcpcd.conf am Ende die Fallbackeinstellung aktiviert. Die Fallbackadresse muss außerhalb des DHCP Bereiches des Routers liegen.
~~~
# It is possible to fall back to a static IP if DHCP fails:
# define static profile
profile static_eth0
static ip_address=192.168.1.2/24
static routers=192.168.1.1
static domain_name_servers=192.168.1.1 8.8.8.8
# fallback to static profile on eth0
interface eth0
fallback static_eth0
~~~

###WLAN Verbindung einrichten
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

###WLAN Access Point einrichten
Den Pi als WLAN Access Point nutzen und über den LAN Anschluß mit einem Router verbinden. Für dieses Scenario gibt es viele Anwendungsfälle, wie z.B. über den PI Medien verwenden (Bilder / Video / Musik) wenn er nicht am Netz hängt.
Dieses Thema wird sehr häufig im Netz diskutiert und es gibt nur wenig brauchbare Lösungen. Eine recht gute ist hier zu finden:
https://github.com/damiencaselli/rpi3-hotspot

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

###SSH Login auf dem Raspi
Funktioniert wie auf dem Freifunkrouter. SSH Server aktivieren über:
~~~
sudo raspi-config
~~~
In den Homeverzeichnissen der angelegten Benutzer das Verzeichnis .ssh erstellen. Dorthin die Datei authorized_keys mit unserem Schlüssel kopieren.

Die Konfigurationen unter /etc/ssh werden nicht angefasst. Deren Funktion ist für den SSH Zugriff nicht genau geklärt, alle Einstellungen sind auskommentiert. (Forschungsarbeit notwendig). So wie es aussieht, sind diese Konfigdateien für ältere Raspbian-Versionen gedacht. Auf der aktuellen Version ist es schon automatisch aktiv.

###Projekt Taster
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

###Projekt Webserver
Viele tolle Projekte verwenden ein Webinterface und jedes Projekt einen anderen Webserver. Wenn mehrere Webseiten auf dem Pi laufen sollen, kommen wir um Virtualhosts nicht herum. Damit verschiedene Webseiten vernünftig funktionieren, bedarf es einer sauberen Konfiguration. Deshalb ist hier die erste Wahl: Apache2
Wer also mehr als nur eine Webseite auf dem Pi hosten möchte, sollte sich mit dem Apache Webserver beschäftigen.

###Projekt Nextcloud
Eine Nextcloud auf dem Pi zu istallieren ist eine recht einfache Sache. Damit die Nextcloud auch vernünftig funktioniert, bedarf es tiefergehenden Fachwissens. Hier gibt es Abhilfe durch ein vorkonfiguriertes System, in dem bereits alle relevanten Einstellungen vorgenommen wurden.
Meine Empfehlung: nextcloudpi
https://github.com/nextcloud/nextcloudpi
https://ownyourbits.com/nextcloudpi/

###Projekt DynDNS
Zwei Möglichkeiten für DynDNS als Vorschlag.

DynDNS Domain bei spdyn.de
Registriert euch zuerst bei spdyn.de und fügt über 
euer Profil bei Hosts von Benutzer einen IPv4 Host hinzu.

DynDNS-Funktion der FRITZ!Box nutzen:
Meldet euch unter fritz.box auf eurer FRITZ!Box an und geht auf Internet > Freigaben > DynDNS
Gebt dort folgende Daten ein:

Update-URL: 
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

Anschließend müsst ihr mit sudo nano /etc/spdynu.conf die Datei /etc/spdynu.conf anpassen. 
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

###Lets Encrypt Zertifikat
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


