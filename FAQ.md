# Häufig gestellte Fragen (FAQ)
TODO: schönes Accordion oder sowas basteln und auf Hauptseite verlinken
TODO: hyperlinks pflegen
TODO: reviewen
## Allgemein
### Was ist Freifunk?
Freifunk ist ein Funknetzwerk in Bürgerhand. Privatleute stellen freiwillig offene WLAN Zugangspunkte zur Verfügung, die jeder kostenlos nutzen kann. Diese Zugangspunkte sind untereinander verbunden (in der Fachsprache: sie “meshen” miteinander) und bilden so ein dezentrales vermaschtes Netzwerk. Man kann sich Freifunk als stadtweites “Intranet” vorstellen, also ein “Internet im Kleinen”. So kann man im Freifunknetz beispielsweise Websiten aufrufen, die es nur im Freifunknetz, aber nicht im Internet gibt. Hier findest du eine Liste der verfügbaren Dienste.

### Wie kann ich Freifunk nutzen?
Im Empfangsbereich eines Zugangspunktes kannst Du das Freifunk-Netz mit jedem WLAN-fähigen Endgerät nutzen. Wenn Du bei eingeschaltetem WLAN den Netzwerknamen bremen.freifunk.net siehst, kannst Du Dich einfach und ohne Passwort mit dem Funknetzwerk verbinden. Den nächsten Zugangspunkt findest Du unter
http://knotenkarte.de/

### Was ist ein Knoten (Node)?
Knoten (engl. 'Node') ist gleichbedeutend mit Router, Access-Point oder Zugangspunkt. Sie werden in der Regel von Privatpersonen betrieben und bieten Dir und Anderen Zugang zum Freifunknetzwerk.

### Kann ich einen Freifunk-Knoten mit Bremer Firmware ausserhalb Bremens betreiben?
Erst mal großartig, dass du Freifunk machen möchtest!

Freifunk steht u.a. für Denzentralität. Deshalb wäre es klasse wenn Du Dich einer Community in Deiner Nähe anschließt oder vielleicht sogar Deine eigene gründest. Da aller Anfang schwer ist, macht es für eben diesen vielleicht Sinn sich erst mal einer nahegelegen Gruppe anzuschließen. Auch wir von Freifunk Bremen stehen Dir natürlich gerne mit Rat und Tat zur Seite und mit den existierenden Hilfsmitteln ist die technische Hürde auch nicht mehr ganz so gigantisch.

Es gibt auch technische Gründe, die gegen eine Erweiterung über die Grenzen von Freifunk Bremen hinaus sprechen. Das Problem mit Mesh-Netzen heute ist, dass sie nicht besonders gut skalieren und mit jedem weiteren Router die Leistung nach unten geht.
Betreiben von Bremen firmware in Städten, die bereits ein eigenes Freifunk-Netz haben macht gar kein Sinn. Denn sonst klappt es nicht mit dem Meshen, was ein zentraler Bestandteil von Freifunk ist.

Im Moment kommen ständig neue Freifunk-Gemeinden dazu. Welche Gemeinden es schon gibt, siehts Du in dieser Übersicht.

### Moment, aber ich geh doch mit Freifunk ins Internet! Wieso sagt ihr, ihr seid ein Intranet?
Freifunk soll primär keinen HotSpot-Internetzugang darstellen wie ihn die Telekom oder FON bereits anbietet. Die Vision von Freifunk ist, ein auf WLAN basierendes eigenständiges Netz aufzubauen, ein Bürgernetz. Die Verbindung zum Internet ist daher nur ein zusätzliches optionales Feature.

Unser Anliegen ist also nicht nur, jedem kostenlos Zugang zum Internet zu gewähren, sondern vielmehr ein Funknetzwerk in Bürgerhand aufzubauen, an dem jeder partizipieren kann und das von Niemandem kontrolliert, überwacht oder eingeschränkt werden soll.

## Mitmachen

### Darf ich Freifunk einfach so benutzen?
Ja, Du darfst Freifunk ohne zu bezahlen und schlechtes Gewissen nutzen. Und wenn Du doch eins bekommst, mach mit, indem Du einen Knoten aufstellst. ;)

