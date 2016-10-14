Wenn man der Software, Hardware oder Administration eines Freifunk-Knoten nicht vertrauen möchte ist es kein Problem, den Knoten am Gastzugang einer Fritzbox zu betreiben. Dort hat er keinen Zugriff auf die anderen Geräte im LAN und auch seinen Internetzugang kann man stark einschränken. Folgende Schritte sind dafür notwendig:

1. Eine aktuelle Firmware auf der Fritzbox installieren. Diese Anleitung wurde für Fritz!OS 06.21 geschrieben, kann aber auch bei älteren Versionen funktionieren. Ggf. sind jedoch die Klickpfade im Webinterface dann anders.
2. Freifunk-Knoten an LAN-Port 4 anschließen. Dies ist leider der einzige, der als "Gastzugang" konfiguriert werden kann.
3. Heimnetz → Heimnetzübersicht → Netzwerkeinstellungen → „Gastzugang für LAN 4 aktiv“ aktivieren. Ggf. „Anmeldung am Gastzugang nur nach Zustimmung zu den Nutzungsbedingungen gestatten“ deaktivieren.
4. Internet → Filter → Listen → Netzwerkanwendung hinzufügen
    1. Netzwerkanwendung „Alles außer Freifunk-VPN“
    2. Neues Protokoll → Protokoll „UDP“, Quellport „beliebig“, Zielport „Port 1 bis 49999“ → OK
    3. Neues Protokoll → Protokoll „UDP“, Quellport „beliebig“, Zielport „Port 50001 bis 65535“ → OK
    4. Neues Protokoll → Protokoll „TCP“, Quellport „beliebig“, Zielport „beliebig“ → OK
    5. OK
5. Internet → Filter → Zugangsprofile → Neues Zugangsprofil
    * Name: Freifunk-Knoten
    * Zeitraum: immer
    * Zeitbudget: unbegrenzt
    * Nutzung des Gastzugangs gesperrt: nein
    * Internetseiten filtern: nein
    * Gesperrte Netzwerkanwendungen: die eben angelegte „Alles außer Freifunk-VPN“
    * OK
6. Internet → Filter (→ Kindersicherung): Dem Freifunk-Knoten das Profil „Freifunk-Knoten“ zuordnen.