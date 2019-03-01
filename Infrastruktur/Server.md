Es gibt momentan 6 Gateway-Server, die zum Verbinden der Knoten untereinander und mit dem Internet genutzt werden.

## Gateways a.k.a VPNs
Der Status der Gateways kann hier eingesehen werden: https://status.bremen.freifunk.net/

### Sponsoren und Konfiguration
| Server | Sponsor      | Standort | Uplink-Anbieter    | Uplink-Standort |
|:-------|:-------------|:---------|:-------------------|:----------------|
| vpn01  | LWLcom       | Bremen   | Digineo            | Bremen          |
| vpn02  | PLUTEX       | Bremen   | Digineo            | Bremen          |
| vpn03  | LWLcom       | Bremen   | Digineo            | Bremen          |
| vpn04  | PLUTEX       | Bremen   | -                  | Bremen          |
| vpn05  | PLUTEX       | Bremen   | Digineo            | Bremen          |
| vpn06  | Digineo GmbH | 23media  | Digineo            | Frankfurt       |

### Ansprechpartner

| Gateway | Hauptverantwortlicher | Co Verantwortlicher |
|---------|-----------------------|---------------------|
| vpn01   | jplitza, mortzu       | -                   |
| vpn02   | jplitza, mortzu       | -                   |
| vpn03   | jplitza, mortzu       | -                   |
| vpn04   | jplitza, mortzu       | genofire            |
| vpn05   | jplitza, mortzu       | -                   |
| vpn06   | corny                 | genofire, jplitza   |


## Server für zentrale Dienste
| Dienst                                 | Verantwortlicher          | Standort              |
|----------------------------------------|---------------------------|-----------------------|
| [Website](https://ffhb.de)             | jplitza, mortzu           | Bremen / LWLcom       |
| [Downloads](https://downloads.ffhb.de) | corny, jplitza, mortzu    | Bremen / LWLcom       |
| DNS                                    | corny, genofire, jplitza, mortzu   | Bremen / LWLcom  |
| [Wiki](https://wiki.ffhb.de)           | jplitza, mortzu           | Bremen / LWLcom       |
| [Karte](https://map.ffhb.de)           | genofire, jplitza, mortzu | Bremen / LWLcom       |
| [Ticketsystem](https://tasks.ffhb.de)  | mortzu, SimJoSt, ollibaba | Bremen / LWLcom       |
| [gatemon](https://status.ffhb.de)      | mortzu                    | Bremen / LWLcom       |


## Physikalische Hardware
| Server                  | Dienste               | Verantwortlicher           | Standort              |
|-------------------------|-----------------------|----------------------------|-----------------------|
| LWLcom-Server ("bre1")  | DNS, Mailserver, Webserver, Karte (ffmap), IPv6-Downlink, vpn01, vpn03 | chrische, morpheus, mortzu, jplitza | Bremen / LWLcom |
| Plutex-Server ("bre2")  | Jenkins, vpn02, vpn04 | mortzu, jplitza            | Bremen / Plutex       |
| Plutex-Server ("echo")  | vpn05                 | mortzu, jplitza            | Bremen / Plutex       |
| Router                  |                       | chrische, morpheus, mortzu | Bremen / Plutex       |