### Was kostet Freifunk?
Für die Nutzung fallen für Dich keine Kosten an. Falls Du selbst einen Freifunk-Zugang anbieten möchtest benötigst Du neben Deinem eigenen Internetanschluss (falls noch kein anderer Freifunk-Knoten in Reichweite ist) einen passenden Router. Diese kostet je nach Modell ab 20€. Du kannst ihm im Laden kaufen oder von uns bekommen. Die jährlichen Stromkosten für das Betreiben des Routers belaufen sich auf unter 10€, weitere Kosten fallen nicht an.

Auf Seiten unseres Backbones fallen zusätzlich Kosten für die Server und die VPN-Zugänge an. Dies wird momentan durch Privatpersonen finanziert bzw. gespendet. In Zukunft möchten wir unter anderem diese Kosten durch regelmäßige Spenden und Mitgliedsbeiträge decken.

### Ich habe keine Ahnung von Technik. Kann ich dennoch einen Zugangspunkt betreiben?
Die kurze Antwort ist: Ja, Du kannst! Auch wenn Du absolut keine Ahnung von Technik hast, aber dennoch einen Knoten betreiben möchtest, kannst Du über uns einen vorbereiteten Knoten bekommen, den Du nur noch an das Stromnetz (und gegebenenfalls an deinem bereits vorhandenen Internet-Router) anschließen musst. Ein derart vorbereiteter Knoten funktioniert “einfach so”.

### Ich habe ein wenig Ahnung von Technik, aber noch nie ein Gerät geflasht. Ist es schwer, die Freifunksoftware auf den Router aufzuspielen?
Nein, die Installation unserer Software ist nicht schwer und wird von uns so einfach wie möglich gehalten. Wirf doch einfach einen Blick in die [Anleitung](LINK) und entscheide selbst, ob du dir das Flashen zutraust oder nicht.

Bei Rückfragen helfen wir gerne auf einem [Treffen](LINK).

### Wie kann ich bei Freifunk mitmachen?
Es gibt viele Möglichkeiten, sich für Freifunk einzusetzen. Eine einfache, aber effektive Möglichkeit uns zu helfen ist Mundpropaganda: Erzähl Deinen Freund_innen und Deiner Familie von dem Projekt und zeig ihnen, wo und wie sie Freifunk nutzen können.

Du kannst uns auch aktiv unterstützen, indem Du einen eignen Knoten (Zugangspunkt) aufstellst. Du bist herzlich eingeladen zu unseren [Treffen](). Dort können wir dann besprechen, was gerade konkret anliegt und wie du dich auch mit eigenen Ideen einbringen kannst.

### Muss ich zu den Treffen, wenn ich nur einen Router aufstellen möchte oder gelegentlich das WLAN mit meinem Smartphone nutze?
Nein. Freifunk funktioniert auf freiwilliger Basis. Jede_r bringt sich so ein, wie er oder sie es für richtig hält. Eine Verpflichtung besteht nicht.

