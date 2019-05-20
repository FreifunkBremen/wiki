# Debugging

## Babeld

Ein Kontrollsocket des Daemons läuft standardmäßig auf Port `33123` auf den Loop-Interface `::1`.

- Babeld's status auslesen:
  `echo dump | nc ::1 33123`

- Babeld's status monitoren (changes mitbekommen)
`echo monitor | nc ::1 33123`

- Interface zum Babeld hinzufügen
`echo "interface mesh-vpn-0" | nc ::1 33123`