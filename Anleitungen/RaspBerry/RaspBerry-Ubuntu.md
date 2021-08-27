## Ubuntu auf eine RspBerry installieren

(27.8.2021 F_H) Die folgenden Spielereien dienen der Unterhaltung und Bildung. 
Der Artikel beschreibt einen Versuch, Ubuntu auf einem Raspberry zu Installieren.
Und **Achtung**. Es ist ein **Fehlschlag**.

## Inhalt
[[_TOC_]]


Hier sind also nur ein paar **_Stolpersteine_** erwähnt, die unserer `Aufmerksamkeit` bedürfen! Es kann verallgemeinert gesagt werden: Ubuntu und Raspberry kann funktionieren, ist jedoch relativ schlecht dokumentiert. Für normale Installationen gibt es ein Prima Wiki und entsprechende Foren, für den Raspberry ist es das auf Debian basierte Raspbian.
Die Probleme meiner Ubuntu Installation konnten für den Raspbian nicht gelöst oder genauer beschrieben werden.
Am Ende kommt keine funtionierende Installation raus


### Vorbereitung

Damit ein neues Projekt funktioniert, wird dieses auf lauffähiger Hardware aufgesetzt. Die Hardware besteht hier aus einem lauffähigen RaspBerry 3B+ mit seriellem USB Port als Konsole. Geprüft und angeschlossen wurden ein Fernseher mit HDMI Anschluss, USB Tastatur und USB Maus. Netzteil, diverse Kabel, und Flashcards.


