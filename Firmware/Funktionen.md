# Funktionen
## Autoupdater
Der Autoupdater ermöglicht es bei erscheinen einer neuen Firmware automatisch auf diese upzudaten. Dies erfolgt generell Nachts zwischen 5 und 6 Uhr. Dabei wird überprüft, ob eine neue Firmware für den gewählten Branch verfügbar ist. Falls dies der Fall ist, wird, je nach Priorität im Manifest, die Firmware mit einer bestimmten Wahrscheinlichkeit geladen und installiert. Der Updater kann auch manuell ausgeführt werden und ein Update erzwungen werden.
## Mesh-on-LAN
Mesh-on-LAN ermöglicht es statt nur über WLAN, auch (oder ggf. nur) über Kabel zu meshen. Ist die Funktion angeschaltet, wird über die LAN-Ports des Geräts B.A.T.M.A.N. gesprochen und ein normaler Anschluss von Geräten (PCs zB) per NetzwerkKabel an den Freifunk-Knoten ist nicht mehr möglich.
## Mesh-on-WAN
Mesh-on-WAN ermöglicht es statt nur über WLAN, auch (oder ggf. nur) über Kabel zu meshen. Ist die Funktion angeschaltet, wird über den WAN-Port des Geräts B.A.T.M.A.N. gesprochen und ein normaler Anschluss von Geräten ans Freifunk-Netz, sowie Mesh-VPN ist nicht mehr möglich.
## Mesh-VPN
Ist Mesh-VPN aktiviert, stellt der Knoten über den WAN-Port eine verschlüsslte fastd-Verbindung zu den VPN-Servern auf. Dafür muss das Gerät entsprechend an das Internet angeschlossen werden.  
Diese Funktion ermöglicht es ihm, auch wenn keine WLAN-Verbindung besteht, sich zu anderen Knoten zu verbinden, sowie den Nutzern den Zugang ins Internet über die VPN-Server herzustellen.
### Bandbreitenbegrenzung
Die Bandbreitenbegrenzung ermöglicht es dem Knoten-Inhaber, die maximale Geschwindigkeit/Bandbreite, die der Knoten nutzen darf/soll, zu den VPN-Servern einzustellen. Dadurch soll verhindert werden, dass der Traffic des Knotens, den persönlichen Zugang ins Internet zu stark beeinträchtigt.
## Remotezugriff per SSH
Der Remotezugriff ermöglicht es Einstellungen am Knoten aus der Ferne vorzunehmen.
### SSH-Key
Die empfohlene Variante ist die Nutzung eines SSH-Keys, da sie deutlich sicherer ist. Dafür muss bei der erstmaligen Einrichtung in der Weboberfläche ein SSH-Public-Key hinterlegt und gespeichert werden.
### Kennwort
Es ist auch möglich eine SSH-Verbindung mit einem festgelegten Passwort herzustellen. Von dieser Möglichkeit wird aufgrund von schlechterer Sicherheit und Komfort jedoch abgeraten.