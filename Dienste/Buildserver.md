# Buildserver
Unsere Firmware wird automatisch von unserem [Buildserver](https://jenkins.bremen.freifunk.net/) compiliert, wenn jemand in das [site.conf-Repository auf github](https://github.com/FreifunkBremen/gluon-site-ffhb) pusht.

Wenn der gebaute Commit einen Namen ("Tag") nach dem üblichen Versionsschema hatte (z.B. "v2018.01+bremen1"), wird der Build mit diesem Namen gebaut, mit dem Nightly-Key signiert und anschließend auf den [Download-Server] gepusht.

Erst durch ein manuelles Release auf dem Testing- oder Stable-Branch wird die Firmware automatisch den Routern zum Download angeboten.

[Download-Server]: https://downloads.bremen.freifunk.net/firmware/all/