# B.A.T.M.A.N-Wechsel für Testing-Nutzer

**Stand: 2022-06-13** 

__Dieser Artikel richtet sich an Nutzer der Testing-Firmware  [2019.1.3+bremen7](https://wiki.bremen.freifunk.net/Firmware/Changelog#2019-1-3-bremen7)__, die helfen wollen, das Bremer Freifunk-Netz schneller zu machen.

## Hintergrund
Eine Website zu öffnen ist für uns meist nur einen Klick entfernt. Technisch gesehen, sind es dutzende kleine Schritte. Damit die Website durch das Freifunk-Netz zu dir geschickt werden kann, muss der Weg über verschiedene Netzwerkgeräte wie Router und Server zu deinem Endgerät bekannt sein. Es muss eine Route existieren. Um dieses "Routing" kümmert sich im Bremer Freifunk-Netz momentan B.A.T.M.A.N in der Version 13 [^versV13]. Die ist nicht mehr ganz taufrisch.

Um unter anderem eine Vielzahl neuer Geräte zu unterstützen, wollen wir auf Gluon 2020 wechseln. Gluon ist die Grundlage unsere Bremer Freifunk-Firmware.
Da diese aber B.A.T.M.A.N v13 nicht mehr unterstützt, müssen wir vorher einen Wechsel auf B.A.T.M.A.N in der Version 15 [^versV15] vollziehen.

## Der Wechsel
Wir wollen sicherstellen, dass B.A.T.M.A.N v15 bei uns fehlerfrei funktioniert. Deshalb bitten wir dich, deine Testing-Router auf die neue B.A.T.M.A.N-Version umzustellen.

__Hinweis__
- Remote first.
Beginne mit Änderungen am entfernten Gerät.
- B.A.T.M.A.N v15 und v13 sind nicht kompatibel. Sie meshen nicht. Stelle bitte sicher, dass alle Router, die per Kabel oder WLAN mit deinem Router meshen, die gleiche Domain ausgewählt haben.

### Wechsel per Weboberfläche

1. Halte den Reset-Knopf etwa 10-15 Sekunden gedrückt, bis alle Lämpchen kurz aufblinken.
2. Öffne die Seite _http://192.168.1.1/_
3. Wähle im Feld _Domain_ die Zeile _Freifunk Bremen - Experimentelles Netz (mit Batman v15)_ aus.
4. Drücke _Speichern und Neustarten_.
5. Zurück über den gleichen Weg, dann wählen wir _Freifunk Bremen - Normales Netz_ aus.

CPE210v3: Gerät nach Reset nicht erreichbar? dann einmal kurz stromlos machen, dann ist das Gerät im Konfigmodus erreichbar.

### Wechsel per SSH
    uci set gluon.core.domain='ffhb_batv15' && gluon-reconfigure && gluon-reload && uci commit && reboot

### Zurück per SSH
    uci set gluon.core.domain='ffhb_11s' && gluon-reconfigure && gluon-reload && uci commit && reboot

## Testen
Sobald ihr auf v15 umgestellt habt, testet das Netz gern auf Herz und Nieren! Vor allem ist interessant, ob mit dem neuen Netz irgendwas nicht funktioniert, was bisher funktioniert hat. Also: lassen sich alle Seiten aufrufen und alle Dienste nutzen, die bisher auch funktioniert haben?

Übrigens: die Geschwindigkeit des neuen Netzes lässt sich nicht wirklich abschätzen.
Einerseits wird das Netz gerade in der Testphase möglicherweise schneller sein, weil dann noch wenig Nutzer unterwegs sind. Andererseits gibt es bisher auch erst zwei VPN-Server für das v15-Netz.
Und einerseits könnte B.A.T.M.A.N v15 effizienter und dadurch schneller sein; andererseits könnte es auch in bestimmten Situationen mehr unnötige Daten übertragen und dadurch langsamer sein.
Im Moment ist die Erwartung, dass die Geschwindigkeit sich durch den Umstieg nicht merklich verändern wird. Falls ihr aber natürlich bemerkt, dass das v15-Netz deutlich langsamer ist, dann gebt gerne Bescheid!

## Rückmeldung der Ergebnisse, und Hilfe
Wenn ihr Rückmeldung geben wollt, oder wenn ihr Fragen habt, dann schreibt das gerne im [Chat](https://webirc.hackint.org/#ircs://irc.hackint.org/#ffhb?nick=Gast_?) oder auf der [Mailingliste](https://lists.bremen.freifunk.net/mailman/listinfo/ff-bremen/),
oder kommt zum [Treffen](/kontakt.html#treffen)!

Die Ergebnisse sammeln wir dann unter [Erfahrungsberichte/Batman v15 Probleme](Erfahrungsberichte/Batman v15 Probleme).


## Fußnoten:

[^versV13]: genauer: "2013.4.0 compat14 mit B.A.T.M.A.N. IV"
[^versV15]: genauer: "2018.1-4 compat15 mit B.A.T.M.A.N. IV"