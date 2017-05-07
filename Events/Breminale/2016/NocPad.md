# Archivierte Version vom NOC-Pad 2016

(kopiert von https://pads.hackerspace-bremen.de/p/ffhb-breminale-2016-noc)


http://c541678.r78.cf2.rackcdn.com/appnotes/bpg-highdensity.pdf

Traditional networks can only solve this problem by trying to be on a different non-overlapping channel. But since there are only 3 in the 2.4 GHz band, this is not realistic. A better solution is to make use of the other channels. These channels do overlap with traditional plans but have a huge benefit: clients that are on these channels do not hear stations on channels 1, 6 or 11. A client on channel 7 does not need to pay attention to a neighboring network transmitting on channels 6 or 11. It freely ignores these irrelevant preambles.  

OFDM only in the 2.4 GHz band (drop support for 802.11b clients) • Disable background scanning by APs • Enable RTS-CTS to mitigate collisions • Limit the number of SSIDs as much as possible to reduce management traffic and overhead • Disable any service that may potentially deny service such as WIPS 

broadcast + multicast filter

https://github.com/freifunk-gluon/gluon/tree/master/package/gluon-ebtables-filter-multicast/files/lib/gluon/ebtables
anpassen für unser netz ( traffic geht nicht auf bat0 raus )

neues modul bauen für broadcast

openwrt:
SSIDs:
max assoc
isolation


Gut: 
remove 802.11b-support, limit wifi-capabilitys to some faster speeds 
https://github.com/freifunk-gluon/gluon/pull/467/files

kick clients with low snr

    https://github.com/bittorf/kalua/blob/master/openwrt-addons/etc/kalua/wifi#L158


https://github.com/bittorf/kalua/blob/master/openwrt-addons/etc/kalua/wifi#L1686
reduce / increase txpower example ( bei uns nach client anzahl )


https://github.com/FreifunkBremen/gluon-site-ffhb
branch breminale2016

https://github.com/FreifunkBremen/ffhb-packages
branch breminale2016

https://github.com/FreifunkBremen/gluon
branch breminale2016

Plan der Stromkabel 2015
https://www.google.com/maps/d/viewer?mid=1ePMbTgT5_khZI3DS5QFdv0tevOU

