# Debugging

## Babeld

Ein Kontrollsocket des Daemons läuft standardmäßig auf Port `33123` auf den Loop-Interface `::1`.
Daher kann man einfach mittels netcat mit den Daemon interagieren e.g. `nc ::1 33123`.

Die meist benötigsten Befehle im Überlick, mehr inder [man-page](https://www.irif.fr/~jch/software/babel/babeld.html):

- Babeld's status auslesen:
  `echo dump | nc ::1 33123`

- Babeld's status monitoren (changes mitbekommen)
`echo monitor | nc ::1 33123`

- Interface zum Babeld hinzufügen
`echo "interface mesh-vpn-0" | nc ::1 33123`

PS: Der Status vom Gateway kann mittels [babelweb2](https://github.com/Vivena/babelweb2) abgefragt werden: http://vpn04.ffhb.de:8080/