# Probleme mit dem Umstieg auf B.A.T.M.A.N v15

Hier sammeln wir Probleme, die beim [Testen vom neuen B.A.T.M.A.N-v15-Netz](/Anleitungen/BATMAN v15 Umstieg.md) aufgefallen sind.

## Beobachtete Probleme
- Reverse-DNS für Knoten-IPs funktioniert nicht
- `host -6 heise.de` geht nicht (aber das geht auf meinem PC im normalen Internet ebenfalls nicht?! Sollte das funktionieren?)
- vpn07.onffhb.de und vpn08.onffhb.de werden nicht aufgelöst
- Auf `ffhb_batv15` umgestellte Knoten zeigen keine Offline-SSID obwohl sie allein und offline sind. (Mit `ffhb_11s` mesh in Reichweite)


## Noch nicht getestet
Diese Punkte sollten noch getestet werden:
- WLAN-Roaming (also: schalten Telefone und Notebooks automatisch auf einen neuen Knoten um, wenn der alte Knoten nicht merhr in Reichweite ist?)
- Meshing nur über LAN (das erfordert wohl einen Knoten, der nicht über WLAN meshen kann)
    - zu testen: funktioniert das generell; und wird das auf der Karte korrekt dargestellt?
- Speedtest explizit über v4 oder v6
- Multicast-Traffic zwischen Clients am gleichen Knoten
    - dazu brauch ich mal zwei Clients, die a) definitiv im v15-Netz sind und b) Multicast-Traffic anzeigen können
- IC-VPN


## Weitere TODOs
- Gatemons für die neuen VPN-Server aufsetzen (würde ich mir sparen und darauf warten, dass sich das Netz umgestellt hat --mortzu)
- ~~Reverse DNS für vpn7/8 hinzufügen (IPv4 und v6)~~
- auf map.ffhb.de wird bei den neuen Knoten als IPv6-Gateway eine MAC-Adresse statt ein Name angezeigt
    - für Knoten, die an vpn07 hängen, steht da 1e:a8:07:84:63:51; für vpn08-Knoten steht da fe:2c:8b:4a:db:ce
    - für den IPv4-Gateway steht da ein Name, wie erwartet
    - im v13-Netz steht bei den IPv4- und IPv6-Gateways jeweils ein Name
    - muss der `respondd` auf den VPN-Servern noch irgendwelche anderen Infos/Adressen melden, damit das funzt?
- ~~neue Server zum Monitoring hinzufügen~~