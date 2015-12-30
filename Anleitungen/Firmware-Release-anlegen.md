# Firmware Release anlegen
Um später nachvollziehen zu können, aus welchen Dateien in welchem Zustand eine Firmware gebaut wurde, können im Git Repository Tags angelegt werden. Github interpretiert diese als Releases , listet sie seperat auf und bietet sie gepackt zum Download an.

Die Bennenung der Tags folgt dem Schema der [[Firmware-Versionen|/Firmware/Changelog]]. Da es auch Tags ohne Bezug zu Firmware-Versionen gibt, wird einem Versions-Tag ein `v` vorangestellt. Tilden (`~`) werden durch Bindestriche (`-`) ersetzt


## Tag anlegen
Der Befehl `git tag [TAGNAME]` legt einen (einfachen) Tag, in dem Zustand, in dem sich das lokale Repository gerade befindet (Branch, commit), an.


## angelegten Tag zum remote repository pushen
Mit dem Befehl `git push origin [TAGNAME]` wird ein einzelner Tag gepushed.


## signierte Tags
Um Tags signieren zu können, muss `gpg` eingerichtet werden.

##### bestehenden privaten Key importieren
Der Key wird mit `gpg --import [KEYFILENAME]` importiert.  

##### Schlüssel in *gitconfig* hinterlegen
Mit `gpg --list-secret-keys` werden alle privaten Schlüssel angezeigt.

Beispiel:
```
$ gpg --list-secret-keys
~/.gnupg/secring.gpg
---------------------------------
sec   XXXXX/[KEYID] JAHR-MONAT-TAG
uid                  Max Mustermann <Max@Mustermann.de>
ssb   XXXXX/[KEYID] JAHR-MONAT-TAG
```

Die Key-ID wird dann in der `git config` hinterlegt werden, um bei Signieren verwendet werden zu können:
`git config --global user.signingkey [KEYID]`

##### signierten Tag erstelleni
Ein signierter Tag wird mit dem Parameter `-s` erstellt: `git tag -s [TAGNAME] -m [TAGMESSAGE]`

Da ein signierter Tag nicht mehr *einfach*, sondern *kommentiert* ist, muss eine Tag-Message eingegeben werden. In den meisten Fällen reicht es aus den Namen des Tags erneut anzugeben.


## Tag löschen (remote)
Ist ein Fehler unterlaufen, wie ein falscher Tag-Name, oder der Tag nicht mehr benötigt, so kann dieser wie folgt gelöscht werden:
```
git tag -d 12345
git push origin :refs/tags/12345
```