# Babel-FAQ


#### Mein Gerät kennt keinen DNS-Server
Wir verteilen die DNS-Server Informationen mittels Route Advertisment, genau den Eintrag RDNSS ([RFC 5006](https://tools.ietf.org/html/rfc5006) bzw. [RFC 8106            ](https://tools.ietf.org/html/rfc8106)).


Falls du ein älteres Betriebsystem wie Windows 7 nutzt, kannst du den Eintrag selbst setzen.
Für die möglichen Adresse siehe [site.conf](https://github.com/FreifunkBremen/gluon-site-ffhb/blob/babel/site.conf#L46-L50), VPN04 hat z.B. die Adresse `2a06:8782:ffbb:bab0::4`.

PS: Wird unter Windows erst seit [Windows 10 1607](https://insinuator.net/2017/05/one-step-closer-rdnss-rfc-8106-support-in-windows-10-creators-update/) unterstützt, doch da der Support für Windows 7 am 20.01.2020 ausläuft ...


#### Ich hab keine IPv4-Adresse
Dies ist korrekt so, nach 20 Jahren IPv6 haben wir entschieden dies abzuschalten.



#### Ich brauch aber eine IPv4-Adresse
Dies Lösung ist **clat**, hierbei wird unser **plat** (DNS64 und NAT64) auf den Gateways erkannt und dazu passend eine Interface mit passenden Adressen generiert.

###### Betriebsysteme:
Moderne Android und iPhones machen dies bereits automatisch, genau so wie MAC OSX. Unter Linux muss man ggf. noch ein passendes Paket installieren [clatd](https://github.com/toreanderson/clatd) unter Archlinux [AUR](https://aur.archlinux.org/packages/clatd-git).
Unter Windows ist uns keine Lösung bekannt, ihr müsst euch mit den DNS64 und NAT64 zufrieden geben.