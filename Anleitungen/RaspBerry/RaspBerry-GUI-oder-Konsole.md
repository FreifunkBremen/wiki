Raspberry Pi: Benutzeroberfläche einstellen, Gui oder Konsole starten.

Sie möchten dass Ihr Raspberry Pi mit der Kommandozeile startet oder Sie möchten, das automatisch die grafische Benutzeroberfläche gestartet wird.
Generell kann man das mit dem Tool "raspi-config" einstellen. 

Es geht aber auch nur auf der Kommandozeile.

Schauen wir erst einmal nach, was aktuell gestartet wird. Das steht in der ersten Zeile.

~~~
systemctl show default.target
~~~

Wenn die Ausgabe in der ersten Zeile "Id=multi-user.target" ergibt, dann startet der Raspberry Pi mit der Kommandozeile. 
Wenn die Ausgabe in der ersten Zeile "Id=graphical.target" ergibt, dann startet der Raspberry Pi mit der grafischen Benutzeroberfläche.

Beenden Sie die Anzeige mit STRG + C:

Was soll gestartet werden?

Wenn die Kommandozeile gestartet werden soll:

~~~
sudo systemctl set-default multi-user.target
~~~

Wenn die grafische Benutzeroberfläche gestartet werden soll:

~~~
sudo systemctl set-default graphical.target
~~~

Danach ist ein Neustart notwendig.
~~~
reboot
~~~
