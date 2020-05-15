Um den Durchsatz zwischen zwei Knoten zu Messen, kann dieses mit dem Programm iperf3 auf der Konsole durchgeführt werden.
Möchte ich einfach nur einen Speedtest durchführen, reicht es den HTML Speedtest der FFHB VPN-Server zu nutzen.
Hierzu einfach nachsehen, mit welchem VPN-Server ich verbunden bin und im Browser auf dem PC einfach die Adresse:
http://vpn01.ffhb.de/speedtest/ aufrufen. Für VPN 3 ist dieses entsprechend http://vpn03.ffhb.de/speedtest/

Bei kleinen Routern mit 4Mb Flash gehts nicht, da lässt sich nichts mehr zusätzlich installieren. Es werden ca. 40kb Speicher benötigt. Bei den 841er-Routern ist der Speicherplatz leider zu knapp.

iperf3 testet die Verbindung über die IPv6-Adressen zwischen zwei Knoten, für die Interpretation des Testergebnisses muss klar sein, dass dieser Test auf *Layer 3* stattfindet. Bei mehreren möglichen Verbindungen durch das Batman-Mesh auf Layer 2 ist es möglich, dass eine andere physische Verbindung genutzt wird als die augenscheinlich erwartete, der Test gibt keine Info darüber, wo die Pakete auf Layer 1 und 2 nun tatsächlich ausgetauscht werden.

### Installation von iperf3

Iperf3 kann über opkg mit folgenden Kommandos aus den Paketquellen von OpenWRT über SSH installiert werden.
~~~
opkg update && opkg install iperf3
~~~
Dies wird auf beiden Knoten ausgeführt.

### Portfreigabe in der Firewall

Wird gerne vergessen. Auf dem Knoten, bei dem iperf3 im Server-Modus ausgeführt wird, muss Port 5201 in der Firewall freigegeben werden. Mit den folgenden Befehlen wird eine weitere Firewall-Regel dazu hinzugefügt und die Firewall neu gestartet: Die Firewallregel ist nicht permanent und wird mit dem nächsten Release gelöscht.
~~~
uci add firewall rule
uci set firewall.@rule[-1].src=mesh
uci set firewall.@rule[-1].name=mesh_iperf
uci set firewall.@rule[-1].dest_port=5201
uci set firewall.@rule[-1].target=ACCEPT
uci set firewall.@rule[-1].proto=tcp
uci set firewall.@rule[-1].family=ipv6
uci commit firewall
/etc/init.d/firewall restart
~~~

Sollen Firewallregeln permanent upgradesicher sein, verwenden wir die Datei /etc/firewall.user
In diese Datei fügen wir unsere Regel ein.
~~~
# This file is interpreted as shell script.
# Put your custom iptables rules here, they will
# be executed with each firewall (re-)start.

# Internal uci firewall chains are flushed and recreated on reload, so
# put custom rules into the root chains e.g. INPUT or FORWARD or into the
# special user chains, e.g. input_wan_rule or postrouting_lan_rule.

config rule
	option src 'mesh'
	option name 'mesh_iperf'
	option dest_port '5201'
	option target 'ACCEPT'
	option proto 'tcp'
	option family 'ipv6'
~~~

Firewall ebenfalls neu Starten. /etc/init.d/firewall restart

### Starten von iperf3

Der iperf3-Server wird nun mit dem Kommando -s
~~~
iperf3 -s -V
~~~
gestartet. (-s: Server, -V: Detailliertere Ausgabe (Verbose)). Auf dem Client-Knoten wird iperf3 nun mit dem Kommando -c und der Angabe der IPv6 des iperf-Servers
~~~
iperf3 -V -c2a06:8782:ffbb:1337:feec:daff:fe7f:28e1
~~~
gestartet. Es wird ein Test mit einer Dauer von 10 Sekunden gestartet, bei dem jede Sekunde ein Ergebnis angezeigt wird. Die Testzeit kann über „-t 30“ auf 30 Sekunden verlängert werden, mit „-i 10“ wird das Intervall auf der Clientseite auf 10 Sekunden erhöht.

Der Server wird im Terminal durch die Tastenkombination Strg+C beendet. 


### Wiederholte Messung einrichten:

Zum wiederholten Messen kann man iperf3 mit der Option -D starten, dann läuft der Iperf-Server als Daemon auch nach Ende der SSH-Session weiter. Beispiel:
~~~
iperf3 -s -D
~~~


Auf dem Client richtet man einen Cronjob ein, der zB jede Nacht um 3 Uhr für 5 Minuten testet. 
~~~
* 3 * * * iperf3 -c ServerIP -t 300
~~~

Dabei ist unbedingt darauf zu Achten, dass Kapazitäten nicht unnötig belastet werden, zB würde eine dauerhafte Messung die Verbindung zwischen Client und Server dauerhaft auslasten, sodass keine anderen Pakete übertragen werden können.

Die Ergebnisse muss man entweder selbst loggen bei Grafana ablesen. 


