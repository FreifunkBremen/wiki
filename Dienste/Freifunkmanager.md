Der Freifunkmanager ist eine Software, welche ursprünglich für die Breminale entwickelt wurde.
(Die Software nutzt respondd und basiert auf yanic)

Sie soll das Verwalten von "vielen" Routern vereinfachen und bietet die Möglichkeit Knoten spezifische Änderungen.


Momentan werden nur folgende Einstellungen unterstützt:
- Hostname
- Channel wifi24, wifi5
- TXPower wifi24, wifi5
- Gluon - Position
- Gluon - Owner

Dafür müssen die Knoten den SSH-Key vom Freifunkmanager haben:

```
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAACAQDEX65ZS3thwv+jkWBDeO6vyPO3I+U0iDIqONDpB5mej192Dy9Grddc6+vfK94JLQYKytIHO/qgFhFwK85EyhAeuzbVJ/cf0g4UDosPIvn64/6hPaLmnfyFwIxXNx2E1UQKYgFvghwAOMSw17mJuImxNZ0PAy7Nw9muWL87kSmfEobMKTFe8KIqVIk5pv332rPWV+ZiRwqs2SfG+0GydqKIFEz9injteJUB/TvlIrbGgF7wj3E+Jd88HytSEie/DNRLmd07AJroGRHHS0aoQw8/1txu2xa+xuT62cJkXyfMIhtzGUJ0tlmNXb/UrcBCQUNMUgQgJXCpxXDujVQSB4thV1Rm8fxxouBxOonGg/HiP7I/ZndfgGGpGjXsD5Cn/i8i5GTePwP9CMPgkZU4BmUkrEcr8fuzCIiRUSzzpQJikOsWj+LfP0xwYIaYS7pOmqF6G2CQ1kVA2gtLjPuvpzadZGiRJ5HBG23bEJ6vgF8zAQIOvJXiOe0dWJh7PZ8XTjOCAUImhtsv6l8I61XOqwnI8QqLF0RVmVIso6jM1lWWugrBpE56suJPBQ5MaxF14weMRkWQjsAIY2fdUdDaqiZuZk8+zA0BDepizz17P/WwkS/mjXytIuYoDf2/rj41MzS+F7c2ligSre6yqqnl0NTHmwsm12csdzyegR4Etwah1Q== freifunkmanager
```

Nicht für den normalen Freifunk-Betrieb gedacht, da viele das Passwort haben und beim nächsten Event wieder vorhanden.

## List
In der Listen-Ansicht können wenige Einstellungen, bei dennen Rücksicht auf andere Knoten genommen werden können.

![Listen](http://cloud.ffhb.de/index.php/s/aoZpkKceezMpkRE/download?path=%2Ffreifunkmanager&files=Screenshot%20from%202018-09-01%2019-38-12.png&downloadStartSecret=mqm57caa18q)

## Map
Position können per Drag&Drop live editiert werden,
 zudem können Anhand der linken und rechten Farbe des Rand die Anzahl der Clients dargestellt.

In den Popup werden Clients, Channel und TXPower angezeigt.

![Map](http://cloud.ffhb.de/index.php/s/aoZpkKceezMpkRE/download?path=%2Ffreifunkmanager&files=Screenshot%20from%202018-09-01%2019-37-50.png&downloadStartSecret=lonp5zbnjxe)

## Detail-Ansicht
Der einzige Ansicht, in dem der Owner editiert werden kann.
Außerdem den Knotenname und die Position (hier auch mittels GPS der aufrufenden Browser).

Erreichbar über "Edit" in der Listen und über die URL (`#/{NODEID}`) für Knoten, die später erst erscheinen.

![Detail Ansicht](http://cloud.ffhb.de/index.php/s/aoZpkKceezMpkRE/download?path=%2Ffreifunkmanager&files=Screenshot%20from%202018-09-01%2019-38-26.png&downloadStartSecret=r0m9mxcmm8)

## Stats
Eine Übersicht von den Channel-Verteilung (und die letzte yanic/Global Statistik).

![Stats](http://cloud.ffhb.de/index.php/s/aoZpkKceezMpkRE/download?path=%2Ffreifunkmanager&files=Screenshot%20from%202018-09-01%2019-38-35.png&downloadStartSecret=1ju527al498)