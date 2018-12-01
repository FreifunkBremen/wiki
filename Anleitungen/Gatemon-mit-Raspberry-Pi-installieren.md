=== English version below ===  (Work in Progress 30.11.18)

# Gatemon mit Raspberry Pi installieren

Diese Artikel beschreibt, wie man auf einem [Raspberry Pi](https://www.raspberrypi.org/) die Bremer [Gatemon-Software](https://github.com/FreifunkBremen/gatemon) installiert. Mit so einem Gerät hilft man, die Bremer Freifunk-VPN-Server ständig auf Probleme zu überprüfen. Die Ergebnisse aller Gatemons sind unter [status.ffhb.de](https://status.ffhb.de/) verfügbar.

Fragen zu diesem Artikel könnt ihr im Chat oder auf der Mailing-Liste stellen, wie unter https://ffhb.de/kontakt.html beschrieben. Ich freu mich über Verbesserungen und Korrekturen!

## Hardware-Voraussetzungen
Grundlage für diese Anleitung ist ein Raspberry Pi Model 1B oder besser. Das Gerät wird am Schluss per LAN-Kabel an einen Freifunk-Router angeschlossen und kann dann (ohne Tastatur, Maus oder Monitor) still seinen Dienst verrichten.

Zur Einrichtung braucht man:
- einen Monitor/Fernseher mit HDMI-Eingang
- USB-Keyboard
- einen weiteren Rechner:
	- an dem man (Micro-)SD-Karten beschreiben kann
	- der ins Internet kommt
	- der einen SSH-Client hat (unter Windows z.B. Putty)
	- der IPv6 unterstützt
- grundlegende Kenntnisse eines Raspis (wie benutzt man die Anschlüsse, wie benutzt man die SD-Karte)
- grundlegende Kenntnisse der Linux-Kommandozeile

## Raspian installieren
Unter https://www.raspberrypi.org/downloads/raspbian/ lädt man sich eines der angebotenen Images runter.
Ich gehe in dieser Anleitung davon aus, dass das "Lite"-Image verwendet wird. Wenn man später gerne eine grafische Oberfläche auf dem Raspi haben möchte, kann man auch eines der anderen Images nehmen. Dann braucht man während der Installation zusätzlich eine USB-Maus.

Das Image schreibt man auf die SD-Karte, wie in der [Anleitung](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) beschrieben.

Dann schliesst man an den Raspi die Tastatur, Monitor und Strom an und wartet, bis der Bootvorgang abgeschlossen ist und der Login-Prompt erscheint. Dort meldet man sich als Benutzer "pi" mit Passwort "raspberry" an (Achtung: standardmäßig ist ein US-Tastatur-Layout eingestellt, so dass bei einer deutschen Tastatur "y" und "z" vertauscht sind).

Erstmal ändert man das Tastatur-Layout: `sudo raspi-config` ausführen, dann unter "4. Localisation Options" die Sprache, Zeitzone und das Tastatur-Layout anpassen.

Als nächstes ändert man das Standard-Passwort. Dazu erzeugt man ein neues zufälliges Passwort nach einer dieser Methoden:
* auf einem anderen Rechner `pwgen 12 1` ausführen
* auf dem Raspi `head /dev/urandom | tr -dc A-Za-z0-9 | head -c12` ausführen
Das neue Passwort schreibt man sich auf einen Zettel auf oder besser: legt es im Passwort-Manager ab.
Dann auf dem Raspi "passwd" ausführen und das alte Passwort (raspberry) und das neue eingeben.

Dann aktiviert man den SSH-Server: `sudo raspi-config` ausführen, unter "5. Interfacing" -> "P2 SSH" mit "Yes" bestätigen.

Schließlich legt man mittels `nano /etc/network/interfaces.d/eth0` eine neue Datei an, mit folgendem Inhalt:

```
auto eth0
iface eth0 inet auto
iface eth0 inet6 auto
```

## Raspi ins Freifunk-Netz hängen
Idealerweise wird der Raspi per Kabel mit einem Freifunk-Router verbunden. Man kann ihn aber wohl auch per WLAN verbinden (hab ich aber nicht ausprobiert und ist nicht Thema dieser Anleitung).

Dazu benötigt man einen Freifunk-Router, der noch einen freien LAN-Port hat und bei dem Mesh-on-LAN _ausgeschaltet_ ist.

Der Raspi wird jetzt an diesen LAN-Port angeschlossen und neugestartet (mittels `sudo reboot`). Nach dem Neustart meldet man sich wieder an und schaut dann mit `ip a | grep 2a06`, welche nutzbare IPv6-Adresse das Gerät bekommen hat. Beispielausgabe:

```
    inet6 2a06:8782:ffbb:1337:ba27:ebff:fea1:1d97/64 scope global mngtmpaddr dynamic
```
Der Teil zwischen "inet6" und dem Schrägstrich ist die öffentliche IPv6-Adresse. Unter dieser Adresse meldet man sich jetzt per SSH an (Benutzer "pi").

## Gatemon installieren
Die Gatemon-Software benötigt ein sogenanntes API-Token, um Daten zu https://status.ffhb.de/ hochzuladen. Dieses Token bekommt man z.B. im IRC-Chat, oder per Mail-Anfrage an liste@bremen.freifunk.net oder bei einem Freifunk-Treffen: einfach fragen "ich bin der XYZ und hätte gerne ein API-Token für status.ffhb.de".
Das Token ist einfach eine lange Zeichenfolge (wie ein langes Passwort). Man sollte ein Token immer nur auf einem einzigen Gatemon verwenden.

Außerdem braucht der Raspi für die Gatemon-Software eine statische IPv4-Adresse (weil der DHCP-Port für die Tests benötigt wird und man somit keinen DHCP-Client laufen lassen kann). Dazu sucht man sich unter https://wiki.ffhb.de/Dienste/Home#ipv4-adressen eine unbenutzte Adresse und trägt diese auf der Wiki-Seite ein (zusammen mit einem IRC-Nick oder anderen Kontaktdaten).

Die gewählte IP (z.B. "10.196.0.250") benutzt man, indem man in `/etc/network/interfaces.d/eth0` folgenden Inhalt einträgt (statt des bisherigen Inhalts):

```
auto eth0
iface eth0 inet static
    address 10.196.0.250
    netmask 255.255.0.0
    gateway 10.196.0.1
    dns-nameservers 10.196.0.1 10.196.0.2 10.196.0.3 10.196.0.5 10.196.0.6

iface eth0 inet6 auto
```

Bei "address" trägt man halt seine eigene gewählte IP-Adresse ein.   Nach einem Reboot sollte `ip a | grep "inet "` die neue Adresse zeigen.

Als nächstes installiert man die nötige Zusatzsoftware, mittels:
```
sudo apt-get install monitoring-plugins-basic monitoring-plugins-standard nagios-plugins-contrib ndisc6 dnsutils git make gcc curl
```
(nicht wundern: dieser Befehl installiert ca. 80 neue Pakete).

Dann installiert man die Gatemon-Software, wie unter https://github.com/FreifunkBremen/gatemon#installation beschrieben:
```
git clone https://github.com/FreifunkBremen/gatemon
cd gatemon
make check_dhcp
sudo mkdir /usr/lib/gatemon
sudo cp check-all-vpn-exits.sh check_dhcp /usr/lib/gatemon/
sudo cp check-all-vpn-exits.cfg /etc/
sudo cp check-all-vpn-exits.cron /etc/cron.d/
```

Weiterhin bearbeitet man die `/etc/check-all-vpn-exits.cfg` und ändert die Angaben für folgende Parameter:
* API_TOKEN: das API-Token, das man vorher angefordert hatte
* MESHMON_NAME: ein kurzer Name des Gatemons (nicht mehr als 20 Zeichen bitte), der dann auf status.ffhb.de erscheinen wird
* MESHMON_PROVIDER: kurzer Beschreibung des verwendeten Internet-Provider; der Text erscheint auf status.ffhb.de im Tooltip und kann helfen, Probleme auf einzelne Provider einzugrenzen
* NETWORK_DEVICE: eth0 (also der Name des Netzwerk-Interface, mit dem der Raspi ins Netz geht)

Jetzt wartet man bis zu 15 Minuten; danach sollte auf https://status.ffhb.de/ der eigene Gatemon neu auftauchen. Die Gatemon-Tests werden nun automatisch alle 10 Minuten durchgeführt.

Wenn das alles soweit funktioniert, kann man Tastatur und Monitor abstöpseln und den Raspi in die Ecke neben den Freifunk-Router stellen. Fertig!

## Fehlersuche
Falls der eigene Gatemon nicht nach spätestens 15 Minuten auf status.ffhb.de auftaucht, kann man mal die Check-Software von Hand starten:
```
sudo /usr/lib/gatemon/check-all-vpn-exits.sh
```
Aus den Ausgaben lässt sich evtl. rausfinden, wo das Problem liegt.

Weitere Hilfe findet man dann im IRC, auf der Mailingliste oder beim Treffen.

## TODO
* automatische Updates einrichten
* Postfix installieren, um Fehler-Ausgaben zu bekommen
* rdnssd für dynamische DNS-Server-Adressen einrichten
** s.a. https://olivergerlich.wordpress.com/2017/07/20/preventing-rdnssd-from-ruining-the-sd-card/
* Datei in /etc/cron.d/ darf keine Endung haben, war bei yannik problematisch.






# Guide on how to install Gatemon on a Raspberry Pi

This article describes the necessary steps to install a gatemon on a  [Raspberry Pi](https://www.raspberrypi.org/). 
The [Gatemon-Software](https://github.com/FreifunkBremen/gatemon) is 
a piece of software, created by some of the "Freifunk Bremen" People. 
The gatemons deliver data about the VPN-Servers continously and thereby help finding problems.
The results of all gatemons (in Bremen) are available here: 
 [status.ffhb.de](https://status.ffhb.de/) .

Questions on this Article and the gatemons are welcome either in the 
Chat or on the Mailinglist, Contact-Info can be found here: https://ffhb.de/kontakt.html. 
we are looking forward to constructive criticism and feedback.


## Hardware prerequisites
The hardware described here is a raspberry PI, which will in the end be connected by ethernet and power-cord only, no keyboard or mouse is needed after the setup.
For the setup-process you will need: 
- a screen with HDMI-Input
- USB-Keyboard
- another Computer/Laptop
  - capable of writing to SD-cards
  - connection to the internet
  - having an ssh-client (e.g. PuTTy for windows)
  - support of IPv6 
- basic knowledge on Raspis (pretty basic, really)
- basic knowledge of the linux-commandline




## install Raspian
Get an image of raspian here:  https://www.raspberrypi.org/downloads/raspbian/ 
This Documentation assumes the Lite-Version of Raspian. For other images than "Lite" it may be necessary to use an USB-Mouse.

Write the image to a SD-Card, as mentioned in the raspberry- [Guide](https://www.raspberrypi.org/documentation/installation/installing-images/README.md).


Connect your Keyboard and Screen to the PI, connect the power-cord and wait for the boot process to finish. 
You should see a login-prompt.
login with user "pi" and password "raspberry". 
Take care of possibly switched "y" and "z", depending on your keyboard. 

First: switch the keyboard layout to your favourite settings with the following command:
`sudo raspi-config`
You can also change timezone and language there.

Next: change the default password. Therefore a new one can be created in one of the following ways:
* use the command `pwgen 12 1` on another computer. 
* use the command `head /dev/urandom | tr -dc A-Za-z0-9 | head -c12` on your raspi. 

Both commands will print a new password, which you should write down on paper or a password-manager.
To finally change the password, use `passwd` on your raspi and type in the old password (raspberry), followed by the new one.

Then, the ssh-server needs to be activated. 
type `sudo raspi-config` in your commandline, under section "5.Interfacing" you can find the option "P2 SSH". Confirm the entry with "Yes".

Finally create a textfile with the follwing command:
`nano /etc/network/interfaces.d/eth0`
and put the follwing 3 lines in:

```
auto eth0
iface eth0 inet auto
iface eth0 inet6 auto
```

## connecting the raspi to the freifunk-net
Idealy you connect the raspi to one of your freifunk-routers, you could also use the wifi, but none of us tried this so far. 
(Many router-models have USB-Ports, you can use this to power the raspi)

To be connected to the Freifunk-Net, the Mesh-on-LAN option mus be disabled. (The raspi needs the client-net)

After connecting the raspi to the router and rebooting via `sudo reboot`, you can login again and check the ip-adresses, the raspi was given. 
Example:
`ip a | grep 2a06`
Example output:

```
    inet6 2a06:8782:ffbb:1337:ba27:ebff:fea1:1d97/64 scope global mngtmpaddr dynamic
```
The part between "inet6" and the slash is the public IPv6-Adress.
Use it to connect to the pi via ssh (user "pi")


## Installing Gatemon 
The Gatemon-Software needs an API-Token to send data to https://status.ffhb.de/. 
You can get a Token in our IRC-Chat or via Mail to: liste@bremen.freifunk.net. Simply say "hi, i am XYZ and would like to have a Token for status.ffhb.de"
The Token is a long string, just like a password. Please use on Token for each Gatemon. 

Furthermore your raspi needs a static IPv4-Adress (since the DHCP-Port is needed for the tests and cannot be used for the normal adress-management).
To set a static IPv4-Adress, go to https://wiki.ffhb.de/Dienste/Home#ipv4-adressen , find an unused adress, write this adress with your nicname and some contact data on this page.

The adress (lets assume 10.196.0.250 here) can be used by writing the following lines (and only these lines) in the file `/etc/network/interfaces.d/eth0` 

```
auto eth0
iface eth0 inet static
    address 10.196.0.250
    netmask 255.255.0.0
    gateway 10.196.0.1
    dns-nameservers 10.196.0.1 10.196.0.2 10.196.0.3 10.196.0.5 10.196.0.6

iface eth0 inet6 auto
```
Write your own address in the "address" line . 
After reboot, the command  `ip a | grep "inet "` should print your IP.

Next, you need the software, install it via:
```
sudo apt-get install monitoring-plugins-basic monitoring-plugins-standard nagios-plugins-contrib ndisc6 dnsutils git make gcc curl
```
(dont panic, this command installs around 80 packages)

Then install the Gatemon-Software as described on the github-page:
https://github.com/FreifunkBremen/gatemon#installation beschrieben:

```
git clone https://github.com/FreifunkBremen/gatemon
cd gatemon
make check_dhcp
sudo mkdir /usr/lib/gatemon
sudo cp check-all-vpn-exits.sh check_dhcp /usr/lib/gatemon/
sudo cp check-all-vpn-exits.cfg /etc/
sudo cp check-all-vpn-exits.cron /etc/cron.d/
```

Second last step:
edit the following lines in the file `/etc/check-all-vpn-exits.cfg`:

* API_TOKEN: your API-Token, that you got before.
* MESHMON_NAME: a short name for yur gatemon. It will appear on status.ffhb.de (no more than 20 characters, please)
* MESHMON_PROVIDER: short description of your Internet-Provider; This text will appear on status.ffhb.de in the Tooltip and can help to localize the problem to certain providers.
* NETWORK_DEVICE: eth0 (the name of the network-Interface, that is connected to the internet, usually eth0. You are free to try setting up a gatemon via wifi, please give feedback to the mailinglist.)

Now wait 15 Minutes. Then, the gatemon should appear on  https://status.ffhb.de/ . 
The Gatemon-Tests will run every 10 Minutes.
If that works, you can disconnect screen and keyboard and place the raspi next to your freifunk-Router.
DONE!

## Trouble-Shooting
If the Gatemon doesnt appear on status.ffhb.de after 15 minutes,
you can start the Check-Software with this command:
```
sudo /usr/lib/gatemon/check-all-vpn-exits.sh
```
The output may tell you more about the problem. If the output looks fine, the cronjob may be the problem. 

Further assistance can be requested in the IRC-Channel or on the Mailinglist.
