[[_TOC_]]

##sysupgrade

Es werden regelmäßig neue Versionen zum Testen auf dem FF Server abgelegt.
Wenn ich eine solche neue Version ausprobieren möchte, sind folgende Schritte notwendig.

Wichtig: https://wiki.openwrt.org/de/doc/howto/generic.sysupgrade

Der Router und _ich_ sind mit dem Freifunk verbunden und _ich_ kann mich per SSH zu dem Router verbinden. Wechseln nach /tmp und den Routertyp abfragen, damit wir das richtie Image einspielen.

##Routerversion abfragen

~~~
cd /tmp
lua -e 'print(require("platform_info").get_image_name())'
~~~

Beispielausgabe:
~~~
tp-link-tl-wdr4300-v1
~~~
oder
~~~
tp-link-tl-wr740n-nd-v4
~~~

##Image suchen

Jetzt suchen wir uns das passende Image.
Unter https://downloads.bremen.freifunk.net/firmware/ werden die Verzeichnisse mit den Images aufgelistet.
Zum Beispiel liegen unter https://downloads.bremen.freifunk.net/firmware/all/2016.1.5+bremen1/sysupgrade/
die Images für v2015.1.5+bremen1 vom 26.5.2016. Bzw. einfach mal Suchen und das finden, welches ich Einspielen möchte.

Den Link zu dem entsprechen Image aus dem Browser kopieren und mit wget voran auf der Konsole einfügen. Auf dem Image mit rechter Maustaste klicken und Linkadresse kopieren.

Für den TP-LINK TL-WR1043ND sieht das so aus.
~~~
wget http://downloads.bremen.freifunk.net/firmware/all/2016.1.5+bremen1/sysupgrade/gluon-ffhb-2016.1.5+bremen1-tp-link-tl-wr1043n-nd-v1-sysupgrade.bin
~~~
Ausgabe:
~~~
Connecting to downloads.bremen.freifunk.net ([2a06:8782:ff00::f2]:80)
gluon-ffhb-2016.1.5+ 100% |********************************************************************************|  3456k  0:00:00 ETA
~~~

##Image Aktivieren:

~~~
echo 3 > /proc/sys/vm/drop_caches
sysupgrade -F gluon-ffhb-2016.1.5+bremen1-tp-link-tl-wr1043n-nd-v1-sysupgrade.bin
~~~
Ausgabe:
~~~
Saving config files...
killall: watchdog: no process killed
Sending TERM to remaining processes ... sse-multiplexd uhttpd dnsmasq odhcp6c udhcpc odhcp6c batman-adv-visd ntpd alfred batadv-vis dnsmasq respondd ubusd
~~~
1-2 Minuten warten und fertig. 

###Gluon Version abfragen

Abfragen kann ich die Gluonversion über die SSH Konsole mit:
~~~
cat /lib/gluon/gluon-version
#v2016.1.5
~~~

Weitere Informationen zur Konsole unter:
https://wiki.openwrt.org/de/doc/howto/user.beginner.cli

##Ein Wort zur Vorsicht.
Mit `sysupgrade -F` erzwinge ich den Upgrade und ignoriere Fehlermeldungen. Bitte auch die technische Referenz Beachten.

https://wiki.openwrt.org/doc/techref/sysupgrade

https://wiki.openwrt.org/de/doc/howto/generic.sysupgrade

Hier eine kleine Ergänzung, falls vorhandene Daten / Programme gesichert werden sollen. 

##sysupgrade mit vorgehendem Backup.

Wird ein Upgrade durchgeführt, sind einige Einstellungen/Installationen weg.
Insbesondere werden Flashkarten neu Partitioniert, eigene Partitionen werden gelöscht. Beispiel am X86 Image, das ist 50Mb groß. Bei einer 1GB oder 512Mb Flashkart bleibt viel Platz zum Experimentieren. Ich hatte die Partition sda von 50Mb auf 128Mb vergrössert und dem verbleibendem Platz einer sdb Partition zugeordnet.**Nach dem sysupgrade ist alles wieder Original!**
Also reicht mir auch eine kleine Flashcard. Leider sind auch alle installierten Programme und Konfigurationen weg und das ist ärgerlich. Vor dem Anschalten des Autoupdaters, Backup erstellen.

###Backup erstellen

Hier ein verbesserungsfähiger Vorschlag, wie ich ein Teilbackup mache.

Benötigt werden SSH (Konsole) und SCP Zugang (Dateitransfer).

In "/lib/opkg/status" stehen die installierten Programme. Einige Einträge enden mit "Auto-Installed: yes", die automatisch installiert wurden, alle anderen nachträglich manuel. Genau diese Einträge fischen wir heraus. Das geht von Hand in einem Editor oder einfach mit einem Script.
Gefunden unter: https://wiki.openwrt.org/doc/howto/generic.sysupgrade#ensure_desired_configuration_files_will_be_saved

Mit `cd /tmp`nach /tmp wechsel und die Datei listuserpackages.awk mit genau 2 Zeilen anlegen.
~~~
/^Package:/{PKG= $2}
/^Status: .*user installed/{print PKG}
~~~
Im Verzeichnis /tmp nun das Script mit 
~~~
awk -f listuserpackages.awk /usr/lib/opkg/status
~~~
ausführen. Nun werden alle zusätzlich installierten Pakete aufgelistet. Durch Umlenken auf >myprog.txt wird die Liste in eine Datei geschrieben, die ich über SCP zum Bearbeiten aus /tmp herunterlade. Geübte machen das mit vi auf dem Router :-)
~~~
awk -f listuserpackages.awk /usr/lib/opkg/status >myprog.txt
~~~
Die Programme, die wir später nicht mehr haben wollen, können aus der Liste gelöscht werden. Diese Liste wird nach dem sysupgrade mit opkg install <programme> wieder neu installiert.

Bei Programmen mit zusätzlichen Konfigurationsdateien, müssen wir diese mit scp aus dem zugehörigen Verzeichnis retten. Meistens aus /etc & /etc/config. Bei waren das netfilter/snort/icecast/ices/openssl Konfigurationen, die später einfach zurückgespielt werden. Sicherheitshalber auch die fstab, dort habe die automounteinträge und den Schreibschutz für die USB Sticks eingefügt und sofern vorhanden die Autostarteinträge aus /etc/init.d/

Verbesserungen und Erweiterungen sehr erwünscht. Einfach oben den `Edit` Knopf drücken.

