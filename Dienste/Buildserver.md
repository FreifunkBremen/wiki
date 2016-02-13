# Buildserver
Von jplitza wurde eine VM gestellt, auf welcher die Firmware zentral gebaut werden kann.

## Anleitungen
### SSH Zugriff auf Screen
Mit dem Befehl `ssh ffhb@builder.jplitza.de -t screen -x` kann auf den Screen zugegriffen werden.  
Im Moment haben Zugriff:
* jplitza (Serverinhaber)
* corny
* Ollibaba
* SimJoSt

## Firewall
Der Server hat eine sehr restriktive Firewall und erlaubt nur die nötigsten Adressen zum Bauen von Gluon. Wenn beim Bauen wegen eines fehlerhaften Downloads ein Fehler auftritt, bitte Nachricht an jplitza zum Freischalten der entsprechenden Adresse.