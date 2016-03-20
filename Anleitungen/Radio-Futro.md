### Freifunkradio: Streaming-Server mit Icecast2 und Ices2 


Um einen eigenen Internet-Radiosender zu bauen, brauchen wir ca. 2Mb Speicherplatz auf unserem Router, einen USB-Stick für die Medien und etwas Leistungsreserve. Wenn wir VPN-Mesh machen (Normalfall) steht uns dafür kaum Leistung zur Verfügung. In diesem Fall könenn wir einen weiteren Router ohne Verschlüsseung per Kabel meshen oder einen Offloader verwenden. Der Futro benötigt ca. 1% seiner Leistung für den VPN Tunnel, also genug Reserve zum Spielen.

Die folgende Anleitung ist nicht komplett, es fehlt IP V4, DNS Auflösung, DDNS Unterstützung.
Aber um es einmal auszuprobieren reicht es aus.


## Inhalt:


[1.) Allgemeines](#Allgemeines)

2.) Voraussetzungen

3.) Installation Icecast & Ices

4.) Konfiguration Icecast & Ices

5.) FAQ

6.) Relay-Server

----


[1.) Allgemeines]

Ihr wolltet schon immer mal selbst ein WebRadio betreiben oder nur mal über euer WLAN die Musik nach draussen zur Gartenparty streamen?
Dann solltet ihr euch dieses HowTo genauer ansehen und bei Erfolg hier die fehlerhaften Angaben Korrigieren. 
Hier nun ein kleines HowTo um auf OpenWRT mit Icecast und Ices eine Radiostation aufzubauen.

Doch wir brauchen nicht nur einen Server (Icecast), der unsere Musik im Netz verbreitet sondern auch noch ein Programm, welches die Musik z.B. 
an den Server sendet. Diese Funktion übernimmt Ices. Der Server sendet nur Daten, wenn sich ein Client verbunden hat.
Die Verdinung zwischen Streamclient und Streamserver erfolgt über virtuelle Mountpoints, die wir definieren müssen.

Ich werde hierfür ices vorstellen, da es das vielseitigste Tool ist. Ab OpenWRT *v2016* will sich Ices nicht mehr direkt installiert lassen,
da wird dann der Schalter --force-depends aktiv, hat bei funktioniert.


Mit Icecast wird nun eine erste Konfiguration durchgeführt, die nur die Grundvorraussetzungen erfüllt. Für weitere Informationen 
bitte die offizielle Doku @ http://www.icecast.org/docs.php. aufsuchen. 



2.) Voraussetzungen:

