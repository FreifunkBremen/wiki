# Buildserver
Von jplitza wurde eine VM gestellt, auf welcher die Firmware zentral gebaut werden kann.

## Anleitungen
Bei einem normalen SSH-Login wird automatisch eine tmux-Session gestartet bzw. einer laufenden tmux-Session wird beigetreten. Dadurch können mehrere Personen gleichzeitig die selben Ausgaben beobachten und man kann sich mit `Strg-A D` ausloggen ohne einen laufenden Build-Prozess abzubrechen.
  
Im Moment haben Zugriff:
* jplitza (Serverinhaber)
* corny
* Ollibaba
* SimJoSt

## Firewall
Der Server hat eine sehr restriktive Firewall und erlaubt nur die nötigsten Adressen zum Bauen von Gluon. Wenn beim Bauen wegen eines fehlerhaften Downloads ein Fehler auftritt, bitte Nachricht an jplitza zum Freischalten der entsprechenden Adresse.