# Anleitung zur Erweiterung des Freifunknetzes mit Richtfunk

Exemplarisch wird hier beschrieben, wie man das Freifunk-Netz bei Cafe-Sand mit Richtfunkantennen erweitern kann.

### Auswahl der Hardware
Wenn du dich dazu entscheidest beim Freifunk mitzumachen, hast du anfangs die Qual der Wbahl beim Aussuchen der Hardware. 
Welche Firmware-Version gerade aktuell ist und welche Router sie unterstützt, findest du hier: [[/Firmware/Changelog]]
Eine gute Übersichtseite mit vielen Informationen findet sich auch im Wiki von freifunk.net: http://wiki.freifunk.net/Freifunk_Firmware_Gluon/Hardware

Es ist unbedingt darauf zu achten, dass man die gleiche Frequenz nutzt, wie die Geräte, mit denen man verbinden möchte. Im Falle des Cafe-Sand: 2.4GHz  (Also die Geräte, die eine "2" im Namen tragen: CPE210, Nanostation M2, etc).

### Firmware auf das Gerät laden
Das Einrichten der Antenne erfolgt im wesentlichen wie das Einrichten eines normalen Frefunk-Routers ("flashen" genannt.)
Der Vorgang wird auf folgender Seite gut erklärt: 
[Anleitung zum Flashen](https://wiki.bremen.freifunk.net/Anleitungen/Firmware/Flashen)


### Gerät anbringen
Beim Anbringen der Geräte sind folgende Punkte wichtig/bemerkenswert: 
* PoE: Die meisten Richtunkgeräte beziehehn sowohl Strom, als auch Daten über 1 Kabel. Diese Technik heißt "Power over Ethernet - PoE". Man muss also nur 1 Kabel zum Gerät verlegen. Idealerweise nutzt man hier Flachbandkabel, um keine Löcher bohren zu müssen. 
Erläuterungsbild aus dem Freifunk-Forum:
https://forum.freifunk.net/uploads/default/optimized/2X/5/5eb20f201a2664b6fd26582567f2ecb81b78536a_1_666x500.jpg

* Öffnungswinkel: Die meisten handelsüblichen Richtfunk-Geräte haben einen Öffnungswinkel von 60 Grad, man muss also nicht so genau darauf achten, dass die Gegenstelle optimal angepeilt wird. Mehr Details gibts im Freifunk-Forum.

* Anbring-Ort: Die meisten Richtfunk-Geräte sind auf der Rückseite so geformt, dass man sie mit wenig Aufwand an runde Objekte anbringen kann. Man kann Kabelbinder oder Metalschellen nutzen, Plastik-Kabelbinder können allerdings bei Nässe anfangen zu rutschen.

* Idealer Betriebsmodus: Um ein funktionierendes Freifunk-Netz in einem Kleingarten/Lokal zu betreiben, empfiehlt es sich, die Richtantenne nur dazu zu nutzen, das Signal zur Empfangsstelle zu übertragen, und die Versorgung der Endgeräte im lokalen WLAN mit einem "normalen" Freifunk-Knoten zu machen. Dazu muss der Freifunk-Knoten Mesh-on-LAN oder Mesh-on-WAN aktiviert haben, sodass man den Mesh-Verkehr zwischen Richtantenne und WLAN-Knoten über ein Kabel laufen lässt. Bei Fragen stehen wir auf den üblichen Kanälen gerne zur Verfügung.