* libogg (www.vorbis.com)
* libvorbis (www.vorbis.com)
* libxml2 (http://www.xmlsoft.org)
* libshout 2 (http://www.icecast.org/download.php)
* libperl (http://www.perl.org)


3.) Installation
* icecast (http://www.icecast.org/download.php)
* ices (http://www.icecast.org/ices.php)

Beide Pakete lassen sich im Normalfall mit dem gängigen Linux Pakettools installieren.
Bei OpenWRT mit opkg install. Damit auch alle lib´s installiert werden, geben wir dem Install ein --force-depends mit.

~~~
  opkg install icecast --force-depends
Installing icecast (2.4.2-1) to root...
Downloading http://downloads.openwrt.org/chaos_calmer/15.05/x86/generic/packages/packages/icecast_2.4.2-1_x86.ipk.
Installing libcurl (7.40.0-3.1) to root...
Downloading http://downloads.openwrt.org/chaos_calmer/15.05/x86/generic/packages/base/libcurl_7.40.0-3.1_x86.ipk.
Installing libpolarssl (1.3.14-1) to root...
Downloading http://downloads.openwrt.org/chaos_calmer/15.05/x86/generic/packages/base/libpolarssl_1.3.14-1_x86.ipk.
Installing libxslt (1.1.28-2) to root...
Downloading http://downloads.openwrt.org/chaos_calmer/15.05/x86/generic/packages/packages/libxslt_1.1.28-2_x86.ipk.
Installing libopenssl (1.0.2g-1) to root...
Downloading http://downloads.openwrt.org/chaos_calmer/15.05/x86/generic/packages/base/libopenssl_1.0.2g-1_x86.ipk.
Configuring libpolarssl.
Configuring libcurl.
Configuring libxslt.
Configuring libopenssl.
Configuring icecast.


opkg install ices
Installing ices (2.0.2-1) to root...
Downloading http://downloads.openwrt.org/chaos_calmer/15.05/x86/generic/packages/packages/ices_2.0.2-1_x86.ipk.
Multiple packages (kmod-input-core and kmod-input-core) providing same name marked HOLD or PREFER. Using latest.
Collected errors:
 * satisfy_dependencies_for: Cannot satisfy the following dependencies for ices:
 *      kernel (= 3.18.20-1-8549f8163c15d79b053f26aa0d52e96f) *
 * opkg_install_cmd: Cannot install package ices.


 opkg install ices --force-depends
Installing ices (2.0.2-1) to root...
Downloading http://downloads.openwrt.org/chaos_calmer/15.05/x86/generic/packages/packages/ices_2.0.2-1_x86.ipk.
Multiple packages (kmod-input-core and kmod-input-core) providing same name marked HOLD or PREFER. Using latest.
Installing libshout (2.3.1-1) to root...
Downloading http://downloads.openwrt.org/chaos_calmer/15.05/x86/generic/packages/packages/libshout_2.3.1-1_x86.ipk.
Installing libspeex (1.2rc1-1) to root...
Downloading http://downloads.openwrt.org/chaos_calmer/15.05/x86/generic/packages/packages/libspeex_1.2rc1-1_x86.ipk.
Installing libtheora (1.1.1-1) to root...
Downloading http://downloads.openwrt.org/chaos_calmer/15.05/x86/generic/packages/packages/libtheora_1.1.1-1_x86.ipk.
Installing libvorbisidec (1.0.3-20150104-1) to root...
Downloading http://downloads.openwrt.org/chaos_calmer/15.05/x86/generic/packages/packages/libvorbisidec_1.0.3-20150104-1_x86.ipk.
Installing libxml2 (2.9.2-3) to root...
Downloading http://downloads.openwrt.org/chaos_calmer/15.05/x86/generic/packages/packages/libxml2_2.9.2-3_x86.ipk.
Installing alsa-lib (1.0.28-1) to root...
Downloading http://downloads.openwrt.org/chaos_calmer/15.05/x86/generic/packages/packages/alsa-lib_1.0.28-1_x86.ipk.
Installing kmod-sound-core (3.18.20-1) to root...
Downloading http://downloads.openwrt.org/chaos_calmer/15.05/x86/generic/packages/base/kmod-sound-core_3.18.20-1_x86.ipk.
Configuring libtheora.
Configuring kmod-sound-core.
Configuring alsa-lib.
Configuring libvorbisidec.
Configuring libspeex.
Configuring libxml2.
Configuring libshout.
Configuring ices.
Collected errors:
 * satisfy_dependencies_for: Cannot satisfy the following dependencies for ices:
 *      kernel (= 3.18.20-1-8549f8163c15d79b053f26aa0d52e96f) *
  
 
  opkg install ices --force-depends
Package ices (2.0.2-1) installed in root is up to date.
~~~




4.) Konfiguration Icecast

Die im folgenden aufgeführten Konfigurationsdateien sind dazu gedacht, komplett übernommen und lediglich angepasst zu werden. 
Selbsterversändlich könnt ihr auch die default-configs bearbeiten, jedoch stehen da recht viele, für unsere Zwecke unnötige, 
Dinge drin, die evtl. verwirren könnten.


Als erstes richten wir den server ein. 
Dazu editieren wir **/etc/icecast.xml**, wie folgt:

~~~

<icecast>
    <limits> <!--ausser clients kann man in diesem Abschnitt die default-werte lassen-->
        <clients>30</clients> <!--max Zuhörer -->
        <sources>10</sources>
        <threadpool>5</threadpool>
        <queue-size>102400</queue-size>
        <client-timeout>30</client-timeout>
        <header-timeout>15</header-timeout>
        <source-timeout>10</source-timeout>
    </limits>

    <authentication>
        <!-- Wichtig, Der Benutzername um zum server zu connecten ist 'source' der ist fix-->
        <!-- Das Passwort um sich beim server zum streamen einzuloggen, das ist das PW für source -->
        <source-password>dasPasswort</source-password>
        <!-- Solltet ihr Relay-Server zu euch verbinden lassen wollen, hier das pw dafür -->
        <relay-password>RelayPass</relay-password>
        <!-- Admin-Zugangsdaten für Online-Administration -->
        <admin-user>admin</admin-user>
        <admin-password>adminPasswort</admin-password>
    </authentication>

    <!-- Ip oder hostname des Servers -->
    <hostname>localhost</hostname>
    <!-- Port auf den der Server hören soll -->
    <listen-socket>
        <port>8000</port>
    </listen-socket>
   
    <paths><!-- Installationsverzeichnis von icecast -->
        <basedir>/usr/share/icecast</basedir>
        <!--verschiedene Verzeichnisangaben, das Logdir wird später deaktiviert. -->
        <logdir>/var/log/icecast</logdir>
        <webroot>/usr/share/icecast/web</webroot>
        <adminroot>/usr/share/icecast/admin</adminroot>
     </paths>
    
    <logging> <-- Diese Dateien bereiten Probleme, wird später deaktiviert -->
        <accesslog>access.log</accesslog>
        <errorlog>error.log</errorlog>
      	<loglevel>1</loglevel>  <!-- 4 Debug, 3 Info, 2 Warn, 1 Error -->
    </logging>

    <security>
        <chroot>0</chroot>
        <!-- wichtig falls man den server beim booten starten lässt.
             Hier kann man festlegen als welcher Benutzer der server laufen soll
             (muss auf dem System exisiteren) und das bereitet uns Probleme mit den Logdateien s.u.-->
        <changeowner>
            <user>ice</user>
            <group>ice</group>
        </changeowner>
    </security>
</icecast>
~~~


WICHTIG: Der User den ihr unter changeowner angegeben habt muss Schreibrechte auf das logdir haben!  (chown ice /var/log/icecast && chgrp ice /var/log/icecast)

So, das wäre geschafft. Nun können wir den Server mal testen (als root!):

~~~
icecast -b -c /etc/icecast.xml
~~~

Wenn ihr alles richtig gemacht habt, sollte lediglich ausgegeben werden, dass der Server nun unter einem anderen Benutzer als root läuft:
~~~
Changed groupid to 1001.
Changed userid to 1001.
~~~
Ob der Server läuft, sehen wir mit dem Befehl **top**, in der Prozessliste sollten wir dann icecast sehen.


4.) Konfiguration Ices

Das wäre geschafft. Das war ja gar nicht so schwer. Nun müssen wir unseren Server nur noch irgendwie mit Musik füttern und dazu benutzen wir nun Ices: Auch Ices benutzt eine xml-config-datei. Diese legen wir uns einfach frisch an, z.B. in /etc/ices-playlist.xml oder kopieren die Ices Beispieldateien. Für jeden Stream wird Ices mit einer eigenen Konfig gestartet.

Folgenden Inhalt sollte sie besitzen:

~~~

<?xml version="1.0"?>
<ices>
    <background>1</background> <!-- Soll ices im Hintergrund laufen? (1 falls ja) -->
    <logpath>/var/log/ices</logpath> <!-- wo soll hingelogged werden?-->
    <logfile>ices.log</logfile>
    <loglevel>1</loglevel> <!-- 1=error,2=warn,3=info,4=debug -->
    <consolelog>1</consolelog> <!--verbose-mode, alle meldungen werden auf der konsole ausgegebn. Hierbei wird nicht in obige Logdatei gelogged!!-->
    <stream>
        <metadata><!--Gebt eurem Radio einnen Namen etc...-->
            <name>Radio Freifunk</name>
            <genre>Pop</genre>
            <description>Freifunk Radio Community</description> 
        </metadata>
        <input> 
        <!--Aufnahme-Weiterleit-Modul-->
	    <module>playlist</module> 
			<param name="type">basic</param>
            <param name="file">/mnt/sda3/Musik/playlist.txt</param>
            <param name="random">0</param>
            <param name="restart-after-reread">0</param>
            <param name="once">0</param>
            <param name="metadata">1</param><!--Sollen Titeldaten der Songs mitgestreamt werden?-->
            <param name="metadatafilename">/mnt/sda3/Musik/trackinfo.txt</param><!--wenn ja, wo stehen die? --<
        </input>
        <instance>
            <hostname>localhost</hostname><!--wo laeuft der icecast-server?--> 
			<port>8000</port> <!--über welchen Port connecten?-->
            <password>dasPasswort</password> <!--Passwort?-->
            <mount>/radio.ogg</mount> <!--adresse des eigentlichen streams, mein virtueller Mountpoint -->
            <reconnectdelay>2</reconnectdelay>
            <reconnectattempts>5</reconnectattempts>
            <maxqueuelength>80</maxqueuelength>
			<downmix>1</downmix><!--aus stereo mach mono, oder weglassen-->
			<encode>  
                <nominal-bitrate>64000</nominal-bitrate> <!-- bps. e.g. 64000 for 64 kbps -->
                <samplerate>44100</samplerate>
                <channels>2</channels>
            </encode>    
        </instance>
    </stream>
</ices>

~~~

So, alles was zwischen den stream-tags steht, beschreibt einen Stream. Ihr könnt auch mehrere Streams definieren, z.B. einen in Stereo, einen mit 128Kbit usw. Diese benötigen dann halt einen anderen virtuellen mount-point, die in Icec & Icecast angegeben werden.

Wie ihr oben gesehen habt, wollen wir ja auch title und artist streamen und haben dazu eine Datei namens trackinfo.txt in der config angegeben.
Um diese Datei mit Inhalt zu füllen verwendet ihr ein Musikbearbeitungsprogramm eurer Wahl. Das macht viel Arbeit, ich hab es einfach weggelassen. Evtl. mag es jemand hier Ergänzen.

Nun starten wir unseren Streamplayer ices. Für unterschiedliche Stream lege ich die Playlist und ices-playlist.xml in dem entsprechendem Medienverzeichnis ab.
~~~
ices /etc/ices-playlist.xml
~~~
Sollte alles glatt gegangen sein, sollten wir auf http://ip-desservers:8000/status.xsl nun sehen, dass ein stream läuft.
Nun könnt ihr euch noch von einem Rechner zu eurem Server verbinden und schauen, ob auch wirklich korrekt gestreamt wird.

~~~
http://ip-desserver:8000/radio.ogg oder als ipv6 http://[2a06:8782:ffbb:1337:219:99ff:fe7a:7220]:8000/radio.ogg
~~~

Das Admin-Webinterface findet ihr unter:

~~~
http://ip-desservers:8000/admin/stats.xsl oder http://[ipv6]:8000/admin/stats.xsl
~~~

5.) FAQ:

* Auf dem Webinterface wird kein Mountpoint oder Stream angezeigt.

  Ggf. gibt es Zugriffsprobleme mit den Log Dateien. Sie müssen vorhanden sein, sonst will der Player nicht. Eine Lösungsversuch wäre:

~~~
mkdir -p /var/log/icecast
touch /var/log/icecast/error.log
touch /var/log/icecast/access.log
chmod 777 /var/log/icecast/error.log
chmod 777 /var/log/icecast/access.log
chown ice:ice /var/log/icecast/error.log
chown ice:ice /var/log/icecast/access.log

icecast -b -c /etc/icecast.xml

mkdir -p /var/log/ices
touch /var/log/ices/ices.log
chmod 777 /var/log/ices/ices.log

ices /mnt/sda3/Musik/ices-playlist.xml
~~~

* Mein Musikverzeichnis ist weg.
Noch kein Automount konfiguriert.

~~~
von Hand:
mount -t vfat /dev/sdb1 /mnt/usb
mount /dev/sda3 /mnt/sda3
~~~

* Wie kann ich meine Medien automatisch einbinden lassen?

In der Datei /etc/config/fstab die zu mountenden devices hinzufügen. Beispiel:
~~~
config 'mount'
	option	target	'/mnt/sda3'
	option	uuid	'b0dcc595-86dd-4154-a749-45894b002a18' *Meine neue Partition auf der CF-Card*
	option 'device' '/dev/sda3'
	option 'options' 'rw,sync'
	option 'enabled_fsck' '0'
	option 'enabled' '1'

config 'mount'
	option	target	'/mnt/usb'
	option	uuid	'6633-6536' *Mein USB Stick*
	option 'device' '/dev/sdb1'
	option 'options' 'rw,sync'
	option 'enabled_fsck' '0'
	option 'enabled' '1'
~~~

* Nützliche Befehle:

~~~
/etc/init.d/icecast start
/etc/init.d/icecast stop
/etc/init.d/icecast restart
~~~

* Terminate Streaming
Streams are terminated by killing Ices and/or stop running the Icecast server:

~~~
killall ices
/etc/init.d/icecast stop
~~~


6.) Relay-Server aufsetzen:

