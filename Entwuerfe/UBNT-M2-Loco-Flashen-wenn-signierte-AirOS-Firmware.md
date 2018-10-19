Wenn auf der UBNT eine signierte Firmware installiert ist (= dann sind keine upgrades bzw. downgrades auf unsigned Versionen möglich - erkennbar an entsprechender Fehlermeldung beim Firmware-Upload), dann folgende Schritte gehen:

1.) Auf die folgende beta-Version der AirOS-Firmware installieren  (Hintergrund: Diese Firmware akzeptiert auch unsigned-Updates)
https://www.ubnt.com/downloads/XN-fw-internal/v6.0.6/XM.v6.0.6-beta.30875.170526.0038.bin

2.) Auf die (unsigned!!!) Version 6.0.4 downgraden
https://dl.ubnt.com/firmwares/XN-fw/v6.0.4/XM.v6.0.4.30805.170505.1525.bin

3.) Firmware von Freifunk Bremen installieren:
https://downloads.bremen.freifunk.net/firmware/stable/factory/gluon-ffhb-2017.1.8+bremen1-ubiquiti-nanostation-loco-m2.bin

Fertig :-)