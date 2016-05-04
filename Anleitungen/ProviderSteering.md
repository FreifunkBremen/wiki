Die VPN-Server sind unterschiedlich gut von verschiedenen Providern erreichbar (z.B. Hetzner-Server von DTAG), dafür wurde dieses kleine Skript entwickelt.

ProviderSteering ist, in Anlehnung auf [Band Steering](http://www.arubanetworks.com/techdocs/ArubaOS_64_Web_Help/Content/ArubaFrameStyles/ARM/Band_Steering.htm), das Verfahren, welches wir entwickelt haben, um Knoten, die von einem für einen VPN-Server schlecht geeigneten Netz erst beim zweiten Verbindungsversuch annimmt. (Mit der Hoffnung, das der Knoten von ein VPN-Server mit einer besseren Anbindung angenommen wird.)

## fastd blacklist-Script
The magic `/etc/fastd/ffhb/blacklist.sh`-Script
```
#!/bin/sh -e

STATE_DIR='/run/fastd-blacklist'

if [ ! -d "$STATE_DIR" ]; then
  mkdir -m 0700 -p "$STATE_DIR"
fi

if [ ! -f "${STATE_DIR}/${PEER_KEY}" ]; then
  RDNS="$(dig +short -x "$PEER_ADDRESS")"

  case "$PEER_ADDRESS" in
    127.0.0.1)
     touch "${STATE_DIR}/${PEER_KEY}"
     exit 1
    ;;
  esac

  case "$RDNS" in
    localhost.)
     touch "${STATE_DIR}/${PEER_KEY}"
     exit 1
    ;;
  esac
fi
```

Dieses muss dann in fastd aktiviert werden:
```
on verify "/etc/fastd/ffhb/blacklist.sh"
```

**Achtung:**
Das blacklist.sh-Script muss erweitert, nicht ersetzt werden.

## Cronjob zum Aufräumen
unter `/etc/cron.d/fastd-blacklist`
```
*/5 * * * * root [ -d /run/fastd-blacklist ] && find /run/fastd-blacklist -type f -mmin +5 -delete
```
## Examples
Hier ein paar Netze, die zunächst zurückgestellt werden.
### Kabel-Deutschland
```
  *.dynamic.kabel-deutschland.de.)
    touch "${STATE_DIR}/${PEER_KEY}"
    exit 1
  ;;
```
### o2 / Telefonica
```
  *.net.telefonica.de.)
    touch "${STATE_DIR}/${PEER_KEY}"
    exit 1
  ;;
```

## Entwickler
Danke an jplitza und mortzu.