Was ist denn überhaupt ein Relay-Server? In gewisser Weise ist es vergleichbar mit einem FTP-Mirror oder dem Mirror einer WebSite. 
Ein Relay-Server verbreitet also genau die gleiche Streams wie sein Masterserver. Hierzu fragt er in regelmäßigen Abständen den 
Masterserver ab, welche Streams gehostet werden und übernimmt diese Streams dann. So muss man sich um Mount-Point-Konfiguration 
und encoding bei einem Relay-Server keine Gedanken machen.
Die /etc/icecast.xml sieht nun folgendermassen aus:

~~~
<icecast>
    <limits><!--ausser clients kann man in diesem Abschnitt die default-werte lassen-->
        <clients>30</clients> <!--max Zuhörer -->
        <sources>10</sources>
        <threadpool>5</threadpool>
        <queue-size>102400</queue-size>
        <client-timeout>30</client-timeout>
        <header-timeout>15</header-timeout>
        <source-timeout>10</source-timeout>
    </limits>

    <authentication>
        <!-- Admin-Zugangsdaten für Online-Administration -->
        <admin-user>admin</admin-user>
        <admin-password>sdminPasswort</admin-password>
    </authentication>

    <!-- Ip oder hostname des Servers -->
    <hostname>localhost</hostname>

    <!-- HIERAUF KOMMT ES NUN AN -->
    <master-server>192.168.169.15</master-server>
    <master-server-port>8000</master-server-port>
    <master-update-interval>120</master-update-interval>
    <master-password>RelayPass</master-password>

    <!-- Port auf den der Server hören soll -->
    <listen-socket>
        <port>8000</port>
    </listen-socket> 
    <paths><!-- Installationsverzeichnis von icecast -->
        <basedir>/usr/share/icecast</basedir>
	<logdir>/var/log/icecast</logdir>
        <webroot>/usr/share/icecast/web</webroot>
        <adminroot>/usr/share/icecast/admin</adminroot>
     </paths>
    
    <logging>
        <accesslog>access.log</accesslog>
        <errorlog>error.log</errorlog>
      	<loglevel>1</loglevel> <!-- 4 Debug, 3 Info, 2 Warn, 1 Error -->
    </logging>

    <security>
        <chroot>0</chroot>
	 <changeowner>
            <user>ice</user>
            <group>ice</group>
	</changeowner>    
    </security>
</icecast>
~~~

Auch hier gilt wieder: Der User den ihr unter changeowner angegeben habt muss Schreibrechte auf das logdir haben! (chown ice /var/log/icecast && chgrp ice var/log/icecast). Oder aus der Konfig löschen

Zum Starten des Relay-Servers:
~~~
icecast -b -c /etc/icecast/icecast.xml
~~~
Nun sollte sich euer Server beim Masterserver als normaler client einloggen, die mountpoints übernehmen und streamen. Der Masterserver bekommt davon nichts mit, da der Relay-Server wie ein normaler client einlogged.


Viel Spass beim Radiohören

