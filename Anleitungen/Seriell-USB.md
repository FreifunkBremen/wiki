Informationen zu seriellen USB Adaptern. **(WIKI-Eintrag in Arbeit 4/2024)**
## Inhalt
[[_TOC_]]

### Einleitung

Hier einige Bilder von verfügbaren TTL-USB Adaptern.
Preise liegen zwischen 1 - 5 Euro.
Beim Basteln haben wir mal wieder festgestellt, 1 Jahr nichts geflasht, schon sind wir wieder Anfänger.
Bitte keine USB Verlängerungskabel verwenden, die Goldrandlösung ist das RASPI UART und eine Stiftleiste.
Löten müssen wir sowieso, auf die Platine werden die 4 Pins, die wir von der Leiste abbrechen, eingelötet.
Den RASPI UART können wir dan direkt anstöpseln RX, TX, GND.

### Treiber installieren.

Einige Chipsätze benötigen Treiber. Diese bitte installieren und den enstehenden COM Port im Gerätemanager einstellen. Ein COM85 wird keinem nützen. Der RASPI UART wird manchmal hochgezählt, Auch hier im Gerätemanager eingreifen.

**[------------------------------------------------------------------------------------------------------------------------- Zurück zum Inhalt:](#inhalt)**

### UART Modelle

|  USB-TTL UART PL3203 | USB-TTL UART CP2102 |  USB-A TTL UART CP2102  |
|---|---|---|
| <img src="https://cloud.ffhb.de/index.php/s/fXe9j9JAMFRLQsf/preview" title="USB-TTL UART PL3203"  width="300" />  | <img src="https://cloud.ffhb.de/index.php/s/x2WzaaeWx44s3pW/preview" title="USB-TTL UART CP2102" width="300" />  | <img src="https://cloud.ffhb.de/index.php/s/6JXZqaLjSDiQtgy/preview" title="USB-TTL UART" width="300" />  |

| Federleiste | Raspi UART  | PIN Beispiel  |
|---|---|---|
| <img src="https://cloud.ffhb.de/index.php/s/E84MMBPGjMdzxd7/preview" title="USB-TTL UART" width="300" />  | <img src="https://cloud.ffhb.de/index.php/s/LJja8Qi9geKRNXT/preview" title="USB-TTL UART" width="300" />  | <img src="https://cloud.ffhb.de/index.php/s/aXX6bstTTfMm4AX/preview" title="USB-TTL UART" width="300" />  |

**[------------------------------------------------------------------------------------------------------------------------- Zurück zum Inhalt:](#inhalt)**

### Welche Baudrate ?

Freifunkrouter verwenden wie auch alle anderen Router eine Baudrate von 115200 8 N 1

Weitergehende Informationen [Hier](https://openwrt.org/docs/techref/hardware/port.serial): https://openwrt.org/docs/techref/hardware/port.serial


**[------------------------------------------------------------------------------------------------------------------------- Zurück zum Inhalt:](#inhalt)**

### Pinbelegung

Bitte die Pinbelegung über https://www.opemwrt.org/toh abfragen. Dort sind alle Daten und Fotos zu den einzelnen Modellen verlinkt. Auch wie ein Gehäuse geöffnet wird.

**[------------------------------------------------------------------------------------------------------------------------- Zurück zum Inhalt:](#inhalt)**

