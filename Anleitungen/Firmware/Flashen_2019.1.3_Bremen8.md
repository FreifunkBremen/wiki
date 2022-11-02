Hier eine Aktualisierung zum Thema Flashen und Konfigurieren einer Freifunksoftware.
Im Herbst 2022 musten wir feststellen, das die FCC die Auflagen an Routerhersteller erhöht hat.
Es dürfen nur noch von den Herstellern signierte Images in den Router eingespielt werden.
Damit besteht auch das Problem, das ältere Firmware ebenfalls nicht mehr in einen Router eingespielt werden kann.

Momentan können wir nur sagen, Ausprobieren und uns Routermodel und Software melden. Evtl. haben wir eine Lösung.

## Inhalt

[[_TOC_]]

### 1.) Konfigurationsbeispiel mit virtuellem Image.
Um einen Router zu Konfigurieren verwende ich einen virtuellen Router in Form eines VMWare Inages. Zum Download wird auch ein Image als vdi angeboten.
Ich hab mir eine neu VM erstellt und eine zweite Netzwerkkarte hinzugefügt. Die bekommt die 192.168.1.1 zugewiesen, die Netzwerkkarte klemme ich auch ein Netzwerk mit 192.168.1.0. Mein Konfigurationspc ist auch eine VM, hier ist es mal Ubuntu. Der PC bekommt 192.168.1.2.
In die neue VM hänge ich mein Freifunkimage.vdmk als HDD ein und schon gehts los.

### 2.) Erster Start
Zunächst starte ich meine beiden VM's. Im Routerfenster sehe ich die Konsole des Routers.


<img src="https://cloud.ffhb.de/index.php/s/Tk7JoBLabGC4b4k/preview" width="500">
Konsole des Routers


Dann wird die Adresse des Bedien-PC geprüft. Hier gibt es viele Möglichkeiten.

<img src="https://cloud.ffhb.de/index.php/s/bZX3Q6yLXqd3fjs/preview" width="500">

gluon-ffhb-2019.1.3+bremen8-

<img src=" /preview" width="500">
<img src=" /preview" width="500">
<img src=" /preview" width="500">
<img src=" /preview" width="500">