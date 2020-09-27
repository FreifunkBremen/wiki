Wir bauen eine Freifunkrouter mit einem Raspberry-Zero-W. Der Zero-W hat WLAN :-)

[[_TOC_]]

### Teile-Liste

Die hier angegebenen Links dienen nur als Beispiel und sind meine persönliche Empfehlung. Viele Teile befinden sich normalerweise bereits im Fundus eine Raspi-Bastlers.
- [Zero-W oder WH](https://www.reichelt.de/de/de/raspberry-pi-zero-wh-v-1-1-1-ghz-512-mb-ram-wlan-bt-rasp-pi-zero-wh-p222531.html?&trstct=pos_1&nbc=1)
- [Micro-SD ab 300Mb](https://www.reichelt.de/microsdhc-speicherkarte-32gb-sandisk-mit-adapter-sdsdqm032gb35a-p196654.html?&trstct=pos_7&nbc=1)
- [Netzteil](https://www.reichelt.de/raspberry-pi-netzteil-5-v-2-5-a-micro-usb-schwarz-rasp-nt-25-sw-e-p240934.html?search=raspberry+netzteil)
- [Serielles Interface](https://www.reichelt.de/raspberry-pi-usb-zu-ttl-0-9-m-pl2303hx-rpi-usb-ttl-p150567.html?&trstct=pos_7&nbc=1) oder
  - [LAN-USB-HAT]([https://www.amazon.de/Waveshare-USB-HUB-HAT-Connection/dp/B07T35X4P4/ref=sr_1_9?__mk_de_DE=%C3%85M%C3%85%C5%BD%C3%95%C3%91&dchild=1&keywords=Netzwerkkarte+raspberry+zero+hat&qid=1601205083&quartzVehicle=3443-316&replacementKeywords=netzwerkkarte+raspberry+hat&sr=8-9) oder
  - [LAN-USB-Peitsche](https://www.amazon.de/Micro-Fast-Ethernet-Netzwerkkonverter-Port/dp/B071HS1TF6/ref=sr_1_7?__mk_de_DE=%C3%85M%C3%85%C5%BD%C3%95%C3%91&dchild=1&keywords=Netzwerkkarte+micro+usb+zero&qid=1601204957&quartzVehicle=3443-316&replacementKeywords=netzwerkkarte+micro+usb&sr=8-7)
  - [LAN-Kabel](https://www.reichelt.de/cat-6a-slim-patchkabel-u-ftp-1-5-m-gelb-slim-s6a-1-5-ge-p264786.html?&trstct=pos_9&nbc=1)
- DiskImager z.B. [Win32DiskImager](https://sourceforge.net/projects/win32diskimager/)
- PartedMagic oder Gparted
- ggf. [Gehäuse](https://www.reichelt.de/gehaeuse-fuer-raspberry-pi-zero-transparent-rpiz-case-tr-p223609.html?&trstct=pos_4&nbc=1) 
- ggf. Maus und Tastatur, sowie Monitor und [Micro-HDMI Kabel](https://www.reichelt.de/hdmi-a-stecker-hdmi-micro-d-stecker-4k-2-0-m-delock-84783-p167187.html?&trstct=pos_4&nbc=1) 

### Image vorbereiten
Von der [Freifunk-Imageseite](https://downloads.bremen.freifunk.net/firmware/) die Firmware herunterladen und entpacken. Das Image wird dann mit einem Imager auf die Mico-SD geschrieben. Ggf. mit einem geeigneten Tool die Partitionsgröße anpassen oder den restlichen Speicherplatz partitionieren und später mounten. 
Den leeren Speicherplatz später zu mounten ist der bessere Weg, da nauch einem Sysupgrade eine erweiterte Karte verloren geht.

Speicherkarte in den Zero stecken, Zubehör anstöpseln und booten lassen.

### Konfiguration
Solange der Zero nicht konfiguriert ist, Funkt er nicht. Der Zugang erfolgt über die serielle Schnittstelle oder über ein angeschlossenes LAN-Interface. Wenn der Zero eher voll verkabelt ist, also Maus Monitor Tastatur, kann er auch darüber konfiguriert werden.
ICh beschränke mich hier auf Seriell, WEB-Interface und SSH.

