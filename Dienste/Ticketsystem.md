# Ticketsystem - tasks.ffhb.de
Wir nutzen ein Ticketsystem um alle aktuellen Vorgänge und Anfragen zu dokumentieren, zuzuorden und zuzuteilen. Dafür setzen wir auf [Phabricator](http://phabricator.org/). Es läuft unter dem Domain https://tasks.ffhb.de/.

## Anleitungen

### Benutzer / Frontend



### Admin / Backend

#### SSH Zugriff
Das Ticketsystem läuft auf `andromeda.hostedinspace.de` unter dem Benutzer `ffhb-tickets`.
Im Moment haben Zugriff:
* mortzu (Serverinhaber)
* ec8or
* SimJoSt


#### Daemons neustarten
Um die Phabricator Daemons neuzustarten muss einmal der Befehl `phd-wrapper restart` ausgeführt werden.