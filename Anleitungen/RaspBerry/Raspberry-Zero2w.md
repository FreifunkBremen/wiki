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

* 512Mb Begrenzung zerlegt gafische Anwendungen, Chrome, Firefox, Youtube ...
* Bisher funktionieren nur max. 32Gb SD Karten.
* Mirco Schalter an der SD Karte wackelt manchmal. 
* Showstopper: Buster 64Bit. Faktor 10 langsamer, läuft nicht gut.

### Overclocking

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

Überprüfen:
~~~
pi@ZERO-2:~ $ vcgencmd get_config int
~~~
~~~
aphy_params_current=819
arm_freq=1300
arm_freq_min=600
audio_pwm_mode=514
avoid_warnings=2
camera_auto_detect=1
config_hdmi_boost=5
desired_osc_freq=0x331df0
disable_commandline_tags=2
disable_l2cache=1
display_auto_detect=1
display_hdmi_rotate=-1
display_lcd_rotate=-1
dphy_params_current=1091
dvfs=3
enable_tvout=1
enable_uart=1
force_eeprom_read=1
force_pwm_open=1
framebuffer_ignore_alpha=1
framebuffer_swap=1
gpu_freq=500
ignore_lcd=1
init_uart_clock=0x2dc6c00
mask_gpu_interrupt0=3072
mask_gpu_interrupt1=26370
max_framebuffers=2
over_voltage=5
over_voltage_avs=62500
over_voltage_sdram=3
pause_burst_frames=1
program_serial_random=1
sdram_freq=500
sdram_schmoo=0x2000020
total_mem=512
hdmi_force_cec_address:0=65535
hdmi_force_cec_address:1=65535
hdmi_pixel_freq_limit:0=0x9a7ec80
~~~
pi@ZERO-2:~ $


### Swap
Auslagerungsdatei vergrößern. Aber nur wenn es notwendig ist.
Die Standardauslagerungsgröße beträgt 100 MB. Das ist nicht genug, um die Webbrowser zufrieden zu stellen. Wir werden sie auf 2 GB erhöhen.

1.) Schalte den Swap vorübergehend aus:
    sudo dphys-swapfile swapoff

2.) Bearbeite nun /etc/dphys-swapfile
    sudo nano /etc/dphys-swapfile
    suche nach CONF_SWAPSIZE=100 neuer Wert
    CONF_SWAPSIZE=2048 in Zeile 16 von 26

3.) Speichern und beenden (Strg + O, Enter, Strg + X) oder (Strg + X), Y, Enter

4.) Wieder Einschalten
    sudo dphys-swapfile setup
    sudo dphys-swapfile swapon

Ein Neustart ist nicht erforderlich. Jetzt sollte Chromium mit mehreren Tabs besser funktionieren.

