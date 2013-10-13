## Grundidee

Das Mesh-VPN verbindet einzelne Freifunkrouter, die sich nicht direkt sehen können, über das Internet miteinander.

## Funktionsweise

Jeder Knoten, der mit dem Internet verbunden wird, baut eine verschlüsselte Verbindung zu unseren VPN-Gateways auf, von Freiwilligen betriebene Server. In diesem Fall ersetzen sie die ansonsten nötigen Richtfunkstrecken um Freifunk-"Inseln" zu verbinden.

## Technisches

Über das Technische bin ich mir noch nicht klar. Wir könnten, wie die [Lübecker](http://luebeck.freifunk.net/wiki/Mesh-VPN) [fastd](https://projects.universe-factory.net/projects/fastd/) verwenden oder OpenVPN oder was ganz anderes.

### OpenVPN

Falls wir uns für OpenVPN entscheiden wäre es vermutlich sinnvoll, eine eigene [Certificate Authority](https://de.wikipedia.org/wiki/Zertifizierungsstelle) (CA) für bremen.freifunk.de aufzubauen, die jedem Gerät ein Zertifikat ausstellt. Sobald mehrere VPN-Server verfügbar sind könnten diese zu Lastverteilung über DNS Round-Robin verteilt werden und untereinander am besten vollvermascht VPNs aufbauen und $routingprotokoll (OSPF?) sprechen.