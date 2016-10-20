Es gibt unter der Firmware 2016.1 ein Problem, bei dem eine Node nach dem Flashen eine VPN-Verbindung aufbaut, dann aber wieder verliert und nicht wiederherstellen kann. Dieser Fehler ist an IPv4-only-Anschlüssen bekannt.

Nach ein bis zwei Stunden nach dem Flashen verliert die Node ihren Uplink und stellt diesen nicht wieder her. Ein weiteres Merkmal ist, dass sich Clients nicht einloggen können, da sie keine IP bekommen.

Nach herstellen einer SSH-Verbindung auf die Node, zeigt der Befehl

~~~
logread && logread -f
~~~

an, dass die Namen vpn01.bremen.freifunk.net usw. nicht aufgelöst werden können.

*Dies liegt wahrscheinlich daran, dass die Nodes unsere Nameserver nicht finden können, da diese nur per IPv6 in der Firmware hinterlegt sind und der Anschluss (Uplink) der Node nur IPv4 hat.*

Beheben lässt sich dieser Fehler vorübergehend, mit einer Änderung in der Netzwerk-Config.
Diese ruft man mit

~~~
vi /etc/config/network
~~~

in einem Text-Editor auf.

Man scrollt nun zur "wan" Schnittstelle des Routers und geht mit einem Druck der Tasten CAPS+i in den "Insert"-Modus.

An das Ende der "wan"-Config wird nun

~~~
option dns '8.8.8.8'
~~~

angehängt. Mit einem Druck auf die ESC-Taste und der Eingabe ":wq" speichert man und verlässt den Editor.

Nach einem Neustart per

~~~
reboot
~~~

sollte die Freifunk-Node dann funktionieren.