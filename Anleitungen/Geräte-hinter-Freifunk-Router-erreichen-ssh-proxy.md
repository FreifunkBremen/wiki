# Geräte hinter Freifunk Router erreichen (SSH Proxy)

Gelegentlich hängen zwischen zwei Freifunk-Routern Richtfunkgeräte mit proprietärem Betriebssystem.
Ziel der Anleitung ist es, ohne physikalische Verbindung zwischen Computer und proprietär betriebenem Gerät, die Konfigurationsoberfläche per Webbrowser zu öffnen.

## Beispiel

Das Richtfunkgerät B ist am WAN-Anschluss der Freifunk-Routers A verbunden.


Internet <--Kabel--> Freifunk-Router A <-Kabel-> **Richtfunkgerät B (192.168.1.15)** <-- WLAN --> Richtfunkgerät <-- Kabel --> Freifunk-Router

## Voraussetzungen

* Der Computer muss eine IPv6-Adresse haben.
* Auf dem Freifunk-Router (A) muss ein ssh-Key hinterlegt sein, oder der Zugang mit Passwort muss aktiviert sein.
* Die IP-Adresse des Richtfunkgeräts B ist bekannt.


1. IPv6-Adresse des Freifunk-Routers (A) mit Hilfe von map.ffhb.de rausfinden.

2. Linux/Mac im Terminal eingeben:
```
ssh -i _SSH-Key_ -D 8080 root@ipv6-adresse
```

3. 
Dem entsprechenden Interface am Freifunk-Router A eine passende IP-Adresse geben:
```
ip a add 192.168.1.21/24 dev br-wan
```

4. In Firefox Proxy einrichten:
Manuelle Konfiguration -> SOCKS-Host: 127.0.0.1, Port: 8080, SOCKS v5

5. In Firefox Weboberfläche des Richtfunkgeräts öffnen.
Ggf. mit Login-Daten.
```
http://192.168.1.15
```