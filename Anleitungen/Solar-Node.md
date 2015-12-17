#Solarnode
##Vorraussetzungen
Um einen Freifunk Node über eine Solaranlage zu versorgen sollte eine Grundfläche von mindestens 1m² vorhanden sein.

Der Balkon oder die Dachfläche sollte möglichst Richtung Süden ausgerichtet sein, und unverschattet sein.

###Montagen auf einer Dachfläche sollten unbedingt von einer Fachperson ausgeführt werden. Das Verletzungsrisiko ist hier enorm groß.

Sollte der Balkon oder die Dachfläche nicht nach Süden ausgerichtet sein muss die Anlage entsprechend in der Leistung der Solarpanele und des Pufferspeichers angepasst werden.

Etwas handwerkliches Geschick ist von Vorteil.
###Vor der Montage der Panele auf einer Dachfläche sollte unbedingt der Rat einer Fachfirma eingeholt werden.

##Welcher Node wie lange
Eine Grundsätzliche Entscheidung ist vor jeglicher Planung zu treffen.
Welcher Node soll eingesetzt werden und gibt es zusätzlich dazu noch andere Hardware die mit Solarstrom betrieben werden soll.

###Wichtig:
Hardware die mit 12V Gleichspannung oder weniger betrieben werden kann vermindert die Gesamtverlustleistung der Anlage, da auf eine Wechselrichtung verzichtet werden kann.

###Grundlegende Berechnung am Beispiel eines 841N Routers:
Stromaufnahme des Routers bei Betrieb an 12V ~250mA 

( Die Stromaufnahme hängt stark von der Menge der verbundenen Clients, dem Datendurchsatz und der Anzahl der Wlan-Meshverbindungen ab ) 

24 Stunden Dauerbetrieb ergibt eine Stromaufnahme innerhalb dieses Zeitraums von 

24 ( Stunden ) h * 250 ( Strom ) mA = 6000 ( milli Ampere Stunden ) mAh oder 6 ( Ampere Stunden ) Ah

Ein voll aufgeladener 12V Akku mit 6Ah leistung würde ausreichen um einen 841er 24 Stunden laufen zu lassen. 

###Wichtig:
Akkumulatoren ( auch spezielle Solarakkumulatoren ) haben nur eine bestimmte Menge an Lade- Entladezyklen. Danach verlieren sie dramatisch an Kapazität. 100%-ige Dutycycles (100% Ladung -> Abschaltung vor Tiefentladung ) verringern diese vom Hersteller angegebene Anzahl. 
In der Praxis ( auch bei großen Solaranlagen ) hat sich ein Dutycycle von 50% als angemessen, hinsichtlich des Kosten Nutzenfaktors, erwiesen.

Oben genannten Beispiel würde also einen 12V 12Ah Akkumulator benötigen.

##Solarpanel(e)
Am Markt sind verschiedene Typen von 12V Solarpanele vertreten. Die beiden großen Hauptgruppen Stellen Mono- sowie Polykristaline Module da. Daneben gibt es noch flexible und dünnfilm Module ( es gibt noch weitere diese sind aber noch nicht solange am Markt vertreten das sich reale Aussagen über Leistungsverluste / Alterung machen lassen ).

Monokristaline Module erkennt man an ihrer schwarzen Oberfläche, während polykristaline oftmals eine blaue Waveroberfläche besitzen.

Beide Typen haben ihre Vor- und Nachteile. Für das Projekt selber sind diese Utnerschiede aber nicht relevant.

Solarpanele haben immer Herstellerangaben zur Leistung. Dieser Wert wird in kWp ( Kilowatt peak ) angegeben. 

Das bedeutet das ein Modul mit dem Wert 1 kWp unter Laborbedingungen (1000 W/m2 Einstrahlung, 25 °C Modultemperatur, 1,5 Air Mass ) genau 1000 Watt erzeugt.

In der Realität bedeutet das, das ein Modul mit 1kWp in Bremen bei optimaler Ausrichtung und Hinterlüftung 800W Leistung erbringt.

In Bremen beträgt die durschnittliche Sonnescheindauer pro Tag etwa 4 Stunden. ( Im Sommer liegt der tatsächliche Wert eher bei 12 Stunden am Tag, dafür im Winter teilweise bei 1 Sonnestunde pro Woche ).

Dieser Umstand macht es erforderlich in die Berechnung eine sog. Gangreserve einzufügen. Also einen Puffer für Tage an denen die Akkumulatoren nicht geladen werden können, weil die Sonneneinstrahlung zu gering ist.

Ohne Gangreserve würde also ein 12V Panel mit einer Leistung von 50Wp folgende Rechnung erfüllen:

50Wp * 0,8 ( 80% reale Leistung ) * 4h = 160Wh ( Wattstunden )

160Wh / 12V ( Panelspannung ) = ~13,3Ah

Der 12 Ah Akkumulator würde also innerhalb von 4 Stunden ausreichend Aufgeladen. Der Router selber verbraucht aber innerhalb dieser Zeitspanne auch noch einmal 1 Ah.
Dieses Beispiel zeigt schon sehr deutlich das eine solche Anlage immer nach oben hin erheblich größer ausgelegt werden sollte. ( Sofern man 24/7 Betrieb realisiren will ).

Zusammenfassend kann man sagen das eine Anlage bestehend aus :

12V 50Wp Solarpanel ( optimal ausgerichtet )

12V Laderegler 

12V 12Ah Akkumulator 

in der Lage ist einen 841er Router grundsätzlich über die Sommermonate zu versorgen.

Für das Frühjahr und den Herbst könnte eine Verdopplung der Solarleistung und der Akkumulatorkapazität noch eine ausreichende Versorgung gewährleisten. ( Immer abhängig wieviel Sonnenstunden real auftreten ).

Eine Berechnung macht an dieser Stelle wenig Sinn, da eine Wettervorhersage , oder besser eine Prognose der zu erwartenden Sonnenstunden, nicht machbar ist.

Für den Winter müsste die Anlage derartig überdimensioniert werden, so dass ein Betrieb sich nicht rentieren würde.
Es müsste soviel Energie aus dem Sommer ( ggf. auch aus dem Herbst ) gespeichert werden, das die Selbstentladung der Akkumulatoren so groß werden würde, das die Anlage nicht einmal rechnerisch unter absoluten Idealbedingungen einen 24/7 Betrieb gewährleisten könnte.

##Bilder und Aufbau der Testanlage folgen in kürze






