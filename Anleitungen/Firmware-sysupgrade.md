Es werden regelmäßig neue Versionen zum Testen auf dem FF Server abgelegt.
Wenn ich eine solche neue Version ausprobieren möchte, sind folgende Schritte notwendig.

Der Router und ich sind mit dem Freifunk verbunden und ich kann mich per SSH zu dem Router verbinden. Dann wechsel ich nach /tmp und frage den Routertyp ab.

~~~
cd /tmp	 
cat /proc/cpuinfo |grep machine
~~~

Beispielausgabe:
~~~
# machine                 : TP-LINK TL-WR741ND v4
oder
# machine                 : TP-LINK TL-WR841N/ND v8
oder
# machine                 : TP-LINK TL-WR1043ND
~~~
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
Jetzt noch Aktivieren:
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
1-2 Minuten warten und fertig. Abfragen kann ich die Gluonversion über die SSH Konsole mit:
~~~
cat /lib/gluon/gluon-version
#v2016.1.5
~~~
