**ZNC IRC Bouncer** auf einem Router oder Offloader

Wenn ich nicht im IRC Channel Online bin, bekomme ich keine Chats mit.
Was kann ich anstellen, damit ich immer Online bin, also Historie-Daten bekomme?
Die Konversationen der Vergangenheit lassen sich für einen normalen User nicht abrufen. 
Also immer Online sein? Ja, warum nicht, unser auf OpenWRT/LEDE basierender Router ist immer Online 
und wir können/dürfen Linux Pakete installieren.

Viele benutzen den ZNC IRC Bouncer, der immer für uns Online ist. Wenn wir uns mit dem Bouncer verbinden,
bekommen wir automatisch alles aus der Vergangenheit mit. 

Diese Anleitung ist nicht perfekt, und darf gerne überarbeitet werden.


Auf unserem Gerät wechseln wir erst mal nach /tmp/ und installieren die ZNC Pakete. Mit dem Befehl 'OPKG List' werden alle Pakete gelistet, am Ende der Liste finden wir odie ZNC Module.
~~~
opkg update
opgk install znc znc-mod-fail2ban znc-mod-flooddetach znc-mod-log znc-mod-webadmin znc-webskin-ice
~~~
Starten den ZNC IRC Bouncers -h oder -v, um zu sehen ober er funktioniert. 
~~~
znc -h
[ ** ] USAGE: znc [options]
[ ** ] Options are:
[ ** ]  -h, --help         List available command line options (this page)
[ ** ]  -v, --version      Output version information and exit
[ ** ]  -f, --foreground   Don't fork into the background
[ ** ]  -D, --debug        Output debugging information (Implies -f)
[ ** ]  -n, --no-color     Don't use escape sequences in the output
[ ** ]  -r, --allow-root   Don't complain if ZNC is run as root
[ ** ]  -c, --makeconf     Interactively create a new config
[ ** ]  -s, --makepass     Generates a password for use in config
[ ** ]  -p, --makepem      Generates a pemfile for use with SSL
[ ** ]  -d, --datadir      Set a different ZNC repository (default is ~/.znc)
~~~

mit znc -c legen wir eine neue Konfiguration an. Dabei legen wir Namen und Passwort fest.
Die Konfigurationsdatei wird unter /etc/config/znc abgelegt und sieht dann so aus.
~~~
config znc
	# where to listen for connections
	list listener	'192.168.1.1 1234'  # oder ipv6:1234
	# If using SSL sockets, use the following certifcate:
	# option znc_ssl_cert '/etc/znc.cert'

	# load global modules (You need to install them first):
	# list module 'fail2ban'
	# remove this to enable the service
	# option disabled 1

config user 'USER'
	# Use either a plain text password or use the full sha256#... line.
	# You can generate one with 'znc -s'.
	option password 'PASSWORD'
	option nick 	'USER'
	option altnick 	'USER2'
	option ident 	'openwrt'
	option realname 'USERNAME'

	# This adds support for channels in znc configuration:
	# list channel    '#chan optional_password'

	# list of allowed servers:
	# list server 	'chat.freenode.net 6667'
	list server 'irc.hackint.org 6667'

	# load user modules ('<module> [params...]'):
	# list module 'simple_away -timer 10 disconnected'
~~~

Anmerkung: Neuen Benutzer im System anlegen, ZNC für diesen Benutzer installieren und starten.

Start von ZNC nur als root!
~~~
znc -r
[ .. ] Checking for list of available modules...
[ >> ] ok
[ .. ] Opening config [/root/.znc/configs/znc.conf]...
[ >> ] ok
[ .. ] Binding to port [8067]...
[ >> ] ok
[ ** ] Loading user [Frank]
[ ** ] You are running ZNC as root! Don't do that! There are not many valid
[ ** ] reasons for this and it can, in theory, cause great damage!
[ ** ] You have been warned.
[ ** ] Hit CTRL+C now if you don't want to run ZNC as root.
[ ** ] ZNC will start in 30 seconds.
[ .. ] Forking into the background...
[ >> ] [pid: 31268]
[ ** ] ZNC 1.4 - http://znc.in
~~~

Die PID kann mit TOP angezeigt werden, da ZNC nicht gestoppt werden kann.
Anhalten mit kill 31268 also der aktuellen PID.

Zugriff auf ZNC per Browser. http://IP:Port bzw. http://[ipv6]:Port
Einen nackte graue Weboberfläche, das Modul webadmin wird nicht geladen.
Da das Webmodul und auch die anderen Module nicht geladen werden können,
also über das Konfigfile, Konfigmeü und manuell, bin ich dem Hinweis der 
ZNC Weboberfläche gefolgt, die nur dem Home und Logoff Button aufweist.

Per Irc Programm zum Server connecten und per Message die Webgui starten.
Dieses Vorgehen ist auch unter http://wiki.znc.in/Modules#.28Un.29Loading_Modules
beschrieben. 
/msg *status LoadMod webadmin
Jetzt steht die komplette Webmenüauswahl zur Verfügung. Alle installierten
Module werden unten in der Webübersicht angezeigt und können dort aktiviert werden.

http://wiki.znc.in/ZNC

Ein paar nütziche Module, die nicht fehlen sollten, falls nicht gleich mitinstalliert.
~~~
opkg update
opkg install znc-mod-webadmin znc-mod-log znc-mod-fail2ban znc-webskin-ice znc-mod-flooddetach
znc loadmod webadmin
znc loadmod controlpanel
znc loadmod webskin-ice
~~~

Mit dem Browser auf dem Router einloggen 'ipv6:1234' und über die Weboberfläche alle gewünschten Einstellungen vornehmen. Weitere Benutzer anlegen, Channels hinzufügen, rückwärtige Historie festlegen usw.

Hinweis: die Verbindung mit MIRC unter ipv6 auf den Bouncer funktioniert nicht. Hierzu einfach ein kleines Script im Scripteditor erstellen und beim Start ausführen.
Beispiel:
/znc connect user@password//ipv6:1234 /join #ffhb
TBE

