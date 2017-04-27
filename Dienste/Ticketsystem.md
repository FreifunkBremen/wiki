# [Ticketsystem](tasks.ffhb.de) (tasks.ffhb.de)
Wir nutzen ein Ticketsystem um alle aktuellen Vorgänge und Anfragen zu dokumentieren, zuzuorden und zuzuteilen. Dafür setzen wir auf [Phabricator](http://phabricator.org/). Es läuft unter dem Domain https://tasks.ffhb.de/.

## Zugang
Da unser Ticketsystem regelmäßig sensible Informationen wie zum Beispiel Kontaktdaten enthält, gewähren wir nur bekannten Freifunker Zugang zu diesem System. Typischerweise bedeutet das einen Freifunk-Knoten selber zu betreiben, auf der Mailingliste eingetragen zu sein und sich auf dem Treffen mal vorgestellt zu haben.  
Nicht alles muss zwingend erfüllt sein und wird von Situation zu Situation eingeschätzt.


## Anleitungen
### Benutzer / Frontend
#### Projekten beitreten und folgen
Alle eigenen, bereits beigetretenen Projekte finden sich in der Seitenleiste unter "[Projects](https://tasks.ffhb.de/project/)", alle öffentlichen Projekte lassen sich dann mit einem Klick auf "[All](https://tasks.ffhb.de/project/query/all/)" anzeigen.  
Dort wählt man ein Projekt aus, klickt es an und wählt aus der linken Seitenleiste den Punkt "Members" aus. Auf der sich öffnenden Seite kann man ganz rechts das/dem Projekt:
- **beobachten: "Watch"**  
  Beobachtet man ein Projekt, so wird man über alle Tasks, welche diesem Projekt zugeordnet werden, per Benachrichtigung im Browser und per E-Mail auf dem Laufenden gehalten.
- **beitreten: "Join"**  
  Ist man einem Projekt beigetreten, so wird es im "Projects"-Bereich von Phabricator, in der Standard-Ansicht "Joined", angezeigt für einen schnelleren Zugang zu diesem Projekt.

#### Seitenleiste anpassen
Auch wenn für neue Nutzer eine Standardauswahl an Applikationen für die Seitenleiste ausgewählt wurde, kann man es für seine eigenen Zwecke (für Admins zum Beispiel) anpassen:  
Um das Ticketsystem etwas leichter bedienbar zu gestalten und andere Bereiche und Tasks einfacher zu erreichen, lohnt sich ein Blick in den untersten Menüpunkt der linken Seitenleiste "[Customize Menu...](https://tasks.ffhb.de/settings/panel/home/)".  
Dort werden alle "Applications" angezeigt die an die Seitenleiste gerade "angepinnt" sind. Mit einem Klick auf das "X" dahinter lassen sie sich "entpinnen" und mit einem Klick auf "Pin Application" oben rechts, können neue hinzugefügt werden.

Eine Übersicht von Anwendungen findet man unter dem Seitenleisten-Punkt "[Applications](https://tasks.ffhb.de/applications/)".


### Admin / Backend
#### SSH Zugriff
Das Ticketsystem läuft auf `andromeda.hostedinspace.de` unter dem Benutzer `ffhb-tickets`.
Im Moment haben Zugriff:
* mortzu (Serverinhaber)
* ec8or
* ollibaba
* SimJoSt


#### Daemons neustarten
Um die Phabricator Daemons neuzustarten muss einmal der Befehl `phd-wrapper restart` ausgeführt werden.