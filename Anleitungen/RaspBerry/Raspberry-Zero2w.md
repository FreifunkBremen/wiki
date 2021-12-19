Es gibt wieder ein neues Spielzeug aus der der Raspberry Reihe, den Zero 2W.

[[_TOC_]]

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

* Bisher funktionieren nur max. 32Gb SD Karten.
* Mirco Schalter an der SD Karte wackelt manchmal. 
* 

### Ocerclocking

Übertakten geht gut, mach mehr Bumms, ist ja der gleiche Chip wie beim 3B+
~~~
sudo nano /boot/config.txt
~~~

~~~
# Add your lines at the end of the config.txt file.
# this is an example.
arm_freq=1300
gpu_freq=500
sdram_freq=500
over_voltage_sdram=3
# over_voltage is done by the governor.
# set the parameter to overrule its moderate choice.
over_voltage=5
~~~

Ctrl+X, Y, Enter to save the session

Reboot to run at the new clock frequency

~~~
$ sudo reboot
~~~

