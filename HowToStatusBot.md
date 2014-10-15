In diesem HowTo soll beschrieben werden wie der StatusBot installiert und bedient wird.

* 1. Voraussetzungen überprüfen
  * 1.1 [[Pruefen Voraussetzung fuer Willie]]
* 2. Installation Basispaket (Willie) beschreiben
  * 2.1 Basissystem
    * 2.1.1 LinuxMint 17 Server 64bit
  * 2.2 Softwarepakete installieren (Debian)
    * 2.2.1 python, pip, sqlite, ...
  * 2.3 Softwarepakete installieren (python)
    * 2.3.1 willie
  * 2.4 einrichten beim ersten Start oder später mit "willie -w" zum ändern
      * Enter the nickname for your bot [Willie]: Willie_ffhb
      * Enter the server to connect to [irc.dftba.net]: irc.hackint.eu
      * Should the bot connect with SSL (y/n)? [n]
      * Enter the port to connect on [6667]:
      * Enter your own IRC name (or that of the bot's owner): HeinzBoettjer
      * Enter the channels to connect to by default, one at a time. When done, hit enter again.
Channel: #ffhb_Maschinenraum
      * Channel:
      * Would you like to set up a settings database now (y/n)? [n] y
      * What type of database would you like to use? (sqlite/mysql/postgres) [sqlite]:
      * Location for the database file: willieDatenbank.sqlite
      * Would you like to see if there are any modules that need configuring (y/n)? [n] y
      * Configure meetbot (y/n)? [n] y
      * Path to meeting logs storage directory (should be an absolute path, accessible on a webserver): /var/www/meeting_logs
      * Base URL for the meeting logs directory (eg. http://example.com/logs): localhost/logs
      * Error loading ip: No module named pygeoip (in config.py)
      * Configure radio module (y/n)? [n]
      * Exclude certain URLs from automatic title display (y/n)? [n]
      * Preferred time zone (http://dft.ba/-tz) [UTC]:
      * ...

* 3. Installation Erweiterung Paderborn installieren
  * 3.1 ToDo
* 4. Programmierung Erweiterung Bremen
  * 4.1 In Planung, Wunschtermin 30.06.2015
* 5. Portierung Basispaket auf RasPi
  * 5.1 In Planung, Wunschtermin 31.12.2014
* 6. Portierung Erweiterung Paderborn auf RasPi
  * 6.1 In Planung, Wunschtermin 31.03.2015
* 7. Dokumentation Befehlsübersicht
  * 7.1 Willie (.)
    * .dice
    * .tell <nick> <message>
    * .ask <nick> <message>
    * ...
  * 7.2 Paderborn (!)
    * !info <name>
    * !hamburg
    * !status
    * ...
  * 7.3 Bremen (§)
    * §bremen
    * §paderborn
    * §deutschland
    * ...
* 8.  Publizieren