Es gibt momentan 6 Gateway-Server, die zum Verbinden der Knoten untereinander und mit dem Internet genutzt werden.

## Gateways a.k.a VPNs
Der Status der Gateways kann hier eingesehen werden: https://status.bremen.freifunk.net/

### Sponsoren und Konfiguration
| Server | Sponsor      | Standort | Uplink-Anbieter    | Uplink-Standort |
|:-------|:-------------|:---------|:-------------------|:----------------|
| vpn01  | LWLCOM       | Bremen   | Digineo            | Bremen          |
| vpn02  | PLUTEX       | Bremen   | Digineo            | Bremen          |
| vpn03  | LWLCOM       | Bremen   | Digineo            | Bremen          |
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
| [Website](https://ffhb.de)             | jplitza, mortzu           | Bremen / LWLCOM       |
| [Downloads](https://downloads.ffhb.de) | corny, jplitza, mortzu    | Bremen / LWLCOM       |
| DNS                                    | corny, genofire, jplitza, mortzu           | Bremen / LWLCOM       |
| [Wiki](https://wiki.ffhb.de)           | jplitza, mortzu           | Bremen / LWLCOM       |
| [Karte](https://map.ffhb.de)           | genofire, jplitza, mortzu | Bremen / LWLCOM       |
| [Ticketsystem](https://tasks.ffhb.de)  | mortzu, SimJoSt, ollibaba | Bremen / LWLCOM       |
| [gatemon](https://status.ffhb.de)      | mortzu                    | Bremen / LWLCOM       |
| LWLCOM Hardwareserver ("bre1")         | chrische, morpheus, mortzu, jplitza | Bremen / LWLCOM       |
| Plutex-Hardwareserver ("bre2")         | mortzu, jplitza           | Bremen / LWLCOM       |
| Plutex-Hardwareserver ("echo")         | mortzu, jplitza           | Bremen / LWLCOM       |
| Router                                 | chrische, morpheus, mortzu | Bremen / LWLCOM       |

Auf bre1 läuft: DNS, Mails, Webserver, ffmap, IPv6-Downlink, vpn01, vpn03

Auf bre2 läuft: Jenkins, vpn02, vpn04

Auf "echo" läuft: vpn05
