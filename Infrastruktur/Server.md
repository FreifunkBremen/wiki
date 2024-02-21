## Gateways a.k.a VPNs
Der Status der Gateways kann hier eingesehen werden: [[https://status.bremen.freifunk.net/]]

Zum Uplink siehe [[Infrastruktur/Netzwerk]]

## Zentrale Dienste

| Dienst                                 | Verantwortlicher          |
|----------------------------------------|---------------------------|
| [Website](https://ffhb.de)             | jplitza, mortzu, oliver   |
| [Downloads](https://downloads.ffhb.de) | corny, jplitza, mortzu, oliver  |
| [DNS](https://github.com/FreifunkBremen/ffhb-dns)  | genofire, jplitza, mortzu   |
| [Wiki](https://wiki.ffhb.de)           | jplitza, mortzu           |
| [Karte](https://map.ffhb.de)           | genofire, jplitza, mortzu |
| [Ticketsystem](https://tasks.ffhb.de)  | jplitza, mortzu, oliver, SimJoSt |
| [gatemon](https://status.ffhb.de)      | jplitza, mortzu           |
| [tiles](https://tiles.ffhb.de) (s.a. [[Anleitungen/Kartendaten aktualisieren]]) | ollibaba                  |


## Physikalische Hardware

| Server  | Hardware                | CPU                                         | RAM    | Dienste    | Verantwortlicher                      | Standort        |
|---------|-------------------------|---------------------------------------------|--------|------------|---------------------------------------|-----------------|
| gateway | Cisco ASR 1001          |                                             | 16 GB  | BGP-Uplink | chrische, morpheus, mortzu, jplitza | Bremen / LWLcom |
| bre-2   | HP ProLiant DL360e Gen8 | 2× Intel Xeon E5-2430 v2 @ 2.50GHz, 6C, 12T | 128 GB | VMs        | janeric, jplitza, mortzu          | Bremen / LWLcom |
| bre-3   | Dell PowerEdge R610     | 2× Intel Xeon L5640 @ 2.27GHz, 6C, 12T      | 24 GB  | VMs        | jplitza, mortzu                       | Bremen / LWLcom |

# Hinweise zu den Servern

## Wartungsfenster

Die VM-Hosts starten automatisch in der Nacht auf Sonntag neu, um sicherzustellen dass alle Dienste die aktuellsten Softwareversionen benutzen.

## Dienst auf dem Webserver neustarten (als normaler User)
Die Daemons auf dem Webserver laufen unter eigenen User-Accounts und werden durch die User-spezifische Systemd-Instanz kontrolliert. Um einen Dienst neuzustarten, loggt man sich mit dem entsprechenden User ein und führt z.B. sowas aus:

    systemctl --user restart phabricator.service


Möglicherweise schlägt das fehl, mit der Fehlermeldung "Failed to connect to bus: No such file or directory". Das liegt an einem [Systemd-Fehler](https://github.com/systemd/systemd/issues/4229), der in der verwendeten Debian-Version noch nicht gefixt ist. Als Workaround kann man vor dem `systemctl`-Aufruf folgenden Befehl ausführen:

    export XDG_RUNTIME_DIR=/run/user/$UID

## Dienst auf dem Webserver neustarten (als root)
Als Root-user kann man auch den ganzen Systemd-Prozess des Users neustarten; dabei werden auch alle Kinder-Daemons neugestartet:

    systemctl restart user@1010.service
