Es gibt momentan 6 Gateway-Server, die zum Verbinden der Knoten untereinander und mit dem Internet genutzt werden.

## Gateways a.k.a VPNs
Der Status der Gateways kann hier eingesehen werden: https://status.bremen.freifunk.net/

Zum Uplink siehe [[Infrastruktur/Netzwerk]]

### Sponsoren und Konfiguration
| Server | Sponsor      | Standort            |
|:-------|:-------------|:--------------------|
| vpn01  | LWLcom       | Bremen              |
| vpn02  | PLUTEX       | Bremen              |
| vpn03  | LWLcom       | Bremen              |
| vpn04  | PLUTEX       | Bremen              |
| vpn05  | PLUTEX       | Bremen              |
| vpn06  | Digineo GmbH | 23media, Frankfurt  |

### Ansprechpartner

| Gateway | Hauptverantwortlicher | Co Verantwortlicher |
|---------|-----------------------|---------------------|
| vpn01   | jplitza, mortzu       | -                   |
| vpn02   | jplitza, mortzu       | -                   |
| vpn03   | jplitza, mortzu       | -                   |
| vpn04   | jplitza, mortzu       | genofire            |
| vpn05   | jplitza, mortzu       | -                   |
| vpn06   | corny                 | genofire, jplitza   |


## Zentrale Dienste
| Dienst                                 | Verantwortlicher          | Standort              |
|----------------------------------------|---------------------------|-----------------------|
| [Website](https://ffhb.de)             | jplitza, mortzu, oliver   | Bremen / LWLcom       |
| [Downloads](https://downloads.ffhb.de) | corny, jplitza, mortzu, oliver  | Bremen / LWLcom       |
| DNS                                    | corny, genofire, jplitza, mortzu   | Bremen / LWLcom  |
| [Wiki](https://wiki.ffhb.de)           | jplitza, mortzu           | Bremen / LWLcom       |
| [Karte](https://map.ffhb.de)           | genofire, jplitza, mortzu | Bremen / LWLcom       |
| [Ticketsystem](https://tasks.ffhb.de)  | mortzu, SimJoSt, ollibaba | Bremen / LWLcom       |
| [gatemon](https://status.ffhb.de)      | mortzu                    | Bremen / LWLcom       |


## Physikalische Hardware
| Server | Dienste               | Verantwortlicher           | Standort              |
|-------------------------|-----------------------|----------------------------|-----------------------|
| bre-1  | DNS, Mailserver, Webserver, Karte (ffmap), IPv6-Downlink, vpn01, vpn03 | chrische, morpheus, mortzu, jplitza | Bremen / LWLcom |
| Cisco-Router | BGP | chrische, morpheus, mortzu, jplitza    | Bremen / LWLcom       |
| bre-2  | Jenkins, vpn02, vpn04 | mortzu, jplitza            | Bremen / PLUTEX       |
| echo   | vpn05                 | mortzu                     | Bremen / PLUTEX       |