### Wo bekomme ich einen Router?
[Da](http://wiki.bremen.freifunk.net/Routerboerse)

## Technik

## Ich habe alles angeschlossen und konfiguriert, aber mein Freifunk Router bekommt kein Internet.
Hast Du das Ethernet-Kable von Deinem Heimrouter in den richtigen Port am Freifunkrouter gesteckt? Es muss im **blauen WAN-Port** stecken.

### Lässt sich die original Firmware wieder einspielen?
Ja! Ein bereits in einen Freifunk-Knoten umgewandeltes Gerät kann jederzeit wieder mit der original Hersteller-Firmware geflasht (bespielt) werden und entspricht damit wieder dem Original.

### Wie schnell ist mein Zugang im Freifunk?
Innerhalb des Funknetzes hängt die Geschwindigkeit stark von der Qualität der Funk-Verbindung ab und über wie viele Knoten sie geht. Die Geschwindigkeit der Knoten ins kabelgebundene Netz (z.B. Internet) wird jedoch maßgeblich durch die Prozessor-Leistung der Knoten begrenzt. Denn die müssen den VPN-Tunnel ver- & endschlüsseln, was viel Rechenleistung benötigt. Gemessene Richtwerte pro Modell findest Du [hier](https://projects.universe-factory.net/projects/fastd/wiki/Benchmarks).

### Mein Freifunk-Router spannt ein zweites WLAN mit dem Namen mesh.ffhb auf. Was bedeutet das?
Das zweite WLAN mit einer SSID mesh.ffhb ist ein Ad-hoc-WLAN und dient der Vernetzung der einzelnen Router untereinander. “Sehen” sich zwei Freifunk-Konten in ihrem Empfangsbereich, so nehmen sie über diese WLAN-SSID miteinander Kontakt auf und leiten den Datenverkehr weiter. Wie sprechen dann davon, dass sie “meshen”, der eigentlichen Funktion des Freifunk-Netzes.

### Kann ich den Funkkanal wechseln?
Freifunk arbeitet auf Kanal 6. Da sich die einzelnen WLAN-Knoten nur miteinander vernetzen können, wenn auch alle auf dem selben Kanal funken, macht eine Änderung keinen Sinn. Eine Veränderung des Kanals würde dazu führen, dass ein Router nicht mehr seine Kernfunktion, das “Meshen”, erfüllen kann, es sei denn, alle anderen Router würde auch umgestellt. Sollte es zu Kollisionen mit benachbarten Netzen kommen, schlagen wir den diplomatischen Weg vor, indem man sich mit seinen Nachbarn über die Kanalbelegung abstimmt.

### Kann ich meine Knotendaten (Name, Ort auf der Knotenkarte, etc.) ändern?
Ja! Du kannst diese Daten im Config-Mode (sihe nächste Frage) jederzeit ändern.
Falls du Fernzugriff (SSH) aktiviert hast, lässt sich auch alles über die Konsol ändern (siehe [Freifunk Hamburg Commandline Administration](https://github.com/freifunk-gluon/gluon/wiki/Commandline-administration))

### Wie kann ich meine Knoteneinstellungen ändern?
Config Mode

    Kabel an LAN-Port
    Im Betrieb QSS-Taste bis alle Lampen leuchten, loslassen, neu booten lassen
    Rechner bekommt IP von DHCP
    Netzseite ist erreichbar auf 192.168.1.1

ssh: Wenn du im Config Mode eine Root-Kennwort oder einen ssh-Schlüssel hinterlegt hast geht folgendes…
ssh root@[IPv6-des-Freifunk-Knotens]
Wenn der Knoten am Netz ist, taucht er in dieser Liste auf. Klickst du auf den Knotennamen, siehst du seine IPv6.

OpenWRT Safemode (failsafe), wenn gar nichts mehr geht…

    Kabel an LAN-Port
    Nach Neustart QSS-Taste 3s sobald Zahnrad leuchtet
    Rechner LAN-Port auf 192.168.1.2/24
    telnet 192.168.1.1
    filesystem mounten $ mount_root
    ggf. Kennword aendern: passwd
    

### Wie ist die Belegung der Ports?
Die Standarbelegung für die LAN-Ports (gelb bei TP-Link) ist client-Netz – also für Endgeräte im Freifunknetz, genauso als wären sie per WLAN verbunden.

Der WAN-Port (blau bei TP-Link) macht standardmässig entweder Mesh-VPN (VPN-uplink zum Gateway) und sollte dementsprechend hinter einem Internet-Anschluss hängen, oder Mesh-on-WAN (also meshen per Kabel), solltest du das im Konfigurationsmodus so eingestellt haben.

Näher erklärt werden alle Netzwerkschnittstellen im Wiki.

### Kann ich Uplink über WLAN machen statt über Kabel?
Prinzipiell ja. Allerdings ist es nicht sehr Effizient, da dann schon Mesh, client-Netz, alle clients sowie der Router zu dem als Uplink verbunden wird auf dem selben Kanal funken. Hinzu kommen evtl. Geräte aus der Nachbarschaft, die vielleicht auch auf diesem Kanal sind.

### Kann ich ein privates WLAN parallel auf meinem Freifunk-Knoten herausgeben oder privates Netz über die LAN-Ports?
Dies ist durch editieren der OpenWRT Netzwerkeinstellungen möglich. Jedoch existiert dafür noch keine Anleitung. Wenn du eine gefunden oder geschrieben hast, verknüpfe sie im Wiki.

## Rechtliches

### Kann ich als Knotenbetreiber_in dafür verantwortlich gemacht werden was andere über mein Freifunk tun? (Störerhaftung)
Nein. Der Datenverkehr wird verschlüsselt durch sogenannte Gateway Server getunnelt. Dadurch ist ist der Datenverkehr nicht zu Deinem Anschluss zurückverfolgbar und die sog. 'Störerhaftung' nicht durchsetzbar.

### Darf ich überhaupt WLAN außerhalb meiner Wohnung versenden?
TODO

### Darf ich meinen Internetanschluss überhaupt mit Anderen teilen?

### Wie ist das mit der Sendeleistung? 
TODO
