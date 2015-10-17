#!/bin/sh
	clear
#__________________________________________________________________________________________________
	if [ $# -eq 0 ]; then Modus=0; else Modus=$1; fi
	echo	"________________________________________________________________________________"
#__________________________________________________________________________________________________
	if [ $Modus -eq 4 ]; then
	echo	"Anzahl Parameter	#	$#"
	echo	"Name			0	$0"
	echo	"Parameter 1		1	$1"
	echo	"Parameter 2		2	$2"
	echo	"Alle Parameter		@	$@"
	echo 	"Alle Parameter		*	$*"
	echo 	"PID			$	$$"
	echo	"Rückkehrcode		?	$?"
	echo	"________________________________________________________________________________"
	echo	"Value 127 is returned by /bin/sh when the given command is not found within your"
	echo	"PATH system variable and it is not a built-in shell command. In other words, the"
	echo	"system doesn't understand your command, because it doesn't know where to find"
	echo	"the binary you're trying to call."
	echo	"________________________________________________________________________________"
	exit 4
	fi
#__________________________________________________________________________________________________
	if [ $Modus -eq 3 ]; then
	echo	"Parameter	Bedeutung"
	echo	" /0		Stiller Modus, nur die notwendigen Informationen"
	echo	"1		Verbose, Ausgabe aller Informationen"
	echo	"2		Nur Ausgabe der Version"
	echo	"3		Diese Hilfe"
	echo	"4		Zusätzliche Informationen"
	echo	"8		Installieren Software"
	echo	"9		Entfernen Software"
	echo	"________________________________________________________________________________"
	exit 3
	fi
#__________________________________________________________________________________________________
	if [ $Modus -eq 2 ]; then
	echo	"Prüfen Voraussetzungen Version 0.1 für Willie 4.5.1"
	echo	"________________________________________________________________________________"
	echo	"Author: Heinz Boettjer			Kontakt: Heinz.Boettjer@freenet.de"
	echo	"________________________________________________________________________________"
	echo	"This work is licensed under the Creative Commons Attribution-ShareAlike 4.0"
	echo	"International License. To view a copy of this license, visit"
	echo	"http://creativecommons.org/licenses/by-sa/4.0/. Author Heinz Boettjer"
	echo	"________________________________________________________________________________"
	exit 2
	fi
#__________________________________________________________________________________________________
	if [ $Modus -eq 8 ]; then
	sudo apt-get install python-pip sqlite libsqlite0
	sudo pip install https://pypi.python.org/packages/source/w/willie/willie-4.5.1.tar.gz pygeoip praw ipython
	exit 8
	fi
#__________________________________________________________________________________________________
	if [ $Modus -eq 9 ]; then
	sudo pip uninstall ipython praw pygeoip willie
	sudo apt-get remove libsqlite0 sqlite python-pip
	exit 9
	fi
#__________________________________________________________________________________________________
	if [ $Modus -eq 1 ]; then
	echo	"python -V							0	???"
	fi
	python -V			> /dev/null	2> /dev/null
	Status_python=$?
#__________________________________________________________________________________________________
	if [ $Modus -eq 1 ]; then
	echo	"________________________________________________________________________________"
	echo	"pip -V								0	127"
	echo	"Installation:		sudo apt-get install python-pip"
	fi
	pip -V				> /dev/null	2> /dev/null
	Status_pip=$?
#__________________________________________________________________________________________________
	if [ $Modus -eq 1 ]; then
	echo	"________________________________________________________________________________"
	echo	"sqlite	-version						1	127"
	fi
	sqlite -version			> /dev/null	2> /dev/null
	Status_sqlite=$?
#__________________________________________________________________________________________________
	if [ $Modus -eq 1 ]; then
	echo	"________________________________________________________________________________"
	echo	"mysqlcheck -V							0	127"
	echo	"Installation:		sudo apt-get install mysql-client-core-5.6"
	fi
	mysqlcheck -V			> /dev/null	2> /dev/null
	Status_mysqlcheck=$?
#__________________________________________________________________________________________________
	if [ $Modus -eq 1 ]; then
	echo	"________________________________________________________________________________"
	echo	"postgres -V							0	127"
	echo	"Installation:		sudo apt-get install postgres-xc-client postgres-xc libpq5"
	echo	"Deinstallation: 	sudo apt-get remove postgres-xc-client postgres-xc libpq5"
	echo	"			(Reihenfolge wichtig)"
	fi
	postgres -V			> /dev/null	2> /dev/null
	Status_postgres=$?
#__________________________________________________________________________________________________
	if [ $Modus -eq 1 ]; then
	echo	"________________________________________________________________________________"
	echo	"willie installiert						ja	nein"
	fi
	if [ -f /usr/local/bin/willie ]; then Status_willie="ja"; else Status_willie="nein"; fi
#__________________________________________________________________________________________________
	if [ $Modus -eq 1 ]; then
	echo	"________________________________________________________________________________"
	echo	"pygeoip installiert						ja	nein"
	fi
	if [ -d /usr/local/lib/python2.7/dist-packages/pygeoip ]; then Status_pygeoip="ja"; else Status_pygeoip="nein"; fi
#__________________________________________________________________________________________________
	if [ $Modus -eq 1 ]; then
	echo	"________________________________________________________________________________"
	echo	"praw installiert						ja	nein"
	fi
	if [ -d /usr/local/lib/python2.7/dist-packages/praw ]; then Status_praw="ja"; else Status_praw="nein"; fi
#__________________________________________________________________________________________________
	if [ $Modus -eq 1 ]; then
	echo	"________________________________________________________________________________"
	echo	"praw installiert						ja	nein"
	echo	"________________________________________________________________________________"
	fi
	if [ -d /usr/local/lib/python2.7/dist-packages/IPython ]; then Status_ipython="ja"; else Status_ipython="nein"; fi
	echo	"python: 		$Status_python	muss 0 sein"
	echo	"pip:			$Status_pip	muss 0 sein"
	echo	"sqlite: 		$Status_sqlite	muss 1 sein"
	if [ $Modus -eq 1 ]; then
	echo	"mysqlcheck:		$Status_mysqlcheck	0=installiert 127=nicht installiert"
	echo	"				egal da dieser Ablauf auf sqlite abgestimmt ist"
	echo	"postgres:		$Status_postgres	0=installiert 127=nicht installiert"
	echo	"				egal da dieser Ablauf auf sqlite abgestimmt ist"
	fi
	echo	"willie  installiert:	$Status_willie"
	echo	"pygeoip installiert:	$Status_pygeoip"
	echo	"praw    installiert:	$Status_praw"
	echo	"ipython installiert:	$Status_ipython"
	echo	"________________________________________________________________________________"

	if [ $Modus -eq 1 ]; then exit 1; else exit 0; fi
