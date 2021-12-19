Es gibt wieder ein neues Spielzeug aus der der Raspberry Reihe, den Zero 2W.

[[TOC]]

### Was ist neu?

Der Zero2W hat nun 4 Kerne und ist quasi ein Pi 3B+ mit 512Mb statt 1Gb.
Die Einschränkung des Speichers auf 512 Mb ist auch sein größter Schwachpunkt.
Alles was Grafik verwendet hat ein Problem mit 512 Mb.
Die 32 Bit Version ist Teilweise darauf abgestimmt, die 64 Bit Version (aktuell noch nicht vorgesehen) hat da echte Probleme mit 512Mb.
Die 64 Bit Version kann ich installieren, wenn ich im Anschluß des Schreibens auf der SD Karte die Datei bcm2710-rpi-3-b.dtb im Bootfolder
zu bcm2710-rpi-zero-2.dtb kopiere.
VLC muss deinstalliert werden, da es die Upgrades behindert. Firefox und Chrome funktionieren nicht.
64 Bit lohnt hier noch nicht.

### Probleme
Bisher funktionieren nur max. 32Gb SD Karten.
Mirco Schalter an der SD Karte wackelt manchmal. 
