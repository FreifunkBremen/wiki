Nette Anleitung von Freifunk Magdeburg 
CC BY-SA 4.0 2016 Freifunk Magdeburg 

Aktualisierung abgeschlossen am 26.6.2020

## Flashen von Ubiquiti Routern


### Kompatible Geräte

- [Ubiquiti Bullet M2](https://www.ubnt.com/airmax/bulletm/)
- [Ubiquiti Nanostation Loco M2 XM](https://www.ubnt.com/airmax/nanostationm/)
- [Ubiquiti Nanostation Loco M5 XM](https://www.ubnt.com/airmax/nanostationm/)
- [Ubiquiti Nanostation Loco M2 XW](https://www.ubnt.com/airmax/nanostationm/)
- [Ubiquiti Nanostation Loco M5 XW](https://www.ubnt.com/airmax/nanostationm/)
- [Ubiquiti Nanostation M2 XM](https://www.ubnt.com/airmax/nanostationm/)
- [Ubiquiti Nanostation M5 XM](https://www.ubnt.com/airmax/nanostationm/)
- [Ubiquiti Nanostation M2 XW](https://www.ubnt.com/airmax/nanostationm/)
- [Ubiquiti Nanostation M5 XW](https://www.ubnt.com/airmax/nanostationm/)
- [Ubiquiti Picostation M2 - nicht mehr erhältlich](https://www.netwifiworks.com/PicoStation-M.asp)
- [Ubiquiti Picostation M5 - nicht mehr erhältlich](https://www.netwifiworks.com/PicoStation-M.asp)
- [Ubiquiti Rocket M2](https://www.ubnt.com/airmax/rocketm/)
- [Ubiquiti Rocket M5](https://www.ubnt.com/airmax/rocketm/) **Betrieb seit 17. Juni 2020 durch BNetzA verboten!**
- [Ubiquiti Unifi AP](https://www.ubnt.com/unifi/unifi-ap/)
- [Ubiquiti Unifi AP LR](https://www.ubnt.com/unifi/unifi-ap/)
- [Ubiquiti Unifi AP Pro](https://www.ubnt.com/unifi/unifi-ap/)
- [Ubiquiti Unifi AP Outdoor](https://www.ubnt.com/unifi/unifi-ap/)

### Schritt 1: Einloggen in das UBNT Gerät

    Netzwerkeinstellungen des Rechners konfigurieren wie folgt:
        IP Adresse: 192.168.1.21
        Subnetzmaske: 255.255.255.0
    anschließend das UBNT Gerät mit dem Rechner verbinden

(Achtung: nicht das Netzwerkkabel des Rechners in den PoE Port des UBNT Gerätes verbinden)

Browser öffnen und folgende IP Adresse eingeben: [http://192.168.1.20](http://192.168.1.20/)
Auf der Startseite gibt man dem Gerät zuerst Benuternamen und ein password, default werte sind:
- User: ubnt
- Password: ubnt

<img src="https://cloud.ffhb.de/index.php/s/epc3T9HLdp7kNzb/preview"  alt="UBNT Router GUI, Logon Screen" width="600">

### Schritt 2: Auswählen der richtigen Firmware

Auf der Seite "Main" sieht man nun die Bezeichnung des Gerätes und auch die verwendete Hardwareversion sowie die aktuelle Firmwareversion. In unserem Beispiel:

- Model: Nanostation Loco M5
- Hardwareversion: XW (steht in Klammern hinter der Firmware)
- Firmwareversion: v.5.62 (XW)

<img src="https://cloud.ffhb.de/index.php/s/mfBxdP9MfxAPCwM/preview" alt="UBNT Router GUI, Main Screen" width="600">

Die Hardwareversion des Gerätes befindet sich i.d.R. **nicht** auf der Verpackung, sondern ist nur direkt in der Weboberfläche erkennbar.

### Schritt 2a: Downgrad der AirOS Firmware

(Nutzer der Firmware 0.37 können diesen Schritt 2a direkt überspringen)

Bei Ubiquiti mit der Firmware AirOS XM.v5.6.X / XW.v5.6.X (oder neuer) kommt es zu Komplikationen. Ein direktes Einspielen der Freifunk Firmware ist **NICHT MÖGLICH**. Es ist notwendig, bevor man die Freifunk Firmware oder OpenWRT aufspielt, zuerst ein Firmwaredowngrade auf die Version AirOS **XM.v5.5.X** oder **XW.v5.5.X** durchzuführen. Ohne diesen Firmwaredowngrade WIRD DAS GERÄT NICHT BOOTEN!

Wenn dein Ubiquiti aktuell AirOS XM.v5.5.X oder AirOS XW.v5.5.X als Firmware verwendet, folge bitte diese Anleitung direkt ab dem Schritt 2b.

Je nach Hardwareversion deines Gerätes musst du nun die Firmware AirOS XM.v5.5.X oder AirOS XW.v5.5.X downloaden von der Herstellerseite.

- Download der Passenden Firmware AirOS XM.v5.5.X
 - Download AirOS XM.v5.5.10-u2.28005.150723.1358.bin for: AG-HP-2G16, AG-HP-5G23, AG-HP-5G27, AirGrid M2, AirGrid M5, AR, AR-HP, BM2HP, BM2-Ti, BM5HP, BM5-Ti, LiteStation M5, locoM2, locoM5, locoM9, M2, M3, M365, M5, M900, NB-2G18, NB-5G25, NBM3, NBM365, NBM9, NS2, NSM3, NSM365, NSM5, PBM10, PBM3, PBM5, Power AP N
 - Download AirOS XW.v5.5.10-u2.28005.150723.1358.bin, for: AG-HP-2G16, AG-HP-2G20, AG-HP-5G23, AG-HP-5G27, AirGrid M, AirGrid M2, AirGrid M5, locoM2, locoM5, locoM9, M2, M3, M365, M5, M900, NBE-M2-13, NBE-M5-16, NBE-M5-19, NSM2, NSM3, NSM365, NSM5, PBM3, PBM365, PBM5, RM2-Ti, RM5-Ti

Nachdem du die Firmware auf deiner Festplatte gespeichert hast, gehe nun zur Seite "System" und klicke auf den Buttom "Datei auswählen" oben rechts.

<img src="https://cloud.ffhb.de/index.php/s/Qyt7djoA4fEiQGd/preview" alt="UBNT Router GUI, System Tag" width="600">


Hier wählst du nun das passende Image für dein Gerät aus, im Beispiel "AirOS XW.v5.5.10-u2.28005.150723.1358.bin"

<img src="https://cloud.ffhb.de/index.php/s/TWwRDE7Zkpsiaj4/preview" alt="UBNT Router GUI, Imageauswahl" width="600">

Anschließend musst du für das Downgrade der Firmware auf AirOS XM.v5.5.X / AirOS XW.v5.5.X auf den Button "Absenden" klicken.

<img src="https://cloud.ffhb.de/index.php/s/rGsiRD28aXb5YpH/preview" alt="UBNT Router GUI, Image senden" width="600">

Jetzt wird die Firmware von deinem PC auf das UBNT Gerät geladen.

<img src="https://cloud.ffhb.de/index.php/s/KTrpMJP2EdzyfEL/preview" alt="UBNT Router GUI, Uploading" width="600">

Mit dem klicken auf "Update" wird nun die Fireware geladen.

<img src="https://cloud.ffhb.de/index.php/s/FRWgdxJGbyk9TLq/preview" alt="UBNT Router GUI, Update Button" width="600">

Der Updatevorgang dauert in der Regel 1-2 Minuten.

<img src="https://cloud.ffhb.de/index.php/s/FatYoL4jjWM7JPH/preview" alt="UBNT Router GUI, Updating" width="600">

### Schritt 2b: Einspielen der Freifunk Firmware

Wie bereits in Schritt 1 beschrieben musst du dich nach dem Eingeben der Logindaten unter der http://192.168.1.20 anmelden.

<img src="https://cloud.ffhb.de/index.php/s/q99ygopAEZ4CLxM/preview" alt="UBNT Router GUI, Login" width="600">

Auf der Seite "System" sieht man nun die Bezeichnung des Gerätes und auch die verwendete Hardwareversion sowie die aktuelle Firmwareversion. In unserem Beispiel:

 - Model: Nanostation Loco M5
 - Hardwareversion: XW (steht in Klammern hinter der Firmware)
 - FirmwareversioN: v.5.5.10 (XW)

Mit dem oben rechts kann man nun die Freifunk-Firmware mit dem Button "Datei auswählen" hochladen.

Bitte beachte die Hardwareversion der Geräte. XM ist die Normale. Die passende Firmware findest du unter https://downloads.bremen.freifunk.net/firmware/stable/factory/.

<img src="https://cloud.ffhb.de/index.php/s/TEEHHmYJqdBaMzF/preview" alt="UBNT Router GUI, Hardwareversion" width="600">

Hier wählst du nun das passende Image für dein Gerät aus, als Beispiel "gluon-ffhb-2019.1.1+bremen3-ubiquiti-nanostation-loco-m5-xw.bin" für unsere Nanostation Loco M5 (XW).

<img src="https://cloud.ffhb.de/index.php/s/dr6MxwwTPcZFsjn/preview" alt="UBNT Router GUI, Imageselektion" width="600">

Jetzt wird die Firmware von deinem PC auf das UBNT Gerät geladen.

<img src="https://cloud.ffhb.de/index.php/s/QJJ9wrF6zPXcwb4/preview" alt="UBNT Router GUI, Firmware runterladen" width="600">

Anschließend muss man mit dem klick auf "Update" das Einspielen der Freifunk Firmware bestätigen.

<img src="https://cloud.ffhb.de/index.php/s/ACnk786tFbrAbLi/preview" alt="UBNT Router GUI, Firmware bestaetigen" width="600">


Der Updatevorgang dauert in der Regel 1-2 Minuten.

<img src="https://cloud.ffhb.de/index.php/s/B7jRibFPQWEH9LW/preview" alt="UBNT Router GUI, Firmware aufspielen" width="600">

### Schritt 3: Knoten konfigurieren

Nachdem die Freifunk Firmware erfolgreich eingespielt wurde, musst du nun deinen Freifunk Knoten konfigurieren.

