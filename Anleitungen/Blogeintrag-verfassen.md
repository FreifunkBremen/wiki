# Blogeintrag verfassen


## Markdown Spezialitäten zu beachten
Im Gegensatz zum Github-Markdown, verhält sich unsere Website leicht anders, deswegen ist die Vorschau beim Website-Editor bei Github, nicht imme korrekt:
Hier nun einige Beispiele, es sollte eine korreckte Beipielanzeige dargestellt werden, danach ein Codefeld mit zugehöriger Syntax. 

Als `Kopiervorlage`
~~~
Als `Kopiervorlage` Ticks Shift&Apostroph
~~~

oder _Kursiv_ oder **Fett**

~~~
oder _Kursiv_ oder **Fett**
~~~


- vor Listen muss eine Freizeile gelassen werden

~~~
- vor Listen muss eine Freizeile gelassen werden
~~~

----

~~~
---- 4 Minus erzeugt eine Trennlinie
~~~


## Inhalt:
- [Kapitel 1](#kapitel-1)
- [Kapitel 1.1](#kapitel-1-1)
  - [Kapitel 2](#kapitel-2)
  - [Kapitel 2.1](#kapitel-2-1)

## Kapitel 1
### Kapitel 1.1
## Kapitel 2
### Kapitel 2.1

~~~
## Inhalt:  (Leerzeichen zwischen # und Text)
- [Kapitel 1](#kapitel-1)  (Leerzeichen Sonderzeichen durch Minus Ersetzen)
- [Kapitel 1.1](#kapitel-1-1)
  - [Kapitel 2](#kapitel-2)   (Einrücken erzeugt Untermenüs)
  - [Kapitel 2.1](#kapitel-2-1)

## Kapitel 1
### Kapitel 1.1
## Kapitel 2
### Kapitel 2.1
~~~

----

[[_TOC_]]

~~~
\[\[_TOC_]]
Diese Angabe ohne \ erzeugt automatisch ein Inhaltsverzeichnis aus allen 
Überschriften die mit # ## ### beginnen.
~~~

----

## Bilder Einfügen und Verlinken

![WLAN Dipol](http://martybugs.net/wireless/images/ducky_element_tn.jpg)

Normale WLAN-Antenne 2,4 Ghz

~~~
![WLAN Dipol](http://martybugs.net/wireless/images/ducky_element_tn.jpg)

Normale WLAN-Antenne 2,4 Ghz  :  Externer Link
~~~

----
**Bilderbeispiel:**
<img src="https://cloud.ffhb.de/index.php/s/ZqyafdpgQtLbaAM/preview" width="300">
<img src="https://cloud.ffhb.de/index.php/s/sdqW6Arpf2mdE4y/preview" width="300">
![cp210-UART](https://cloud.ffhb.de/index.php/s/sdqW6Arpf2mdE4y/preview)
<img src="https://cloud.ffhb.de/index.php/s/2EHadHt3rZjeiAR/preview">

~~~
**Bilderbeispiel:**
<img src="https://cloud.ffhb.de/index.php/s/ZqyafdpgQtLbaAM/preview" width="300">
<img src="https://cloud.ffhb.de/index.php/s/sdqW6Arpf2mdE4y/preview" width="300">
![cp210-UART](https://cloud.ffhb.de/index.php/s/sdqW6Arpf2mdE4y/preview)
<img src="https://cloud.ffhb.de/index.php/s/2EHadHt3rZjeiAR/preview">
~~~


~~~
Diese Umrandung ist dabei wichtig:
![Bild](#/preview)   Ersetze das # durch den Link.
<img src="#/preview">
~~~


----
