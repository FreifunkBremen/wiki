


##### Mein Gerät kennt keinen DNS-Server
Wir verteilen die DNS-Server Informationen mittels Route Advertisment, genau den Eintrag RDNSS ([RFC 6106](https://tools.ietf.org/html/rfc6106) bzw. [RFC 8106            ](https://tools.ietf.org/html/rfc8106)).

Alle modernen Betriebssystem unterstützen dies seit Jahren.

Falls du ein älteres wie Windows 7 nutzt, kannst du den Eintrag selbst setzen.
Für die möglichen Adresse siehe [site.conf](https://github.com/FreifunkBremen/gluon-site-ffhb/blob/babel/site.conf#L46-L50), eine

PS: Wird unter Windows erst seit [Windows 10 1607]( Windows 10 1607) unterstützt, doch da der Support für Windows 7 am 20.01.2020 ausläuft ...


##### Ich hab keine IPv4-Adresse
Dies ist korrekt so, nach 20 Jahren IPv6 haben wir/ich entschieden dies abzuschalten

##### Ich brauch aber eine IPv4-Adresse
Dies Lösung ist **clat**, hierbei wird unser **plat** (DNS64 und NAT64) auf den Gateways erkannt und dazu passend eine Interface mit passenden Adressen generiert. 