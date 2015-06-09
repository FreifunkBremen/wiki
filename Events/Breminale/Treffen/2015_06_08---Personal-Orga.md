# Drittes Breminale-Orgatreffen
## Aktueller Status
* Anschluss - Uplink zu Router
* Stand
  * 3 Meter Bühne

## Umsetzung
### Personal
* **Wer kann wann**  
  https://dudle.hackerspace-bremen.de/FFHB-Breminale/  
  http://wiki.bremen.freifunk.net/Events/Breminale/Termine#termine_zeitplanung-während-des-events
* **Aufbau**  
  Wer? Was? (Wir müssen Kabel verlegen?)
* **Standbesetzung/Stand**  
  Wer Wann? Wie soll der Stand aussehen?
* **Abbau**  
  Wer? Was? Wo Lagern wir das Kabel?
* **Technik**  
  Status? Ideen? Testaufbau?
* **Sonstiges**

### Netzwerk
* Anschluss - Uplink zu Router
* Kabel Cat

### Stand
 * 3 Meter Bühne - Meinung?


### Himmlische Wiese

### Aufsteller

### Spendenbox


## Protokoll
* Stand 
  Gerne an 3 Meter Bühne
* Personal
  * Wer kann wann  
    Dudle wird erweitert und Teilnahme erzwungen
* Aufbau  
  * vorher schon Plan haben
  * einen Chef vor Ort  
    mit Plan und bereits erledigten Aufgaben, welcher koordiniert


### Varianten
Verkabelung entlang der Stromkabel (ursprünglicher/aktueller Aufbauplan) wirft Probleme auf, durchgerechnet von Nebirosh, deswegen Brainstorming von Varianten mit pro und contra

#### Variante 1 - Netzwerkabel am Starkstrom entlang
##### Untervarianten
1. **Patch-Kabel an Starkstromkabeln entlang, Switching von Nodes in Stromverteilern (aktueller Plan)**
2. **gleich, aber mit RJ45-Doppeldaten-Dosen an jedem Node der weiterreicht**  
(funktioniert wahrscheinlich)  
Erdung über die Schirmung, welche in der Dose angelegt wird, also Erde durch die Schirmung aller Patch-Kabel durchgereicht vom Patchpanel

##### Probleme  
* Potentialausgleich (1.)  
* Brummen  
* Kabelpreis  
* Dosenpreis (2.)
* Arbeitsaufwand (Krimpen...)  
* Strom für Node im Stromkasten?  

##### Vorteile
* Geschwindigkeit  
* "Stabilität"  
* kein Potentialausgleich (2.)


#### Variante 2
##### Untervarianten
1. **Kupfer durch die Bäume + Nanos**  
die Nanos strahlen vom Deich runter auf die Breminale
2. **Funk durch die Bäume + Nanos**  
statt Kabel wird Richtfunk durch die Bäume verwendet

##### Probleme
* Potentialausgleich (1.)  
* Genehmigung  
* Bäume  
  * Arbeit  
  * Dämpfung  
* Abdeckung nicht gesichert  
* Überlastung der "Nodes"  
* Strom  

##### Vorteile
* kein Brummen  
* kein Potentialausgleich (2.)  


#### Variante 3 - Insellösung (3-4 Inseln
Die einzelnen Inseln werden mit Richtfunk angesprochen.  
Damit der Potentialausgleich nicht wieder ein Problem ist, werden alle Nodes stern-verkabelt von einem geerdeten Patchpanel aus.


#### Variante 4 - kleinere Inseln (zwischen 2 Zelten 2 Inseln)
Die einzelnen Inseln werden mit Richtfunk angesprochen.  
Nodes untereinander verbunden mit
1. WLAN-Meshing
2. Patch-Kabel

##### Probleme  
* evtl. Potentialausgleich (2.)(da unteschiedlich starke Verbraucher, obwohl Strom für Nodes vom gleiche Stromkreis)  
* Brummen (2.)(minimal, da nur kurze Strecken und nicht entlang von starken Stromleitungen)  
* Arbeitsaufwand (Aufbau erst bei aufgebauten Ständen)  
* reduzierter Durchsatz (2.)
* Richtfunk muss eingerichtet werden

##### Vorteile
* kein Potentialausgleich (1.)
* kein Brummen (1.)
* keine Kabelverlegung
  * reduzierter Arbeitsaufwand
  * Ausfallrate wegen Kabeldefekt reduziert