### Freifunkradio: Streaming-Server mit Icecast2 und Ices2 


Um einen eigenen Internet-Radiosender zu bauen, brauchen wir ca. 2Mb Speicherplatz auf unserem Router, einen USB-Stick für die Medien und etwas Leistungsreserve. Wenn wir VPN-Mesh machen (Normalfall) steht uns dafür kaum Leistung zur Verfügung. In diesem Fall könenn wir einen weiteren Router ohne Verschlüsseung per Kabel meshen oder einen Offloader verwenden. Der Futro benötigt ca. 1% seiner Leistung für den VPN Tunnel, also genug Reserve zum Spielen.

Die folgende Anleitung ist nicht komplett, es fehlt IP V4, DNS Auflösung, DDNS Unterstützung.
Aber um es einmal auszuprobieren reicht es aus.


## Inhalt:


1.) Allgemeines

2.) Voraussetzungen

3.) Installation Icecast & Ices

4.) Konfiguration Icecast & Ices

5.) FAQ

6.) Relay-Server

----


1.) Allgemeines:

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


