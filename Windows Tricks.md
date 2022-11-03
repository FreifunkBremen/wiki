Hier ein paar Windows Hacks, die man immer wieder benötigt.

Egal wie die Fenster gerade aussehen, dahinter funktionieren sie alle gleich.

## Inhalt

[[_TOC_]]


### Zombie Hardware (serielle USB Schnittstellen und andere)

 Wenn z.B. ein Adapter angestöpselt wird, dann wir er erkannt und im Gerätemanager angezeigt.
 Wenn es aber mal klemmt oder das Gerät nicht funktioniert, weil z.B. etwas anderes verwendet die Hardware.
 
 Dann ist die Wardware im Gerätemanager eingetragen aber nicht sichtbar und verstopft unseren Rechner.
 Dafür bibt es eine Variable, die und unbenutzte Zombies anzeigt.
 Suche im Systemmanager die Umbegungsvariablen und öffne dieses. Dort sind die Variablen für den Benutzter und für das System angezeigt.
 In den Systemvariablen bitte mit NEU die folgenden Variablen anlegen.
 ~~~
 devmgr_show_nonpresent_devices=1
 devmgr_show_details=1
 ~~~
 
 Dann kann im Gerätemanager unter Ansicht, Ausgeblendete Hardware angezeigt werden und siehe da, viele Zombies zum löschen.
 
 Hinweise : 

1.) Die folgenden Eingaben in eine Kommandozeile oder in einem Batch führen ebenfalls zur  Anzeige der Zombies im Gerätemanager :

~~~
set devmgr_show_nonpresent_devices=1
set devmgr_show_details=1
start DEVMGMT.MSC
~~~

2.) Das Verfahren eignet sich auch für andere Gerätetypen; insbesondere auch für inaktive Parallelschnittstellen



**[------------------------------------------------------------------------------------------------------------------------- Zurück zum Inhalt:](#inhalt)**



**[------------------------------------------------------------------------------------------------------------------------- Zurück zum Inhalt:](#inhalt)**



**[------------------------------------------------------------------------------------------------------------------------- Zurück zum Inhalt:](#inhalt)**



**[------------------------------------------------------------------------------------------------------------------------- Zurück zum Inhalt:](#inhalt)**

 