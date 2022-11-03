Hier eine Aktualisierung zum Thema Flashen und Konfigurieren einer Freifunksoftware.
Im Herbst 2022 musten wir feststellen, das die FCC die Auflagen an Routerhersteller erhöht hat.
Es dürfen nur noch von den Herstellern signierte Images in den Router eingespielt werden.
Damit besteht auch das Problem, das ältere Firmware ebenfalls nicht mehr in einen Router eingespielt werden kann.

Momentan können wir nur sagen, Ausprobieren und uns Routermodel und Software melden. Evtl. haben wir eine Lösung.

## Inhalt

[[_TOC_]]

### 1.) Konfigurationsbeispiel mit virtuellem Image.
Um einen Router zu Konfigurieren verwende ich einen virtuellen Router in Form eines VMWare Inages. Zum Download wird auch ein Image als vdi angeboten. Ich verwende hier ""[gluon-ffhb-2019.1.3+bremen8-x86-64.vmdk](https://downloads.bremen.freifunk.net/firmware/stable/factory/gluon-ffhb-2019.1.3+bremen8-x86-64.vmdk)"" von unserem [Downloadserver](https://downloads.bremen.freifunk.net/firmware/).
Ich hab mir eine neu VM erstellt und eine zweite Netzwerkkarte hinzugefügt. Die bekommt die 192.168.1.1 zugewiesen, die Netzwerkkarte klemme ich auch ein Netzwerk mit 192.168.1.0. Mein Konfigurationspc ist auch eine VM, hier ist es mal Ubuntu. Der PC bekommt 192.168.1.2.
In die neue VM hänge ich mein Freifunkimage.vdmk als HDD ein und schon gehts los.

### 2.) Erster Start
Zunächst starte ich meine beiden VM's. Im Routerfenster sehe ich die Konsole des Routers.


<img src="https://cloud.ffhb.de/index.php/s/Tk7JoBLabGC4b4k/preview" width="500">

Konsole des Routers


Dann wird die Adresse des Bedien-PC geprüft. Hier gibt es viele Möglichkeiten.

<img src="https://cloud.ffhb.de/index.php/s/bZX3Q6yLXqd3fjs/preview" width="500">

### 3.) Hauptbildschirm / Willkommen! Seite
Dann starten wir unseren Browser und geben https://192.168.1.1 ein und schon wird der Startbildschirm angezeigt.

<img src="https://cloud.ffhb.de/index.php/s/cimbERfB6ebcfs5/preview" width="800">

Auf der Willkommen! Seite wird in der Kopfzeile die Softwareversion Angezeigt. Auf der rechten Seite ist Wizard hervorgehoben, dies ist der Knopf, der zu dieser Seite zurück führt. Daneben die Erweiterten Einstellungen. Bevor ihr Eingaben macht, erkundet bitte die Erweiterten Einstellungen.

Hinweis: Eingaben in den Erweiterten Einstellungen werden über den Speichern Button gespeichert. Es können alle Unterseiten einzeln gespeichert werden. Wird auf der Startseite gespeichert, so bootet der Router und geht aus dem Konfigmodus in den Produktivmodus. Es können keine weiteren Eingaben gemacht werden.

<img src="https://cloud.ffhb.de/index.php/s/rNfSSGXwy9eCF4z/preview" width="800">

In der unteren Hälfte der Willkommen Seite werden die Geodaten angegeben und Kontaktdaten wenn gewünscht.
Die Geodaten werden auf der Seite https://map.bremen.freifunk.net/#!/de/map über den PIN (rechts oben) auf der Karte gesetzt und in die Routerkonfiguration kopiert. Bei einigen SW Versionen ist an dieser Stelle auf dem Router eine Karte eingebaut.

<img src="https://cloud.ffhb.de/index.php/s/5XEaYPzKYgdaeBP/preview" width="800">

### 4.) Immer erst die Unterseiten durcharbeiten.

Imfolgenden die Unterseiten.
Die INFO Seite zeigt einige technische Daten des Routers.

<img src="https://cloud.ffhb.de/index.php/s/CSaB3D8sHCrNDnk/preview" width="800">
<img src="https://cloud.ffhb.de/index.php/s/bBAYN29Qgsws8nq/preview" width="800">
<img src="https://cloud.ffhb.de/index.php/s/9DoyQN4RrFs5YaZ/preview" width="800">
<img src="https://cloud.ffhb.de/index.php/s/eZzmCdfbeMnpbiK/preview" width="800">
<img src="https://cloud.ffhb.de/index.php/s/GJM8PdLJe793X2E/preview" width="800">
<img src="https://cloud.ffhb.de/index.php/s/PHoYEEHGL254LeE/preview" width="800">
<img src="https://cloud.ffhb.de/index.php/s/Z6BZxBbso9ngkA4/preview" width="800">
<img src="https://cloud.ffhb.de/index.php/s/tPqy9Lx9Qf6APBr/preview" width="800">
<img src="https://cloud.ffhb.de/index.php/s/RNmoMMsDGYtMXiK/preview" width="800">
<img src=" /preview" width="800">
<img src="https://cloud.ffhb.de/index.php/s/NpK55Y4CioYfWF8/preview" width="800">