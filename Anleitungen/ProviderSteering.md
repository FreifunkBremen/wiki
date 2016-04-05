## fastd blacklist-Skript
The magic `/etc/fastd/ffhb/blacklist.sh`-Skript
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
Enable it on fastd by append this line:
```
on verify "/etc/fastd/ffhb/blacklist.sh"
```
## Cronjob zum Aufräumen
unter `/etc/cron.d/fastd-blacklist`
```
*/5 * * * * root [ -d /run/fastd-blacklist ] && find /run/fastd-blacklist -type f -mmin +5 -delete
```

## Entwickeler
Danke an jplitza und mortzu.