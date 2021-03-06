Es gibt momentan 6 Gateway-Server, die zum Verbinden der Knoten untereinander und mit dem Internet genutzt werden.

## Gateways a.k.a VPNs
Der Status der Gateways kann hier eingesehen werden: https://status.bremen.freifunk.net/

Zum Uplink siehe [[Infrastruktur/Netzwerk]]

### Sponsoren und Konfiguration

| Server | Sponsor      | Standort            | Anbindung    |
|:-------|:-------------|:--------------------|:-------------|
| vpn01  | LWLcom       | Bremen              | ~700 MBit/s  |
| vpn02  | PLUTEX       | Bremen              |              |
| vpn03  | LWLcom       | Bremen              |              |
| vpn04  | PLUTEX       | Bremen              |              |
| vpn05  | PLUTEX       | Bremen              |              |
| vpn06  | Digineo GmbH | 23media, Frankfurt  |              |

("Anbindung" ist die gemessene Bandbreite aus dem Internet.)

### Ansprechpartner

| Gateway | Hauptverantwortlicher | Co Verantwortlicher |
|---------|-----------------------|---------------------|
| vpn01   | jplitza, mortzu       | -                   |
| vpn02   | jplitza, mortzu       | -                   |
| vpn03   | jplitza, mortzu       | -                   |
| vpn04   | genofire              | jplitza, mortzu     |
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


# Hinweise zu den Servern

## Dienst auf dem Webserver neustarten (als normaler User)
Die Daemons auf dem Webserver laufen unter eigenen User-Accounts und werden durch die User-spezifische Systemd-Instanz kontrolliert. Um einen Dienst neuzustarten, loggt man sich mit dem entsprechenden User ein und führt z.B. sowas aus:

`systemctl --user restart phabricator.service`

Möglicherweise schlägt das fehl, mit der Fehlermeldung "Failed to connect to bus: No such file or directory". Das liegt an einem [Systemd-Fehler](https://github.com/systemd/systemd/issues/4229), der in der verwendeten Debian-Version noch nicht gefixt ist. Als Workaround kann man vor dem `systemctl`-Aufruf folgenden Befehl ausführen:

`export XDG_RUNTIME_DIR=/run/user/$UID`

## Dienst auf dem Webserver neustarten (als root)
Als Root-user kann man auch den ganzen Systemd-Prozess des Users neustarten; dabei werden auch alle Kinder-Daemons neugestartet:

`systemctl restart user@1010.service`
