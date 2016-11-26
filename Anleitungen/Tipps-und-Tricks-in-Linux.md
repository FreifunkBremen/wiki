## Tipps und Tricks in Linux

Als Freifunker kommen wir nicht um Linux herum. Mit dem Umstieg auf Windows 10 ändert sich so einiges in der gewohnten Bedienung. Bis wir die Einstellungen so hingefummelt haben, dass wir wieder vernünftig Arbeiten können, schauen wir doch lieber gleich einmal auf Linux.
Das wollten wir doch schon immer mal ausprobieren. Schnell sehen wir, das fast nichts so funktioniert, wie wir es aus der Windowswelt her kennen. Das macht nichts, denn auch an Windows haben wir jahrelang rumkonfiguriert bis es funktioniert.

Unter Linux kürzen wir dieses ab. Alle wichtigen Informationen bekommen wir aus https://wiki.ubuntuusers.de.
Damit uns Linux nicht frustriert, hier ein paar hilfreiche Tipps und Tricks.

Die folgen Tipps vereinfachen uns den Umgang mit Linux, was aber auch zur Folge hat, das wir ein bischen Winblöd werden.

## Inhalt:


[Alias](#inhalt_alias)

[SSH Login auf einem Router vereinfachen.](#inhalt_ssh-login-auf-einem-router-vereinfachen)

[Icons auf dem Desktop](#inhalt_icons-auf-dem-desktop)

[Klassische Startleiste](#inhalt_klassische-startleiste)

[IP v6 Adresse des angeschlossenen Routers](#inhalt_ip-v6-adresse-des-angeschlossenen-routers)

[Security Check : Routerkonfiguration auslesen](#inhalt_security-check-routerkonfiguration-auslesen)

----


###Alias
Sich wiederholende Befehlsfolgen oder häufig benutze komplizierte Eingaben, verpacken wir als Alias.
https://wiki.ubuntuusers.de/alias/
Damit diese Alias Namen permanent sind, geben wir dieses direkt in ~/.bash_aliases ein. Diese Datei liegt versteckt in unserem Homeverzeichnis.

Beispiel: Bessere Lesbarkeit durch farbliche Ausgabe der Dateien über 'ls'

alias ls='ls --color=auto'
Nach dem Speichern und öffnen einer neuen Konsole (Terminalfenster) ist die Ausgabe mit 'ls' nun farblich dargestellt.

###Alias und bashrc Systemweit
Manchmal kann es sinnvoll sein eine lokale Benutzereinstellung systemweit für alle zur Verfügung zu stellen. Für Einstellungen der Konsole wird dieses in der globalen Konfigurationsdatei /etc/bash.bashrc vorgenommen. Die Datei ist als Administrator zu öffnen. Beispiel: sudo gedit /etc/bash.bashrc

Wird dort das Alias-Beispiel von oben eingetragen, ist dieses für alle Benutzer gültig. Die globale Vorgabe wird durch die lokale Einstellung des Benutzers überschrieben. Die lokale Einstellung wird im Homeverzeichnis des Benutzers unter .bashrc vorgenommen.

###SSH Login auf einem Router vereinfachen.
Siehe auch: http://wiki.bremen.freifunk.net/Anleitungen/SSH-Node-Verwaltung.

Normalerweise öffnen wir eine SSH Verbindung in der Konsole mit 'SSH root@ipv6', dann Passwort oder Passphrase.
Das möchte ich vereinfachen.
Schritt 1. SSH Key ohne Passphrase anlegen.
Konsole öffen, mit 'cd ~./ssh'ind das Verzeichnis wechseln, wo unsere Keys abgelegt werden sollen.
Schlüsselpaar generieren mit: 'ssh-keygen -t rsa', als Namen z.B. ffhb angeben. Es werden nun ein privater Schlüssel ffhb und ein öffentlicher Schlüssel ffhb.pub im Verzeichnis ./ssh angelegt.
Den öffentlichen Schlüssel kopieren wir nun auf unseren Router.
Bisher bekanntes SSH Login auf den Router, wechseln nach 'cd /etc/dropbear'. Öfnnen der Datei authorized_keys mit vi 'vi authorized_keys'
Am Ende der Datei unseren Schlüssel kopieren und Speichern. Mit 'chmod 0600 authorized_keys' die Dateirechte setzen.
Auf unserem Rechner fügen wir in die Datei '~/.bash_aliases' unser neues Alias ein.
z.B. alias router='ssh root@ipv6' und speichern.
In einer neuen Konsole bekommen wir nur durch die Eingabe von 'router' sofort eine SSH Verbindung zu unserem Router.

*Alternative Lösung:*
Wir legen im Ordner '~/.ssh/' eine Textdatei namens config an. In diese Datei kopieren wir folgende Zeilen.
~~~
#ssh (secure shell) configuration file
Host router1
    HostName ipv6-Adresse
    Port 22
    User root
    IdentityFile ~/.ssh/ffhb
~~~
Auf der Konsole mit 'SSH router1' sind wir sofort auf unserem Router.
Siehe: https://wiki.ubuntuusers.de/SSH/ oder 'man ssh_config'
~~~
Lokaler Benutzer: ~/.ssh/config
Systemweite Einstellung:  /etc/ssh/ssh_config
~~~

*Der Linuxprofi kopiert den Schlüssel wie folgt auf den Router:*
~~~
cat ~/.ssh/ffhb.pub | ssh root@fe80::6a72:51ff:fe04:f52e%en1 'cat >> /etc/dropbear/authorized_keys'
~~~
ffhb.pub war der öffentliche Schlüssel, den wir weiter oben generiert haben. Damit der Befehl auch tatsächlich auf dem Router ausgeführt wird, muss noch ein leztes Mal das Passwort eingegeben werden, aber anschließend nutzen alle Logins den Schlüssel. 

###Icons auf dem Desktop
Mit Icons auf dem Desktop sollte man Sparsam sein. Wer Icons auf dem Desktop haben möchte, kann wie folgt vorgehen. Bei Ubuntu liegt am linken Rand der Starter. Das erste Icon oben ist die Suchfunktion. Alle dort angezeigten Icons können direkt auf den Desktop gezogen werden.

###Klassische Startleiste
Nicht alle erfreuen sich an dem neuen Starter. Einfach über das Softwarecenter nach ClassicMenue Indicator' oder 'Startleiste' suchen, installieren, freuen.

###IP v6 Adresse des angeschlossenen Routers
Wir wollen die IPv6 Adresse des Routers finden. Dazu einfach im Terminal eingeben (sofern per WLAN mit Freifunknetz verbunden): (Vorweg: *%en1* ist der Bezeichner für das Interface, über das verbunden werden soll. Hier Ethernet 1....kann auch 0 oder 2 ... oder ein ganz anderes Interface sein. Im Zweifel *"ifconfig"* oder *"ip addr show"* eingeben und die Bezeichnung der Interfaces checken). Mein *%en0* Interface ist z.B *enp0s25*

Der Interfacename wir auch unter dem Netzwerksymbol im Menüpunkt Verbindungsinformation angezeigt (Schnittstelle: Ethernet (enp0s25)).

ping6 ff02::1%en0 gibt sonst ein "unknown Host" aus. Ausserdem wollen wir nicht alle Adressen aus dem Netz Auflisten sondern die Ausgabe auf den ersten angeschlossenen Router begrenzen. Deshalb folgede Befehlszeile verwenden.
~~~
ping6 -c3 ff02::2%enp0s25 | grep -v DUP | grep fe80
~~~
Da ich mir das nicht merken kann, mach ich ein Alias davon. Beispiel Routerip oder kurz 'rip'.
~~~
alias rip='ping6 -c3 ff02::2%enp0s25 | grep -v DUP | grep fe80'
~~~
~~~
ffhb@FFHB:~$ rip
64 bytes from fe80::76ea:3aff:fee4:7374: icmp_seq=1 ttl=64 time=0.688 ms
64 bytes from fe80::76ea:3aff:fee4:7374: icmp_seq=2 ttl=64 time=0.782 ms
64 bytes from fe80::76ea:3aff:fee4:7374: icmp_seq=3 ttl=64 time=0.586 ms
ffhb@FFHB:~$
~~~


###Security Check : Routerkonfiguration auslesen

Im Folgenden ein kleines Script, welches aus einer Linux-Umgebung heraus über ip v4 oder ip v6 die Konfiguration eines Freifunkrouters ausliest und die Daten lokal in einer Datei ablegt. Das Script piped die Bildschirmausgabe einfach in eine Datei. Es werden keine Schreiboperationen auf dem Router durchgeführt.
Das Script dient zum Experimentieren und als Kopiervorlage, die Abragen bitte auf eigene Bedürfnisse Anpassen.
Die folgenden Zeilen als allfiles.sh speichen und ausführbar machen (chmod 755 allfiles.sh)
Der Aufruf erfolgt z.B. aus meinem Homeverzeichnis mit ./allfiles.sh 127.0.0.1


~~~
#!/bin/bash

# Usage: execute ./allfiles.sh Ip6/4_Addr and check current directory for output
# before usage, put your existing private ssh keyfile in your .ssh directory ore use pw

CONFFILE="RouterConfig.txt"
OUTFILE="RouterCheck.txt"
UCIFILE="UCI_Config.txt"

# Teil 1: Einzelabfrage
echo "#-cat /etc/config/*------------------------------------------------------------------------#" > $CONFFILE 2>&1
ssh root@$1 cat /etc/config/* >> $CONFFILE 2>&1

echo "#-/etc/dropbear/*--------------------------------------------------------------------------#" >> $CONFFILE 2>&1
ssh root@$1 cat /etc/dropbear/authorized_keys >> $CONFFILE 2>&1
echo "#-cat /etc/dropbear/authorized_keys--------------------------------------------------------#" >> $CONFFILE 2>&1
echo "#------------------------------------------------------------------------------------------#" >> $CONFFILE 2>&1

echo "#-UCI Show --------------------------------------------------------------------------------#" > $UCIFILE 2>&1
ssh root@$1 uci show >> $UCIFILE 2>&1
echo "#------------------------------------------------------------------------------------------#" >> $UCIFILE 2>&1

# Teil 2: Schleifenabfrage
echo "Linux-Check - Allgemein: Bitte etwas Geduld!"
echo "Linux-Check - Allgemein:" > $OUTFILE 2>&1
echo "#------------------------------------------------------------------------------------------#" >> $OUTFILE 2>&1
for testget in 	date uptime\
		uname 'uname -r' 'cat /etc/issue' \
		'cat /etc/passwd' 'cat /etc/ssh/sshd_config' \
		'netstat -tulpe' 'netstat -rn' 'netstat -aptn' \
		'iptables -L' 'iptables -t nat -L' \
		'cat /etc/*' 'cat /etc/config/*' 'cat /etc/dropbear/authorized_keys' \
		'opkg list-installed' \
		ifconfig 'ps -aux' 'ps w' 'df -h' \
		'crontb -l' 'traceroute' \
		'ls /var/log/' mount 'block info'\
		'/etc/init.d/fastd show_key mesh_vpn' 'ifconfig |head|tail -n1' \
		'ip r s t all' 'cat /lib/gluon/release' 'cat /lib/gluon/gluon-version' \
		'cat /tmp/sysinfo/model' 'batctl tl |grep W |wc -l' 'batctl tl |grep W |wc -l' \
		'batctl tg |grep W |wc -l' iwinfo 'batctl if' \
		date \
		; do
	echo -n "."	
	echo "" >> $OUTFILE 2>&1
	echo "#------------------------------------------------------------------------------------------#" >> $OUTFILE 2>&1
	echo "##-> ${testget}" >> $OUTFILE 2>&1
	ssh root@$1 $testget >> $OUTFILE 2>&1
done # for testget
echo "#------------------------------------------------------------------------------------------#" >> $OUTFILE 2>&1
echo "Linux-Check - Allgemein: Ende " >> $OUTFILE 2>&1
echo ""
echo "Linux-Check - Allgemein: Programm Beendet!"
echo "Ergebnisse unter: $OUTFILE,$UCIFILE und $CONFFILE"


~~~

Noch ein Hinweis. In einer VM Umgebung die Netzwerkeinstellunng NAT kontrollieren und ggf. den Haken bei ip6 setzen oder den ip6 Präfix anpassen (2a06:8782:ffbb:1337::/64)




