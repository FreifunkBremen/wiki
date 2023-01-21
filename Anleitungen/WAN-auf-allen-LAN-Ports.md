Selbst benötigt, und auf dieser Wiki gefunden: [[https://wiki.freifunk.net/Konsole#WAN_auf_allen_Netzwerkports]]

Per SSH auf den Node, und dann:

<pre>
uci set network.client.ifname=bat0
uci set network.wan.ifname='eth0 eth1'
uci commit network
</pre>

Somit können auf den LAN-Ports weitere Clients des eigenen Netzwerks (Welches ja am WAN Port hängt) angeschlossen werden.