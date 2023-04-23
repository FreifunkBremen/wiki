**[RaspBerry-Speedtest]**

## Inhalt:
[[_TOC_]]

Hier mal ein schöner Speedtest.

**[------------------------------------------------------------------------------------------------------------------------- Zurück zum Inhalt:](#inhalt)**

### Raspberry Pi Speedtest
#### Installation

Zuerst wird das Paket speedtest-cli installiert.
~~~
sudo apt install speedtest-cli
~~~
#### Speedtest durchführen

Wenn das Package eingespielt ist, reicht die Eingabe des folgenden Befehls:
~~~
speedtest-cli
~~~

Hierbei wird der Test über den nächsten Server ausgeführt. Ist man mit dem Resultat nicht zufrieden, kann ein anderer Server angesteuert werden. Dazu lässt man sich die 10 nächsten Standorte anzeigen.
~~~
speedtest-cli --list
~~~



~~~
pi@pi4:~ $ speedtest-cli
Retrieving speedtest.net configuration...
Testing from Deutsche Telekom AG (93.215.158.51)...
Retrieving speedtest.net server list...
Selecting best server based on ping...
Hosted by Schlueter Onlinedienste (Ruethen) [179.26 km]: 15.497 ms
Testing download speed................................................................................
Download: 245.76 Mbit/s
Testing upload speed......................................................................................................
Upload: 43.65 Mbit/s
pi@pi4:~ $
~~~



**[------------------------------------------------------------------------------------------------------------------------- Zurück zum Inhalt:](#inhalt)**