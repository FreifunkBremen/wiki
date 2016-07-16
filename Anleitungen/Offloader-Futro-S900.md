E N T W U R F (wird erweitert)

Alternative zum Futro S550 kann man auch den Futro S900 benutzen. Den Futro-S900 bekommt man in der Bucht füf 19€. Er benutzt als Speichermedium statt der CFcard eine mSATA, die noch hinzu gekauft werden muss.

Bei mir kommt z.Zt. eine SanDisk 32GByte aus der Bucht für €20 zum Einsatz. Es war die kleinste, die ich auf die Schnelle gefunden habe.

Der Rest läuft in der gleichen Weise ab. Es werden benötigt:

1. Risercard
2. Netzwerkkarte

Die Installation läuft genau so wie beim Futro S550 ab. Auf dem USB-Stick muss aber die
~~~
bitte_nicht_loeschen.sh
~~~

geändert oder erweitert werden. Da das script auf die in den Futro-S550 vorhandenen CPU-Typen prüft, muss der neue CPU-Typ ergänzt oder einer der beiden S550-Typen überschrieben werden.

Der Eintrag lautet:

~~~
if (grep -Fq "AMD G-T44R Processor" /proc/cpuinfo) ; then
  echo "AMD G-T44R Processor -> Futro S900"
~~~