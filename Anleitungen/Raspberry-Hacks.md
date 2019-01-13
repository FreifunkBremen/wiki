## Hacks (Hex) mit dem Raspberry! 3B+

(13.1.2019 F_H) Die folgenden Spielereien dienen der Unterhaltung und Bildung. Der Artikel beschreibt meine ersten Schritte mit dem kleinen Kumpel, einem Raspberry 3B+. Da es einige Stolpersteine gibt, kann dies evtl. hilfreich sein. Rückschläge machen keinen Spass und können vermieden werden. Bei älteren Modellen können die Einstellungen ggf. anders sein.

Hier sind also nur ein paar Stolpersteine erwähnt, die unserer Aufmerksamkeit bedürfen!

## Inhalt:
[Kaufberatung](#inhalt_kaufberatung)

[Netzteil](#inhalt_netzteil)

[Monitor](#inhalt_monitor)

[Serielle Schnittstelle](#inhalt_serielle-schnittstelle)

[LAN Interface feste IP-Adresse](#inhalt_lan-interface-feste-ip-adresse)

[WLAN Verbindung einrichten](#inhalt_wlan-verbindung-einrichten)

[SSH Login auf dem Raspi](#inhalt_ssh-login-auf-dem-raspi)

[Projekt Taster](#inhalt_projekt-taster)


###Kaufberatung
Soll es nur ein Gerät sein, lohnt sich ein Bundle, damit habe ich alles zusammen für den Betrieb eines Raspberry.

Werden es evtl. mehr Geräte oder es werden ein paar Besonderheiten gewünscht, lohnen sich Einzelteile.

Warum Einzelteile?
Micro-SD: wird mehr Speicher benötigt lohnt eine große Karte.

Netzteil: Das originale Netzteil ist sehr groß und verdeckt benachbarte Steckdosen einer Leiste. Das schmale EU-Netzteil 2,5A 5,1V ist besser.

Netzteil: Anker USB Netzteil, 6A 6*5,0V Kabel mit Flachgeräte-Stecker.

Netzteil: Netzteile < 5,1V Raspi Hack erforderlich (s.u.)

Gehäuse: von Formschön bis Wasserdicht alles möglich.

Gehäuse: evtl. nicht präzise für 3B+ passend, Dremel erfordelich.

Kühlkörper: sind immer gut und es gibt sie in Schick, Kupfer / vergoldet.

Lüfter: Es gibt besonders Geräuscharme Lüfter, Lüfter sind nicht erfordelich.

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
Damit die Änderungen wirksam werden, muss der Netzwerkadapter neu gestartet werden.
~~~
Möglichkeit 1, das Interface ab- und wieder anzuschalten.

    sudo ifconfig wlan0 down
    sudo ifconfig wlan0 up

Möglichkeit 2, den ganzen Netzwerkstack neu starten.

    sudo service networking restart
~~~
Damit ist die Einrichtung abgeschlossen und der Raspberry Pi verbindet sich mit deinem WLAN-Netzwerk.

###SSH Login auf dem Raspi
Funktioniert wie auf dem Freifunkrouter. SSH Server aktivieren über:
~~~
sudo raspi-config
~~~
In den Homeverzeichnissen der angelegten Benutzer das Verzeichnis .ssh erstellen. Dorthin die Datei authorized_keys mit unserem Schlüssel kopieren.

Die Konfigurationen unter /etc/ssh werden nicht angefasst. Deren Funktion ist für den SSH Zugriff nicht genau geklärt, alle Einstellungen sind auskommentiert. (Forschungsarbeit notwendig).

###Projekt Taster
Ein Aus Reboot Taster. Tolle Sache, wenn der Pi hängt, kann mit dem Taster neu gestartet werden. Eleganter als den Netzstecker zu ziehen.



