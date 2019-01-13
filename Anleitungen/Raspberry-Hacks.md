Hacks (Hex) mit dem Raspberry!

(13.1.2019 F_H) Die folgenden Spielereien dienen der Unterhaltung und Bildung. Der Artikel beschreibt meine ersten Schritte mit dem kleinen Kumpel, einem Raspberry 3B+. Da es einige Stolpersteine gibt, kann dies evtl. hilfreich sein. Rückschläge machen keinen Spass und können vermieden werden.

## Inhalt:
[Kaufberatung:](#inhalt_Kaufberatung)

[Netzteil:](#inhalt_Netzteil)

[Alias](#inhalt_alias)

### Kaufberatung:

Soll es nur ein Gerät sein, lohnt sich ein Bundle, damit habe ich alles zusammen für den Betrieb eines Raspberry.

Werden es evtl. mehr Geräte oder es werden ein paar Besonderheiten gewünscht, lohnen sich Einzelteile.

Warum Einzelteile?

Micro-SD: wird mehr Speicher benötigt lohnt eine große Karte.

Netzteil: Das originale Netzteil ist sehr groß und verdeckt benachbarte Steckdosen einer Leiste. Das schmale EU-Netzteil 2,5A 5,1V ist besser.

Netzteil: Anker USB Netzteil, 6A 6*5,0V Kabel mit Flachgeräte-Stecker.

Netzteil: Netzteile < 5,1V Raspi Hack erforderlich (s.u.)

Gehäuse: von Formschön bis Wasserdicht alles möglich.

Gehäuse: evtl. nicht präzise für 3B+ passend, Dremel erfordelich.

Kühlkörper: sind immer gut und es gibt sie in Schick, Kupfer / vergoldet.

Lüfter: Es gibt besonders Geräuscharme Lüfter, Lüfter sind nicht erfordelich.

### Netzteil:
Wird auf dem Monitor ein roter Blitz rechts oben eingeblendet, so liegt eine Unterspannung vor. Eine schlimme Folge ist, die Taktfrequenz wird runtergesetzt und der Pi ist deutlich langsamer.

Kann das Netzteil genug Strom liefern, so kann die Überwachung auf Unterspannung abgeschaltet werden.

Mit den Editor nano im Terminalfenster die Datei config.txt öffnen
~~~
sudo nano /boot/config.txt

avoid_warnings=2
~~~

~~~
~~~