**[------------------------------------------------------------------------------------------------------------------------- Zurück zum Inhalt:](#inhalt)**


### Pi Imager

Die weiteren Konfigurationen im Terminal mit sudo `raspi-config` vornehmen.

**[------------------------------------------------------------------------------------------------------------------------- Zurück zum Inhalt:](#inhalt)**

Installtion von Ubuntu Server LTS auf dem Raspi.

Zuerst einen benötigen wir einen lauffähigen Raspi mit Monitor und Tastatur, Maus optional.
Wenn wir hier ein neues Gerät verwenden, dieses bitte erst zum laufen bringen, egal mit was.

Für die Installation von Ubuntu gibt es eine schöne Anleitung,
die alles sehr einfach beschreibt.
Leider fehlt es Problembeschreibungen und deren Lösungen und es gibt Probleme.

SD-Karte bespielen:
Anstatt Winimage etc. habe ich die SD Karte mit dem Raspi-Imager bespielt.
Das Programm ist für Superfaule und funktioniert prima.
Das Programm kennt alle Images, und läd das Ausgwählte frisch aus dem Netz.
Ohne Netzanbindung kann auch ein vorhandenes Image ausgewählt weden.

Habe das Empfohlene 32 Bit Image verwendet. Leider kann ich mich nicht einlaggen.
Die User/PW Kombination ubuntu/ubuntu wird verweigert. Das 64Bit Image hat hingegen funktioniert. 

Nach erfolgreichem Schreiben, ist die SD Karte unter Windows nicht zu sehen.
Ziehen uns Stecken hilft, dadurch kann auf den FAT Anteil Bootpartition zugegriffen werden.
Hier sollen nach Anleitung einige Grundeinstellungen vorgenommen werden.
LAN, Wifi, Konsole, SSH.
Hat alles nicht funktioniert. Kein Netz, keine serielle Konsole.
Habe an den PI dann Tastatur und Monitor angeschlosen.

Also die Headless Installation über WiFi oder LAN mit SSH Zugriff klappt nicht.
Die IP Afrage im Netz über arp klappt nicht.
Zitat
Determining the Pi’s IP address
To determine the IP address of your board, open a terminal and run the arp command:
On Ubuntu and Mac OS:
~~~
arp -na | grep -i "b8:27:eb"
~~~
If this doesn’t work and you are using the latest Raspberry Pi 4, instead run:
~~~
arp -na | grep -i "dc:a6:32"
~~~
    Information
    Depending on your version of Ubuntu, you may need to install the net-tools package. Install it with sudo apt install net-tools and try the arp command again.

On Windows:
~~~
arp -a | findstr b8-27-eb
~~~
If this doesn’t work and you are using the latest Raspberry Pi 4, instead run:

~~~
arp -a | findstr dc-a6-32
~~~

Es werden IP Adressen von vorhandenen PI´s wiedergegeben, aber nicht von diesem hier.
Dieser PI ist ziemlich taub, kein WiFi aber LAN ist up

Kurz einen Schritt zurück.


**[------------------------------------------------------------------------------------------------------------------------- Zurück zum Inhalt:](#inhalt)**

### Boot Ubuntu Server
SD Karte mit 64Bit Image in den PI, Fernseher und Tastatur drann und Strom drauf.
Der Pi macht den bunten Farbbildschirm und bootet. Der Bootvorgang endet mit dem Login.
Erster login: ubuntu ubuntu und dann PW ändern.
Als root darf ich später auch wieder ein triviales PW setzen, falls ich wieder einfaches PW möchte.
der User root hat kein PW, der Wechsel erfolgt über "sudo su" und fertig.

Auf der Konsole die IP Adresse abgefragt, ok geht nicht.
Ein Ping 8.8.8.8 sagt, Netz vorhanden, damit sind wir glücklich un können weitermachen.

~~~
sudo apt install net-tools
sudo apt install wireless-tools
~~~

Prima, jetzt können wir die ip Abfragen
arp -a und unser Gateway wird angezeigt
ifconfig und eth0 mit IP Adresse etc.

Ich mach vieles über Windows, jetzt wird mir auf Windows mit arp -a auch der neue Ubuntu Pi angezeigt.
mit putty/kitty etc. kann ich jetzt per SSH zugreifen und benötige den angeschlossenen Fernseher nicht mehr,
lasseihn aber noch bis zum Abschluss drann.

Wenn das neue Passwort erstellt wurde, überprüft man zunächst alle verfügbaren Updates mit dem folgenden Befehl:

~~~
sudo apt update && sudo apt upgrade -y
~~~

Sind alle Updates installiert, sollte der Pi neu gestartet werden:

~~~
sudo reboot
~~~


**[------------------------------------------------------------------------------------------------------------------------- Zurück zum Inhalt:](#inhalt)**

### Systemsprache ändern

Die Standardsprache von Ubuntu ist Englisch. Man kann die gesamte System- 
oder auch nur die Tastatursprache bei Bedarf ändern. 
Dafür müssen zunächst Sprachpakete durch folgenden Befehl installiert werden:

~~~
sudo apt install language-pack-de language-pack-de-base
~~~


**[------------------------------------------------------------------------------------------------------------------------- Zurück zum Inhalt:](#inhalt)**

### Zum Umstellen der Sprache:

~~~
sudo dpkg-reconfigure locales
~~~

Dadurch öffnet sich eine Liste aller verfügbaren Sprachen; 
für Deutsch wählt man mit der Sternchentaste/Leertaste daraus „de_DE.UTF-8 UTF-8“ aus 
und bestätigt mit TAB & „OK“. Danach fragt das System, welche Einstellung die Standardeinstellung werden soll; 
auch hier wählt man wieder „de_DE.UTF-8 UTF-8“. Um die neue Spracheinstellung zu aktivieren, 
muss das System neu gestartet werden.


**[------------------------------------------------------------------------------------------------------------------------- Zurück zum Inhalt:](#inhalt)**

### Tastatur ändern

Wer nur die Tastaturbelegung ändern möchte, kann dies mittels folgendem Befehl tun:
~~~
sudo dpkg-reconfigure keyboard-configuration
~~~
Auch hier muss das System nach den Änderungen neu gestartet werden.


**[------------------------------------------------------------------------------------------------------------------------- Zurück zum Inhalt:](#inhalt)**

### Zeitzone ändern

Um das Betriebssystem noch mehr zu lokalisieren, kann man auch die Zeitzone von UTC auf CET umstellen:
~~~
sudo timedatectl set-timezone Europe/Berlin
~~~


**[------------------------------------------------------------------------------------------------------------------------- Zurück zum Inhalt:](#inhalt)**

### Mit SSH auf Raspberry Pi und Ubuntu zugreifen

Der SSH-Server ist standardmäßig installiert und aktiviert. 
Wer die IP-Adresse seines Pis nicht kennt, kann sie über folgenden Befehl herausfinden:
~~~
ip a
~~~

Falls nicht, auf dem PI LAN starten. Das System sollte nach mehreren Neustarts sich sicher mit dem Netz verbinden.

~~~
sudo dhclient eth0
~~~

Man findet die IP-Adresse auch im Router oder DHCP-Server. oder mit arp -a.
Jetzt kann über SSH auf den Raspberry Pi zugegriffen werden.

Sobald das funktioniert, bitte den SSH Key in authorizedkeys hinterlegen und den PW Zugang deaktivieren.

**[------------------------------------------------------------------------------------------------------------------------- Zurück zum Inhalt:](#inhalt)**

### Benutzeroberfläche für Raspberry Pi: Ubuntu nachinstallieren

Wer mit Bildschirm, Maus und Tastatur am Pi arbeiten möchte, braucht eine Desktop-Umgebung. 
Wir für Serverbetrieb normalerweise nicht benötigt. Es stehen verschiedene Benutzeroberflächen zur Auswahl, 
die sich schnell und unkompliziert installieren lassen.

Ubuntus Standard-Desktop ist Gnome Shell. Dieser ist den meisten Usern bekannt und einfach zu bedienen, 
verbraucht allerdings auch einen großen Teil der Systemressourcen. Deshalb ist er für einen Raspberry Pi 
eher ungeeignet. Weitere Optionen sind unter anderem:

    Xubuntu (Xfce)
    Lubuntu (LXDE)
    Kubuntu (KDE)

Die Desktop-Umgebungen werden mit folgenden Code installiert:
~~~
sudo apt install xubuntu-desktop
sudo apt install lubuntu-desktop
sudo apt install kubuntu-desktop
~~~
Gegen Ende der Installation wird abgefragt, welcher Displaymanager konfiguriert werden soll. 
Wenn man sich zuvor für Lubuntu als Desktop entschieden hat, ist der Displaymanager LXDE zu empfehlen, 
bei Xubuntu Xfce und bei Kubuntu KDE. 
Der Displaymanager von Gnome gdm3 wird allerdings in jedem Fall mitinstalliert, 
egal welche Desktopumgebung man zuvor gewählt hat. 
Gnome macht den Pi aber so langsam, dass damit ein Arbeiten kaum möglich ist.

Deshalb sollte man nach einem Neustart in der Benutzeranmeldung das ressourcenschonende 
LXDE oder Xfce auswählen. Dafür klickt man einfach unten rechts auf das Zahnradsymbol 
und wählt seinen Desktop aus. Also doch besser keinen Desktop installieren.

**[------------------------------------------------------------------------------------------------------------------------- Zurück zum Inhalt:](#inhalt)**

### USB Tastatur funktioniert nicht
Der erste Start von der Speicherkarte führt nicht zu einem laufenden System. 
Auf Raspberry Pi mit 4 GByte Arbeitsspeicher bleibt das System hängen. 
Erst nach dem Ziehen und Wiederanstecken der Stromversorgung bootet Ubuntu dann in die Kommandozeile durch, 
diesmal ohne Fehler – zumindest auf den ersten Blick.
Versucht man nämlich, etwas auf der Kommandozeile einzugeben, passiert rein gar nichts. 
Die angeschlossene USB-Tastatur bleibt tot. Der Grund liegt in einem bekanntem Bug: 
Ein Fehler im Kernel blockiert bei Systemen mit mehr als 3072 MByte Arbeitsspeicher das Erkennen von USB-Geräten. 
Die Ausgabe von Lsusb etwa listet lediglich den USB-Hub auf, nicht aber die angeschlossenen USB-Geräte. 
Bis Canonical den Fehler behebt, bleibt als Workaround nur übrig, den vom System genutzten Arbeitsspeicher zu beschränken.
Dazu fügen Sie die Zeile total_mem=3072 ans Ende der Konfigurationsdatei /boot/firmware/usercfg.txt an und booten das System neu. 
Bei der Speicherbegrenzung hin und wieder prüfen, ob deer Bug bereits gelöst ist und dann hier entfernt werden kann.

**[------------------------------------------------------------------------------------------------------------------------- Zurück zum Inhalt:](#inhalt)**
