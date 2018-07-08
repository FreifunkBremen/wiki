Anleitung – WinSCP gespeicherte Sitzungen sichern

[WinSCP](https://winscp.net/eng/index.php) ist ein freier SFTP, SCP und FTP Client für Windows


Hier eine kurze Anleitung zum sichern und einspielen seiner gespeicherten WinSCP Sitzungen, die normalerweise in der Regisrtry gespeichert sind.
Die WinSCP Verbindungen können auch in eine Datei ausgelagert werden. Diese kann dann auch auf einem anderen Rechner kopiert werden.

Öffnet euer WinSCP und baut irgendeine Verbindung auf. Geht in Einstellungen und nochmals auf Einstellungen (Strg-Alt-P)
Auf der linken Seite auf Speicher, Speicherort für Konfiguration auf „INI Datei (WinSCP.ini) stellen und WinSCP schließen.
Diese sollte sich jetzt in folgendem Ordner befinden: „﻿C:\Users\name\AppData\Local\VirtualStore\Program Files (x86)\WinSCP\“
WinSCP.ini sichern. Andere Orte sind auch möglich, je nach eigenem Bedarf.
Auf eurem neuen Rechner müsst Ihr nach der WinSCP installation auch erstmal eine Verbindung aufbauen und dieses Anhand der Anleitung auf WinSCP.ini umstellen.

![Bild: WinSCP-Einstellungen](https://cloud.ffhb.de/index.php/s/o5NFGZwYC24WBSR/download)

Jetzt nur noch die neue leere WinSCP.ini gegen die bereits gesicherte ersetzen. Natürlich kann ein Umzug/Backup auch aus der Registry gemacht werden, exportiere aus regedit.exe heraus
HKEY_CURRENT_USER\Software\Martin Prikryl\WinSCP 2\Sessions\

Anmerkung zum Export/Import auf unterschiedlichen Rechnern und SSH Schlüsseln.
Damit importierte Konfiguration funktionieren, ist für die Schlüssel der gleiche Ablageort zu wählen. Beispiel: C:\.SSH
Die Fehlermeldung für lokale Verzeichnisse nur mit ok Bestätigen.
Sollen nur einzelne Sessions exportiert werden, belasse die WinSCP Konfiguration auf Registry und exportiere aus
HKEY_CURRENT_USER\Software\Martin Prikryl\WinSCP 2\Sessions\
nur die gewünschte Session. Weitere Infos unter [WinSCP-Dokumentation](https://winscp.net/eng/docs/config)
