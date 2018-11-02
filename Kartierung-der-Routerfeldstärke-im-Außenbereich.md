### Übersicht

Die folgende Anleitung ist für die Nutzer gedacht, die die Feldstärkeverteilung ihres Routersignals im Außenbereich messen und aufzeichnen möchten.

### Voraussetzungen
* Outdoor-Router (dessen Feldstärke vermessen werden soll)
* Smartphone mit Anzeige der WLAN-Feldstärke (von mir verwendet wurde die App „WiFi Analyzer“)
* Open Street Map (z. B. von freifunk.bremen.net)
* Programm zur Umrechnung der Daten (z. B. Matlab bzw. das von mir verwendete Open Source-Programm „GNU Octave“)


### Durchführung der Messung
Optimal wäre eine App, die die Feldstärke zusammen mit der Position aufzeichnet. Leider habe ich keine entsprechende Anwendung gefunden (die App „WiFi Heatmap“ verspricht zwar genau das, angeblich aufgezeichnete Daten sind jedoch nicht zu finden). Also händisch vorgehen:

* zu vermessendes Gebiet mit Smartphone und Papierausdruck der Karte abgehen
* an strategisch verteilten Punkten Messung vornehmen, Punkt und Meßwert in Karte eintragen
* Anzahl der Meßpunkte: soviel wie möglich, mindestens ca. 50...100, besser mehr


### Übertragung der Meßwerte

Mit Hilfe der Karte von bremen.freifunk.net werden jedem Meßpunkt seine Koordinaten zugewiesen und ggf. mit einem Editor in eine Datei geschrieben, und zwar nach Longitude und Latitude getrennt, also:   
lon1; lon2; lon3;...lonn   
lat1; lat2; lat3;....latn   
ebenso die Meßwerte:   
fs1; fs2; fs3;.....fsn


### Berechnung des Potentialfeldes
Jetzt müssen die Daten als Matrix verarbeitet werden. Die entsprechenden Befehlsfolge in Octave (bzw. Matlab):
* Longitude-Daten der Matrix lom zuweisen (einlesen aus Datei oder copy/paste eingeben):  
lom = [lon1; lon2; lon3; ...lonn];
* Latitude-Daten der Matrix lam zuweisen:  
lam = [lat1; lat2; lat3; ....latn];
* ebenso Meßwerte:   
fsm = [fs1; fs2; fs3; ….fsn];

Anschließend wird ein Gitternetz erzeugt, das das vermessene Feld einschließt, z. B. :   
[Lon,Lat] = meshgrid(8.795:0.00005:8.802,53.067:0.00005:53.071);

Die Meßdaten werden interpoliert und den Gitternetzwerten zugewiesen:   
Fieldstrength = griddata(lom,lam,fsm,Lon,Lat);

Die Potentiallinien werden zugewiesen (hier von -90 dBm bis -40 dBm) und gezeichnet:   
[C,fs]=contour(Lon,Lat,Fieldstrength,-90:5:-40);

Schließlich können die Potentiallinien mit Werten versehen werden:
clabel(C,'FontSize',12); 

Die erzeugte Grafik kann, falls gewünscht, mit einem (Vektor-)Grafikprogramm über den entsprechenden Kartenausschnitt gelegt werden, das Ergebnis könnte dann so aussehen:


  



 