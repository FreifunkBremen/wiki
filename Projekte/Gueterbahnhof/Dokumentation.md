Hier infos zur doku

Naming Convention: 

* Die Namen der Knoten haben den Standort auf dem Gelände einkodiert. 
* Alle Routernamen beginnen mit GB (GüterBahnhof). 
* Router im "Künstlerhaus", also dem Verwaltungshaus auf der kurzen Seite zwischen Hof und Gleishalle, sind GB-KH (Künsttlerhaus) benannt. Im Anschluss folgt das Stockwerk GB-KH-E0 (Etage 0 = Keller, Etage 2 = Oberste Etage) und eine fortlaufende Nummer pro Etage, also GB-KH-E0-1.
* Router an den langen Torseiten sind GB-RT (rechte Tore) und GB-LT (linke Tore) benenannt und ebenfalls fortlaufend nummeriert (z.B. GB-RT-3)
* Es gibt weiterehin einige Testrouter, CPEs, usw. die nicht dieser Konvention folgen.

Konfiguration der Knoten:

* Soweit nicht anders angegeben geben alle Router auf allen Ports das Mesh-Netz raus. 
* Wifi-Mesh wäre wünschenswerterweise überall aus (aktuell nocht nicht der Fall, wird an manchen Orten noch als Fallback-Option benutzt, Stand: Feb2021). 
* Außer bei Routern im GB-RT und GB-LT Strang, da ist Wifi-Mesh aktiviert. Durch die Schaltung der Router in Reihe gibt es manchmal bei Stromausfällen (Hauptsicherung aus, Elektro-Umbau, etc) abrisse für viele Nutzer*innenn. Daher ist der WIFI-Mesh als Fallback aktiviert.
* agffgb07 ("Keller"): WLAN komplett aus, Client-Netz auf den (gelben) LAN-Ports, durch einen USB-Switch 3 zusätzliche Client-Ports 
* agffgb12 ("Schaulust"): Wifi-Mesh ist an, damit der Router erreichbar ist, auch wenn die Verkabelung zu Tor40 ausfällt.
