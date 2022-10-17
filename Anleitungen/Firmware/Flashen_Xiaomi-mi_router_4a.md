Evtl. wird das der neue Butter & Brot Freifunk Router. Es wird ein Nachfolger für 4Mb Geräte wie den TP-Link WR841 gesucht.
Preis und Leistung des Xiaomi 4A Gigabit Edition sind Beeindruckend. Hier mein Eindruck zu dem Gerät.

### Mein Ergebnis vorab: Als Bürgergerät ungeeignet, Bastelkiste. Das Gerät ist was für Freifunkbastler. Stand 15.10.2022

## Inhalt

[[_TOC_]]

### 1.) "XR4A XIAOMI Mi Router 4A Gigabit Edition"

Information: gibt's in zwei Varianten (100Mbit und Gigabit)
kostet zwischen 15€ (100MBit) und 35€ (Gbit)
https://www.mi.com/de/product/mi-router-4a-gigabit-edition/
https://openwrt.org/toh/xiaomi/mi_router_4a_mir4a_100m
https://openwrt.org/inbox/toh/xiaomi/xiaomi_mi_router_4a_gigabit_edition
Verfügbarkeit:
    gibt's derzeit bei Amazon, Ebay
    gibt's derzeit aber nicht bei MediaMarkt etc.
wird von der neusten Gluon-Version unterstützt (s. https://gluon.readthedocs.io/en/latest/releases/v2022.1.html#added-hardware-support)
es gibt auch eine inoffizielle Freifunk-Bremen-Firmware für dieses Gerät: https://code.bremen.freifunk.net/ffhb/firmware/gluon-site-ffhb/-/jobs/1497/artifacts/file/gluon/output/images/sysupgrade/gluon-ffhb-2019.1.3+bremen9-build137-xiaomi-mi-router-4a-gigabit-edition-sysupgrade.bin



**[------------------------------------------------------------------------------------------------------------------------- Zurück zum Inhalt:](#inhalt)**


### 2.) Xiaomi Mi Router 4A (MIR4A) Gbit

Achtung: Unterschiedliche Routerhardware. (Xiaomi Mi Router 4A (MIR4A) 100M) ist nicht (Xiaomi Mi Router 4A (MIR4A) Gbit)

Warnung Xiaomi liefert seit 2020 Mi Router 4A Gigabit Edition-Geräte ohne angemessene Abschirmung aus. Beachten Sie, dass diese aufgrund von Funkstörungen Probleme verursachen können. 

Warnung 03/2022 OpenWrt funktioniert derzeit nicht auf Geräten mit Eon- oder CFeon-Flash-Chips. [Klicken Sie auf den Link.](https://openwrt.org/inbox/toh/xiaomi/xiaomi_mi_router_4a_gigabit_edition#unable_to_install_openwrt_to_new_r4a_gigabit_edition) 
Es wurden keine Probleme mit Winbond- oder GigaDevice-Flash-Chips gemeldet, die in früher hergestellte Einheiten eingebaut wurden. Andere Unterschiede wurden auch bei dem chinesischen Modell beobachtet, das im September 2021 hergestellt wurde. [Klicken Sie auf Link](https://forum.openwrt.org/t/observations-on-xiaomi-mir4ag-newer-firmware/127373)

Warnung 10/2022 Xiaomi liefert derzeit v2 der 4A-Gigabit-Edition aus, die anhand der FW-Version 2.30.20 und des Namens identifiziert werden kann, wenn ihr eine IP von einem DHCP (nicht Ihren ISPs) über den WAN-Port, MiWiFi-R4AV2, zugewiesen wird. Dieses Modell kann nicht mit Openwrt geflasht werden. [Klicken Sie auf Link.](https://forum.openwrt.org/t/support-for-xiaomi-router-ac1200-rb02/124962)

Achtung: Gbit ports sind 3 (1x WAN, 2x LAN) und nicht 2xWAN, 1xLAN

Achtung: Die Buchsen haben keine Aussparung für das LAN Kabel, könnte eng werden. Die Abbildungen in der Bedienungsanleitung sind Spegelverkert und habenen einige Schreibfehler.



**[------------------------------------------------------------------------------------------------------------------------- Zurück zum Inhalt:](#inhalt)**

### 3. SSH FTP Telnet Zugang

Alle Zugänge sind deaktiviert, auch keine seriellen Ausgaben auf der Konsole.

**[------------------------------------------------------------------------------------------------------------------------- Zurück zum Inhalt:](#inhalt)**

### 4. TTL UART
Als erstes löte ich einige Kabel an die UART-Pins auf der Platine und verbinde sie mit einem TTL-zu-USB-Adapter. 
So sollte man die übliche Linux-Ausgabe von einem Router sehen, aber leider kommt da nichts: 
Ich kann U-Boot nicht daran hindern, automatisch zu booten, und ich kann die Befehlszeilenschnittstelle 
nicht aufrufen, sobald die Standard-Firmware gebootet hat.

Nachdem das Gerät auf die Bremer FF Sw geflasht ist, zeigte ein serieller Adapter folgende Ausgabe:

~~~pre{white-space: pre !important; overflow-y: scroll !important; max-height: 100px !important;}<pre class="table" style="max-height: 100px;">

/bin/ash: üø: not found
root@ffhb-64644adb97c2-XIAOMI-Mi-Router-4A-Gigabit-Edition:/# 
root@ffhb-64644adb97c2-XIAOMI-Mi-Router-4A-Gigabit-Edition:/# 
root@ffhb-64644adb97c2-XIAOMI-Mi-Router-4A-Gigabit-Edition:/# 
root@ffhb-64644adb97c2-XIAOMI-Mi-Router-4A-Gigabit-Edition:/# **reboot**
root@ffhb-64644adb97c2-XIAOMI-Mi-Router-4A-Gigabit-Edition:/# [162308.891283] device client0 left promiscuous mode
[162308.896326] br-client: port 5(client0) entered disabled state
[162309.115048] device client1 left promiscuous mode
[162309.120175] br-client: port 6(client1) entered disabled state
[162309.670944] batman_adv: bat0: Interface deactivated: primary0
[162309.676866] batman_adv: bat0: Removing interface: primary0
[162309.711517] batman_adv: bat0: Interface deactivated: mesh0
[162309.717160] batman_adv: bat0: Removing interface: mesh0
[162309.813013] batman_adv: bat0: Interface deactivated: mesh1
[162309.818671] batman_adv: bat0: Removing interface: mesh1
[162313.140210] batman_adv: bat0: Interface deactivated: mesh-vpn
[162313.146092] batman_adv: bat0: Removing interface: mesh-vpn
[162313.156954] br-client: port 4(bat0) entered disabled state
[162313.169972] device bat0 left promiscuous mode
[162313.174466] br-client: port 4(bat0) entered disabled state
[162313.385844] br-client: port 3(local-port) entered disabled state
[162314.051449] device lan1 left promiscuous mode
[162314.056334] br-client: port 1(lan1) entered disabled state
[162314.112054] device lan2 left promiscuous mode
[162314.116986] br-client: port 2(lan2) entered disabled state
[162314.160845] device local-port left promiscuous mode
[162314.165972] br-client: port 3(local-port) entered disabled state
[162314.859150] device wan left promiscuous mode
[162314.863858] br-wan: port 1(wan) entered disabled state
[162314.960271] mtk_soc_eth 1e100000.ethernet eth0: Link is Down
[162320.708029] reboot: Restarting system

===================================================================
     		MT7621   stage1 code Oct 28 2018 20:39:32 (ASIC)
     		CPU=500000000 HZ BUS=166666666 HZ
==================================================================
Change MPLL source from XTAL to CR...
do MEMPLL setting..
MEMPLL Config : 0x11100000
3PLL mode + External loopback
=== XTAL-40Mhz === DDR-1200Mhz ===
PLL4 FB_DL: 0xa, 1/0 = 557/467 29000000
PLL3 FB_DL: 0x12, 1/0 = 679/345 49000000
PLL2 FB_DL: 0x16, 1/0 = 757/267 59000000
do DDR setting..[01F40000]
Apply DDR3 Setting...(use customer AC)
          0    8   16   24   32   40   48   56   64   72   80   88   96  104  112  120
      --------------------------------------------------------------------------------
0000:|    0    0    0    0    0    0    0    0    0    0    0    0    0    0    0    0
0001:|    0    0    0    0    0    0    0    0    0    0    0    0    0    0    0    0
0002:|    0    0    0    0    0    0    0    0    0    0    0    0    0    0    0    0
0003:|    0    0    0    0    0    0    0    0    0    0    0    0    0    0    0    0
0004:|    0    0    0    0    0    0    0    0    0    0    0    0    0    0    0    0
0005:|    0    0    0    0    0    0    0    0    0    0    0    0    0    0    0    0
0006:|    0    0    0    0    0    0    0    0    0    0    0    0    0    0    0    0
0007:|    0    0    0    0    0    0    0    0    0    0    0    0    0    0    0    0
0008:|    0    0    0    0    0    0    0    0    0    0    0    0    0    0    0    0
0009:|    0    0    0    0    0    0    0    0    0    0    0    0    0    0    0    0
000A:|    0    0    0    0    0    0    0    0    0    0    0    0    0    0    0    0
000B:|    0    0    0    0    0    0    0    0    0    0    0    0    0    0    0    0
000C:|    0    0    0    0    0    0    0    0    0    0    0    0    0    0    0    0
000D:|    0    0    0    0    0    0    0    0    0    0    0    0    0    0    1    1
000E:|    0    0    0    0    0    0    0    0    1    1    1    1    1    1    1    1
000F:|    0    0    0    0    1    1    1    1    1    1    1    1    1    1    0    0
0010:|    1    1    1    1    1    1    1    1    0    0    0    0    0    0    0    0
0011:|    1    1    1    0    0    0    0    0    0    0    0    0    0    0    0    0
0012:|    0    0    0    0    0    0    0    0    0    0    0    0    0    0    0    0
0013:|    0    0    0    0    0    0    0    0    0    0    0    0    0    0    0    0
0014:|    0    0    0    0    0    0    0    0    0    0    0    0    0    0    0    0
0015:|    0    0    0    0    0    0    0    0    0    0    0    0    0    0    0    0
0016:|    0    0    0    0    0    0    0    0    0    0    0    0    0    0    0    0
0017:|    0    0    0    0    0    0    0    0    0    0    0    0    0    0    0    0
0018:|    0    0    0    0    0    0    0    0    0    0    0    0    0    0    0    0
0019:|    0    0    0    0    0    0    0    0    0    0    0    0    0    0    0    0
001A:|    0    0    0    0    0    0    0    0    0    0    0    0    0    0    0    0
001B:|    0    0    0    0    0    0    0    0    0    0    0    0    0    0    0    0
001C:|    0    0    0    0    0    0    0    0    0    0    0    0    0    0    0    0
001D:|    0    0    0    0    0    0    0    0    0    0    0    0    0    0    0    0
001E:|    0    0    0    0    0    0    0    0    0    0    0    0    0    0    0    0
001F:|    0    0    0    0    0    0    0    0    0    0    0    0    0    0    0    0
DRAMC_DQSCTL1[0e0]=13000000
DRAMC_DQSGCTL[124]=80000033
rank 0 coarse = 15
rank 0 fine = 72
B:|    0    0    0    0    0    0    0    0    0    0    1    1    1    0    0    0
opt_dle value:11
DRAMC_DDR2CTL[07c]=C287223D
DRAMC_PADCTL4[0e4]=000022B3
DRAMC_DQIDLY1[210]=0B080808
DRAMC_DQIDLY2[214]=06070807
DRAMC_DQIDLY3[218]=0A080607
DRAMC_DQIDLY4[21c]=09070A09
DRAMC_R0DELDLY[018]=00001D1E
==================================================================
		RX	DQS perbit delay software calibration 
==================================================================
1.0-15 bit dq delay value
==================================================================
bit|     0  1  2  3  4  5  6  7  8  9
--------------------------------------
0 |    7 7 7 11 6 8 7 5 6 6 
10 |    8 9 8 10 7 8 
--------------------------------------

==================================================================
2.dqs window
x=pass dqs delay value (min~max)center 
y=0-7bit DQ of every group
input delay:DQS0 =30 DQS1 = 29
==================================================================
bit	DQS0	 bit      DQS1
0  (1~58)29  8  (1~55)28
1  (1~57)29  9  (1~58)29
2  (1~58)29  10  (1~57)29
3  (1~60)30  11  (1~55)28
4  (1~57)29  12  (1~56)28
5  (1~60)30  13  (1~58)29
6  (1~59)30  14  (1~58)29
7  (1~58)29  15  (1~56)28
==================================================================
3.dq delay value last
==================================================================
bit|    0  1  2  3  4  5  6  7  8   9
--------------------------------------
0 |    8 8 8 11 7 8 7 6 7 6 
10 |    8 10 9 10 7 9 
==================================================================
==================================================================
     TX  perbyte calibration 
==================================================================
DQS loop = 15, cmp_err_1 = ffff2000 
dqs_perbyte_dly.last_dqsdly_pass[0]=15,  finish count=1 
DQS loop = 14, cmp_err_1 = ffff0000 
dqs_perbyte_dly.last_dqsdly_pass[1]=14,  finish count=2 
DQ loop=15, cmp_err_1 = ffff0080
dqs_perbyte_dly.last_dqdly_pass[1]=15,  finish count=1 
DQ loop=14, cmp_err_1 = ffff0000
dqs_perbyte_dly.last_dqdly_pass[0]=14,  finish count=2 
byte:0, (DQS,DQ)=(8,8)
byte:1, (DQS,DQ)=(8,8)
DRAMC_DQODLY1[200]=88888888
DRAMC_DQODLY2[204]=88888888
20,data:88
[EMI] DRAMC calibration passed

===================================================================
     		MT7621   stage1 code done 
     		CPU=500000000 HZ BUS=166666666 HZ
===================================================================


U-Boot 1.1.3 (Aug 18 2020 - 11:10:29)

Board: Ralink APSoC DRAM:  128 MB
Power on memory test. Memory size= 128 MB...OK!
relocate_code Pointer at: 87fb0000

Config XHCI 40M PLL 
RT2880_RSTSTAT_REG 0xc0030004
******************************
Software System Reset Occurred
******************************
flash manufacture id: c8, device id 40 18
find flash: GD25Q128C
============================================ 
Ralink UBoot Version: 5.0.0.0
-------------------------------------------- 
ASIC MT7621A DualCore (MAC to MT7530 Mode)
DRAM_CONF_FROM: Auto-Detection 
DRAM_TYPE: DDR3 
DRAM bus: 16 bit
Xtal Mode=3 OCP Ratio=1/3
Flash component: SPI Flash
Date:Aug 18 2020  Time:11:10:29
============================================ 
icache: sets:256, ways:4, linesz:32 ,total:32768
dcache: sets:256, ways:4, linesz:32 ,total:32768 

 ##### The CPU freq = 880 MHZ #### 
 estimate memory size =128 Mbytes
#Reset_MT7530
set LAN/WAN LLLLW

restore_defaults:0

Please choose the operation: 
   1: Load system code to SDRAM via TFTP. 
   2: Load system code then write to Flash via TFTP. 
   3: Boot system code via Flash (default).
   4: Entr boot command line interface.
   7: Load Boot Loader code then write to Flash via Serial. 
   9: Load Boot Loader code then write to Flash via TFTP. 

   n3: System Boot system code via Flash.
Booting System 1
Erasing SPI Flash...
raspi_erase: offs:30000 len:10000
.
Writing to SPI Flash...
.
done
## Booting image at bc180000 ...
   Image Name:   MIPS OpenWrt Linux-5.10.127
   Image Type:   MIPS Linux Kernel Image (uncompressed)
   Data Size:    2656448 Bytes =  2.5 MB
   Load Address: 80001000
   Entry Point:  80001000
   Verifying Checksum ... OK
OK
Erasing SPI Flash...
raspi_erase: offs:30000 len:10000
.
Writing to SPI Flash...
.
done
commandline uart_en=0 factory_mode=0 mem=128m root=/dev/mtdblock9
No initrd
## Transferring control to Linux (at address 80001000) ...
## Giving linux memsize in MB, 128

Starting kernel ...



OpenWrt kernel loader for MIPS based SoC
Copyright (C) 2011 Gabor Juhos <juhosg@openwrt.org>
Decompressing kernel... done!
Starting kernel at 80001000...

[    0.000000] Linux version 5.10.127 (gitlab-runner@jenkins) (mipsel-openwrt-linux-musl-gcc (OpenWrt GCC 11.2.0 r19525+6-f854de6ada) 11.2.0, GNU ld (GNU Binutils) 2.37) #0 SMP Tue Jul 5 21:49:31 2022
[    0.000000] SoC Type: MediaTek MT7621 ver:1 eco:3
[    0.000000] printk: bootconsole [early0] enabled
[    0.000000] CPU0 revision is: 0001992f (MIPS 1004Kc)
[    0.000000] MIPS: machine is Xiaomi Mi Router 4A Gigabit Edition
[    0.000000] Initrd not found or empty - disabling initrd
[    0.000000] VPE topology {2,2} total 4
[    0.000000] Primary instruction cache 32kB, VIPT, 4-way, linesize 32 bytes.
[    0.000000] Primary data cache 32kB, 4-way, PIPT, no aliases, linesize 32 bytes
[    0.000000] MIPS secondary cache 256kB, 8-way, linesize 32 bytes.
[    0.000000] Zone ranges:
[    0.000000]   Normal   [mem 0x0000000000000000-0x0000000007ffffff]
[    0.000000]   HighMem  empty
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x0000000000000000-0x0000000007ffffff]
[    0.000000] Initmem setup node 0 [mem 0x0000000000000000-0x0000000007ffffff]
[    0.000000] percpu: Embedded 15 pages/cpu s29936 r8192 d23312 u61440
[    0.000000] Built 1 zonelists, mobility grouping on.  Total pages: 32512
[    0.000000] Kernel command line: console=ttyS0,115200n8 rootfstype=squashfs,jffs2
[    0.000000] Dentry cache hash table entries: 16384 (order: 4, 65536 bytes, linear)
[    0.000000] Inode-cache hash table entries: 8192 (order: 3, 32768 bytes, linear)
[    0.000000] Writing ErrCtl register=00015290
[    0.000000] Readback ErrCtl register=00015290
[    0.000000] mem auto-init: stack:off, heap alloc:off, heap free:off
[    0.000000] Memory: 119736K/131072K available (6467K kernel code, 599K rwdata, 1344K rodata, 1240K init, 237K bss, 11336K reserved, 0K cma-reserved, 0K highmem)
[    0.000000] SLUB: HWalign=32, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] rcu: Hierarchical RCU implementation.
[    0.000000] 	Tracing variant of Tasks RCU enabled.
[    0.000000] rcu: RCU calculated value of scheduler-enlistment delay is 10 jiffies.
[    0.000000] NR_IRQS: 256
[    0.000000] CPU Clock: 880MHz
[    0.000000] clocksource: GIC: mask: 0xffffffffffffffff max_cycles: 0xcaf478abb4, max_idle_ns: 440795247997 ns
[    0.000013] sched_clock: 64 bits at 880MHz, resolution 1ns, wraps every 4398046511103ns
[    0.007941] clocksource: MIPS: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 4343773742 ns
[    0.016999] Calibrating delay loop... 586.13 BogoMIPS (lpj=2930688)
[    0.083160] pid_max: default: 32768 minimum: 301
[    0.087906] Mount-cache hash table entries: 1024 (order: 0, 4096 bytes, linear)
[    0.095109] Mountpoint-cache hash table entries: 1024 (order: 0, 4096 bytes, linear)
[    0.105179] rcu: Hierarchical SRCU implementation.
[    0.110187] dyndbg: Ignore empty _ddebug table in a CONFIG_DYNAMIC_DEBUG_CORE build
[    0.118183] smp: Bringing up secondary CPUs ...
[    0.123375] Primary instruction cache 32kB, VIPT, 4-way, linesize 32 bytes.
[    0.123385] Primary data cache 32kB, 4-way, PIPT, no aliases, linesize 32 bytes
[    0.123397] MIPS secondary cache 256kB, 8-way, linesize 32 bytes.
[    0.123471] CPU1 revision is: 0001992f (MIPS 1004Kc)
[    0.178075] Synchronize counters for CPU 1: done.
[    0.210397] Primary instruction cache 32kB, VIPT, 4-way, linesize 32 bytes.
[    0.210407] Primary data cache 32kB, 4-way, PIPT, no aliases, linesize 32 bytes
[    0.210414] MIPS secondary cache 256kB, 8-way, linesize 32 bytes.
[    0.210460] CPU2 revision is: 0001992f (MIPS 1004Kc)
[    0.269357] Synchronize counters for CPU 2: done.
[    0.299859] Primary instruction cache 32kB, VIPT, 4-way, linesize 32 bytes.
[    0.299867] Primary data cache 32kB, 4-way, PIPT, no aliases, linesize 32 bytes
[    0.299875] MIPS secondary cache 256kB, 8-way, linesize 32 bytes.
[    0.299922] CPU3 revision is: 0001992f (MIPS 1004Kc)
[    0.354539] Synchronize counters for CPU 3: done.
[    0.384402] smp: Brought up 1 node, 4 CPUs
[    0.392303] clocksource: jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 19112604462750000 ns
[    0.402120] futex hash table entries: 1024 (order: 3, 32768 bytes, linear)
[    0.409070] pinctrl core: initialized pinctrl subsystem
[    0.416575] NET: Registered protocol family 16
[    0.422279] thermal_sys: Registered thermal governor 'step_wise'
[    0.423420] cpuidle: using governor teo
[    0.475076] clocksource: Switched to clocksource GIC
[    0.481712] NET: Registered protocol family 2
[    0.486381] IP idents hash table entries: 2048 (order: 2, 16384 bytes, linear)
[    0.494564] tcp_listen_portaddr_hash hash table entries: 512 (order: 0, 6144 bytes, linear)
[    0.502923] TCP established hash table entries: 1024 (order: 0, 4096 bytes, linear)
[    0.510568] TCP bind hash table entries: 1024 (order: 1, 8192 bytes, linear)
[    0.517545] TCP: Hash tables configured (established 1024 bind 1024)
[    0.523991] UDP hash table entries: 256 (order: 1, 8192 bytes, linear)
[    0.530468] UDP-Lite hash table entries: 256 (order: 1, 8192 bytes, linear)
[    0.537595] NET: Registered protocol family 1
[    0.541897] PCI: CLS 0 bytes, default 32
[    0.548072] workingset: timestamp_bits=30 max_order=15 bucket_order=0
[    0.558079] squashfs: version 4.0 (2009/01/31) Phillip Lougher
[    0.563826] jffs2: version 2.2 (NAND) (SUMMARY) (LZMA) (RTIME) (CMODE_PRIORITY) (c) 2001-2006 Red Hat, Inc.
[    0.574481] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 251)
[    0.583334] mt7621_gpio 1e000600.gpio: registering 32 gpios
[    0.589259] mt7621_gpio 1e000600.gpio: registering 32 gpios
[    0.595198] mt7621_gpio 1e000600.gpio: registering 32 gpios
[    0.601626] Serial: 8250/16550 driver, 16 ports, IRQ sharing enabled
[    0.611934] printk: console [ttyS0] disabled
[    0.616274] 1e000c00.uartlite: ttyS0 at MMIO 0x1e000c00 (irq = 19, base_baud = 3125000) is a 16550A
[    0.625277] printk: console [ttyS0] enabled
[    0.625277] printk: console [ttyS0] enabled
[    0.633515] printk: bootconsole [early0] disabled
[    0.633515] printk: bootconsole [early0] disabled
[    0.645972] spi-mt7621 1e000b00.spi: sys_freq: 220000000
[    0.652692] spi-nor spi0.0: gd25q128 (16384 Kbytes)
[    0.657696] 8 fixed-partitions partitions found on MTD device spi0.0
[    0.664021] Creating 8 MTD partitions on "spi0.0":
[    0.668859] 0x000000000000-0x000000030000 : "u-boot"
[    0.674734] 0x000000030000-0x000000040000 : "u-boot-env"
[    0.680967] 0x000000040000-0x000000050000 : "Bdata"
[    0.686730] 0x000000050000-0x000000060000 : "factory"
[    0.692780] 0x000000060000-0x000000070000 : "crash"
[    0.698566] 0x000000070000-0x000000080000 : "cfg_bak"
[    0.704413] 0x000000080000-0x000000180000 : "overlay"
[    0.710373] 0x000000180000-0x000001000000 : "firmware"
[    0.716544] 2 uimage-fw partitions found on MTD device firmware
[    0.722457] Creating 2 MTD partitions on "firmware":
[    0.727429] 0x000000000000-0x000000288900 : "kernel"
[    0.732370] mtd: partition "kernel" doesn't end on an erase/write block -- force read-only
[    0.741290] 0x000000288900-0x000000e80000 : "rootfs"
[    0.746307] mtd: partition "rootfs" doesn't start on an erase/write block boundary -- force read-only
[    0.756224] mtd: device 9 (rootfs) set to be root filesystem
[    0.762011] 1 squashfs-split partitions found on MTD device rootfs
[    0.768196] 0x000000550000-0x000000e80000 : "rootfs_data"
[    0.826742] mt7530 mdio-bus:1f: MT7530 adapts as multi-chip module
[    0.836386] mtk_soc_eth 1e100000.ethernet eth0: mediatek frame engine at 0xbe100000, irq 21
[    0.845751] i2c /dev entries driver
[    0.851399] mt7621-pci 1e140000.pcie: host bridge /pcie@1e140000 ranges:
[    0.858134] mt7621-pci 1e140000.pcie:   No bus range found for /pcie@1e140000, using [bus 00-ff]
[    0.866928] mt7621-pci 1e140000.pcie:      MEM 0x0060000000..0x006fffffff -> 0x0000000000
[    0.875103] mt7621-pci 1e140000.pcie:       IO 0x001e160000..0x001e16ffff -> 0x0000000000
[    0.883347] mt7621-pci 1e140000.pcie: Parsing DT failed
[    0.890927] NET: Registered protocol family 10
[    0.896960] Segment Routing with IPv6
[    0.900706] NET: Registered protocol family 17
[    0.905300] bridge: filtering via arp/ip/ip6tables is no longer available by default. Update your scripts to load br_netfilter if you need this.
[    0.918623] 8021q: 802.1Q VLAN Support v1.8
[    0.926296] mt7530 mdio-bus:1f: MT7530 adapts as multi-chip module
[    0.947180] mt7530 mdio-bus:1f lan2 (uninitialized): PHY [mt7530-0:02] driver [MediaTek MT7530 PHY] (irq=26)
[    0.959371] mt7530 mdio-bus:1f lan1 (uninitialized): PHY [mt7530-0:03] driver [MediaTek MT7530 PHY] (irq=27)
[    0.971721] mt7530 mdio-bus:1f wan (uninitialized): PHY [mt7530-0:04] driver [MediaTek MT7530 PHY] (irq=28)
[    0.984165] mt7530 mdio-bus:1f: configuring for fixed/rgmii link mode
[    0.994566] DSA: tree 0 setup
[    0.997858] rt2880-pinmux pinctrl: pcie is already enabled
[    1.003400] mt7621-pci 1e140000.pcie: host bridge /pcie@1e140000 ranges:
[    1.010109] mt7621-pci 1e140000.pcie:   No bus range found for /pcie@1e140000, using [bus 00-ff]
[    1.018901] mt7621-pci 1e140000.pcie:      MEM 0x0060000000..0x006fffffff -> 0x0000000000
[    1.027078] mt7621-pci 1e140000.pcie:       IO 0x001e160000..0x001e16ffff -> 0x0000000000
[    1.035339] mt7621-pci-phy 1e149000.pcie-phy: PHY for 0xbe149000 (dual port = 1)
[    1.043049] mt7621-pci-phy 1e14a000.pcie-phy: PHY for 0xbe14a000 (dual port = 0)
[    1.050666] mt7621-pci 1e140000.pcie: failed to parse bus ranges property: -22
[    1.158047] mt7621-pci-phy 1e149000.pcie-phy: Xtal is 40MHz
[    1.163612] mt7621-pci-phy 1e14a000.pcie-phy: Xtal is 40MHz
[    1.269331] mt7621-pci 1e140000.pcie: pcie2 no card, disable it (RST & CLK)
[    1.276284] mt7621-pci 1e140000.pcie: PCIE0 enabled
[    1.281139] mt7621-pci 1e140000.pcie: PCIE1 enabled
[    1.286013] mt7621-pci 1e140000.pcie: PCI coherence region base: 0x60000000, mask/settings: 0xf0000002
[    1.295465] mt7621-pci 1e140000.pcie: PCI host bridge to bus 0000:00
[    1.301809] pci_bus 0000:00: root bus resource [io  0x1e160000-0x1e16ffff]
[    1.308678] pci_bus 0000:00: root bus resource [mem 0x60000000-0x6fffffff]
[    1.315545] pci_bus 0000:00: root bus resource [bus 00-ff]
[    1.321010] pci_bus 0000:00: root bus resource [mem 0x60000000-0x6fffffff] (bus address [0x00000000-0x0fffffff])
[    1.331213] pci 0000:00:00.0: [0e8d:0801] type 01 class 0x060400
[    1.337230] pci 0000:00:00.0: reg 0x10: [mem 0x00000000-0x7fffffff]
[    1.343473] pci 0000:00:00.0: reg 0x14: [mem 0x60300000-0x6030ffff]
[    1.349790] pci 0000:00:00.0: supports D1
[    1.353783] pci 0000:00:00.0: PME# supported from D0 D1 D3hot
[    1.360063] pci 0000:00:01.0: [0e8d:0801] type 01 class 0x060400
[    1.366107] pci 0000:00:01.0: reg 0x10: [mem 0x00000000-0x7fffffff]
[    1.372349] pci 0000:00:01.0: reg 0x14: [mem 0x60310000-0x6031ffff]
[    1.378663] pci 0000:00:01.0: supports D1
[    1.382656] pci 0000:00:01.0: PME# supported from D0 D1 D3hot
[    1.390041] pci 0000:01:00.0: [14c3:7662] type 00 class 0x028000
[    1.396098] pci 0000:01:00.0: reg 0x10: initial BAR value 0x00000000 invalid
[    1.403122] pci 0000:01:00.0: reg 0x10: [mem size 0x00100000 64bit]
[    1.409411] pci 0000:01:00.0: reg 0x30: initial BAR value 0x00000000 invalid
[    1.416446] pci 0000:01:00.0: reg 0x30: [mem size 0x00010000 pref]
[    1.422700] pci 0000:01:00.0: PME# supported from D0 D3hot D3cold
[    1.430207] pci 0000:00:00.0: PCI bridge to [bus 01-ff]
[    1.435454] pci 0000:00:00.0:   bridge window [io  0x0000-0x0fff]
[    1.441522] pci 0000:00:00.0:   bridge window [mem 0x60000000-0x600fffff]
[    1.448305] pci 0000:00:00.0:   bridge window [mem 0x60100000-0x601fffff pref]
[    1.455518] pci_bus 0000:01: busn_res: [bus 01-ff] end is updated to 01
[    1.462341] pci 0000:02:00.0: [14c3:7603] type 00 class 0x028000
[    1.468375] pci 0000:02:00.0: reg 0x10: initial BAR value 0x00000000 invalid
[    1.475414] pci 0000:02:00.0: reg 0x10: [mem size 0x00100000]
[    1.481271] pci 0000:02:00.0: PME# supported from D0 D3hot D3cold
[    1.488793] pci 0000:00:01.0: PCI bridge to [bus 02-ff]
[    1.494015] pci 0000:00:01.0:   bridge window [io  0x0000-0x0fff]
[    1.500104] pci 0000:00:01.0:   bridge window [mem 0x60200000-0x602fffff]
[    1.506894] pci_bus 0000:02: busn_res: [bus 02-ff] end is updated to 02
[    1.513537] pci 0000:00:00.0: BAR 0: no space for [mem size 0x80000000]
[    1.520137] pci 0000:00:00.0: BAR 0: failed to assign [mem size 0x80000000]
[    1.527089] pci 0000:00:01.0: BAR 0: no space for [mem size 0x80000000]
[    1.533673] pci 0000:00:01.0: BAR 0: failed to assign [mem size 0x80000000]
[    1.540623] pci 0000:00:00.0: BAR 8: assigned [mem 0x60000000-0x600fffff]
[    1.547404] pci 0000:00:00.0: BAR 9: assigned [mem 0x60100000-0x601fffff pref]
[    1.554594] pci 0000:00:01.0: BAR 8: assigned [mem 0x60200000-0x602fffff]
[    1.561371] pci 0000:00:00.0: BAR 1: assigned [mem 0x60300000-0x6030ffff]
[    1.568160] pci 0000:00:01.0: BAR 1: assigned [mem 0x60310000-0x6031ffff]
[    1.574922] pci 0000:00:00.0: BAR 7: assigned [io  0x1e160000-0x1e160fff]
[    1.581697] pci 0000:00:01.0: BAR 7: assigned [io  0x1e161000-0x1e161fff]
[    1.588486] pci 0000:01:00.0: BAR 0: assigned [mem 0x60000000-0x600fffff 64bit]
[    1.595793] pci 0000:01:00.0: BAR 6: assigned [mem 0x60100000-0x6010ffff pref]
[    1.602984] pci 0000:00:00.0: PCI bridge to [bus 01]
[    1.607942] pci 0000:00:00.0:   bridge window [io  0x1e160000-0x1e160fff]
[    1.614701] pci 0000:00:00.0:   bridge window [mem 0x60000000-0x600fffff]
[    1.621475] pci 0000:00:00.0:   bridge window [mem 0x60100000-0x601fffff pref]
[    1.628696] pci 0000:02:00.0: BAR 0: assigned [mem 0x60200000-0x602fffff]
[    1.635474] pci 0000:00:01.0: PCI bridge to [bus 02]
[    1.640417] pci 0000:00:01.0:   bridge window [io  0x1e161000-0x1e161fff]
[    1.647191] pci 0000:00:01.0:   bridge window [mem 0x60200000-0x602fffff]
[    1.660336] mt7530 mdio-bus:1f: Link is Up - 1Gbps/Full - flow control rx/tx
[    1.668478] VFS: Mounted root (squashfs filesystem) readonly on device 31:9.
[    1.679457] Freeing unused kernel memory: 1240K
[    1.683986] This architecture does not have kernel memory protection.
[    1.690563] Run /sbin/init as init process
[    2.263679] init: Console is alive
[    2.267510] init: - watchdog -
[    3.026907] kmodloader: loading kernel modules from /etc/modules-boot.d/*
[    3.111070] kmodloader: done loading kernel modules from /etc/modules-boot.d/*
[    3.125485] init: - preinit -
[    3.940046] random: jshn: uninitialized urandom read (4 bytes read)
[    4.014758] random: jshn: uninitialized urandom read (4 bytes read)
[    4.051114] random: jshn: uninitialized urandom read (4 bytes read)
[    4.291636] mtk_soc_eth 1e100000.ethernet eth0: configuring for fixed/rgmii link mode
[    4.300456] mtk_soc_eth 1e100000.ethernet eth0: Link is Up - 1Gbps/Full - flow control rx/tx
[    4.305295] mt7530 mdio-bus:1f lan1: configuring for phy/gmii link mode
[    4.315894] 8021q: adding VLAN 0 to HW filter on device lan1
[    4.324147] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Press the [f] key and hit [enter] to enter failsafe mode
Press the [1], [2], [3] or [4] key and hit [enter] to select the debug level
[    8.636652] jffs2: notice: (553) jffs2_build_xattr_subsystem: complete building xattr subsystem, 17 of xdatum (13 unchecked, 4 orphan) and 23 of xref (4 dead, 0 orphan) found.
[    8.654772] mount_root: switching to jffs2 overlay
[    8.665871] overlayfs: upper fs does not support tmpfile.
[    8.683849] urandom-seed: Seeding with /etc/urandom.seed
[    8.867140] procd: - early -
[    8.870237] procd: - watchdog -
[    9.525246] procd: - watchdog -
[    9.529446] procd: - ubus -
[    9.569768] random: ubusd: uninitialized urandom read (4 bytes read)
[    9.586016] random: ubusd: uninitialized urandom read (4 bytes read)
[    9.592800] random: ubusd: uninitialized urandom read (4 bytes read)
[    9.602612] procd: - init -
Please press Enter to activate this console.
[   10.213300] random: crng init done
[   10.216884] random: 28 urandom warning(s) missed due to ratelimiting
[   10.268461] kmodloader: loading kernel modules from /etc/modules.d/*
[   10.613399] urngd: v1.0.2 started.
[   10.616040] tun: Universal TUN/TAP device driver, 1.6
[   10.645859] GACT probability on
[   10.651201] Mirror/redirect action on
[   10.669149] u32 classifier
[   10.671878]     input device check on
[   10.675544]     Actions configured
[   10.693467] Simple TC action Loaded
[   10.728609] Loading modules backported from Linux version v5.15.33-0-g06f50ca83ace
[   10.736377] Backport generated by backports.git v5.15.33-1-0-g183c4ab2
[   10.815116] xt_time: kernel timezone is -0000
[   11.087530] mt7621-pci 1e140000.pcie: bus=2 slot=1 irq=23
[   11.093021] pci 0000:00:01.0: enabling device (0006 -> 0007)
[   11.098746] mt7603e 0000:02:00.0: enabling device (0000 -> 0002)
[   11.104922] mt7603e 0000:02:00.0: ASIC revision: 76030010
[   12.140059] mt7603e 0000:02:00.0: Firmware Version: ap_pcie
[   12.145670] mt7603e 0000:02:00.0: Build Time: 20160107100755
[   12.185064] mt7603e 0000:02:00.0: firmware init done
[   12.369899] mt7621-pci 1e140000.pcie: bus=1 slot=0 irq=22
[   12.375384] pci 0000:00:00.0: enabling device (0006 -> 0007)
[   12.381057] mt76x2e 0000:01:00.0: enabling device (0000 -> 0002)
[   12.387301] mt76x2e 0000:01:00.0: ASIC revision: 76120044
[   13.130023] mt76x2e 0000:01:00.0: ROM patch build: 20141115060606a
[   13.140085] mt76x2e 0000:01:00.0: Firmware Version: 0.0.00
[   13.145602] mt76x2e 0000:01:00.0: Build: 1
[   13.149679] mt76x2e 0000:01:00.0: Build Time: 201607111443____
[   13.175136] mt76x2e 0000:01:00.0: Firmware running!
[   13.215441] batman_adv: B.A.T.M.A.N. advanced 2022.0-openwrt-5 (compatibility version 15) loaded
[   13.226505] kmodloader: done loading kernel modules from /etc/modules.d/*
[   22.222409] mtk_soc_eth 1e100000.ethernet eth0: Link is Down
[   22.237506] mtk_soc_eth 1e100000.ethernet eth0: configuring for fixed/rgmii link mode
[   22.245719] mtk_soc_eth 1e100000.ethernet eth0: Link is Up - 1Gbps/Full - flow control rx/tx
[   22.254178] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   22.262281] mt7530 mdio-bus:1f lan1: configuring for phy/gmii link mode
[   22.270130] 8021q: adding VLAN 0 to HW filter on device lan1
[   22.279531] br-client: port 1(lan1) entered blocking state
[   22.285133] br-client: port 1(lan1) entered disabled state
[   22.291576] device lan1 entered promiscuous mode
[   22.296345] device eth0 entered promiscuous mode
[   22.320943] mt7530 mdio-bus:1f lan2: configuring for phy/gmii link mode
[   22.328188] 8021q: adding VLAN 0 to HW filter on device lan2
[   22.338415] br-client: port 2(lan2) entered blocking state
[   22.343946] br-client: port 2(lan2) entered disabled state
[   22.351497] device lan2 entered promiscuous mode
[   22.436705] mt7530 mdio-bus:1f wan: configuring for phy/gmii link mode
[   22.443740] 8021q: adding VLAN 0 to HW filter on device wan
[   22.453253] br-wan: port 1(wan) entered blocking state
[   22.458670] br-wan: port 1(wan) entered disabled state
[   22.464647] device wan entered promiscuous mode
[   22.538814] IPv6: ADDRCONF(NETDEV_CHANGE): local-node: link becomes ready
[   22.563169] br-client: port 3(local-port) entered blocking state
[   22.569369] br-client: port 3(local-port) entered disabled state
[   22.597727] device local-port entered promiscuous mode
[   22.603664] br-client: port 3(local-port) entered blocking state
[   22.609824] br-client: port 3(local-port) entered forwarding state
[   22.617165] IPv6: ADDRCONF(NETDEV_CHANGE): br-client: link becomes ready
[   22.973599] 8021q: adding VLAN 0 to HW filter on device bat0
[   22.982433] br-client: port 4(bat0) entered blocking state
[   22.988284] br-client: port 4(bat0) entered disabled state
[   22.994518] device bat0 entered promiscuous mode
[   22.999818] br-client: port 4(bat0) entered blocking state
[   23.005583] br-client: port 4(bat0) entered forwarding state
[   23.475210] batman_adv: bat0: No IGMP Querier present - multicast optimizations disabled
[   23.483322] batman_adv: bat0: No MLD Querier present - multicast optimizations disabled
[   24.001516] batman_adv: bat0: Adding interface: primary0
[   24.006920] batman_adv: bat0: Interface activated: primary0
[   24.151824] batman_adv: bat0: Interface deactivated: primary0
[   24.176891] batman_adv: bat0: Interface activated: primary0
[   25.842366] br-client: port 5(client1) entered blocking state
[   25.848174] br-client: port 5(client1) entered disabled state
[   25.854505] device client1 entered promiscuous mode
[   26.241436] IPv6: ADDRCONF(NETDEV_CHANGE): client1: link becomes ready
[   26.248481] br-client: port 5(client1) entered blocking state
[   26.254277] br-client: port 5(client1) entered forwarding state
[   26.401279] br-client: port 6(client0) entered blocking state
[   26.407164] br-client: port 6(client0) entered disabled state
[   26.413757] device client0 entered promiscuous mode
[   26.419456] br-client: port 6(client0) entered blocking state
[   26.425307] br-client: port 6(client0) entered forwarding state
[   26.444873] IPv6: ADDRCONF(NETDEV_CHANGE): client0: link becomes ready
[   27.671016] IPv6: ADDRCONF(NETDEV_CHANGE): mesh1: link becomes ready
[   27.735427] batman_adv: bat0: Adding interface: mesh-vpn
[   27.740802] batman_adv: bat0: The MTU of interface mesh-vpn is too small (1280) to handle the transport of batman-adv packets. Packets going over this interface will be fragmented on layer2 which could impact the performance. Setting the MTU to 1532 would solve the problem.
[   27.765112] batman_adv: bat0: Interface activated: mesh-vpn
[   27.870870] IPv6: ADDRCONF(NETDEV_CHANGE): mesh0: link becomes ready
[   28.279095] batman_adv: bat0: Adding interface: mesh1
[   28.284200] batman_adv: bat0: Interface activated: mesh1
[   28.512628] batman_adv: bat0: Adding interface: mesh0
[   28.517870] batman_adv: bat0: Interface activated: mesh0
[   32.675290] batman_adv: bat0: IGMP Querier appeared
[   32.680220] batman_adv: bat0: MLD Querier appeared



BusyBox v1.35.0 (2022-07-05 21:49:31 UTC) built-in shell (ash)

  _______                     ________        __
 |       |.-----.-----.-----.|  |  |  |.----.|  |_
 |   -   ||  _  |  -__|     ||  |  |  ||   _||   _|
 |_______||   __|_____|__|__||________||__|  |____|
          |__| W I R E L E S S   F R E E D O M
 -----------------------------------------------------
 OpenWrt 22.03-SNAPSHOT, r19525+6-f854de6ada
 -----------------------------------------------------
root@ffhb-64644adb97c2-XIAOMI-Mi-Router-4A-Gigabit-Edition:/# 
root@ffhb-64644adb97c2-XIAOMI-Mi-Router-4A-Gigabit-Edition:/# 
</pre>
~~~


Der Start mit gedrücktem Reset Knopf soll den TFTP Ladevorgang anstossen, ist nicht genau verifiziert.
Auch mit installierter FF - SW wurde noch kein Test mit TFTP durchgeführt.



**[------------------------------------------------------------------------------------------------------------------------- Zurück zum Inhalt:](#inhalt)**

### 5. Grundkonfiguration & Downgrade auf Version 3.0.24 der Xiaomi Firmware
Bereits die normale Inbetriebnahme kann nur erfolgreich durchgeführt wenn der Router
an einen Internetanschluss mit DHCP verkabelt ist. Es wird ein zweites LAN Kabel benötigt.
An den beiden LAN Schnittstellen hört dieser nach dem Booten auf die IP 192.168.31.1. 

Hier bitte eine Basiskonfiguration durchführen - auch um die Firmware Version zu checken. 
Sollte diese nicht 3.0.24 sein, kann nach der initialen Konfiguration über das Admin 
Interface ein Downgrade vorgenommen werden. Eine passende Firmware findet ihr hier:
https://github.com/ffrgb/stockimages/blob/master/xiaomi-4a-gige/miwifi_r4a_all_03233_3.0.24_INT.bin

Sollte sich die SW Version nicht aktivieren lassen, bitte im OpenWRT Forum nach der Geräte-SW suchen und Prüfen ob es eine Möglichkeit zum flashen für diese Version gibt. Es ist dem Hersteller überlassen, die Gerätefirmware abzusichern, das diese nicht durch freie Software ersetzt werden kann.


**[------------------------------------------------------------------------------------------------------------------------- Zurück zum Inhalt:](#inhalt)**

### 6. Exploit für den Hack unter Linux vorbereiten
Als Windwos Bemutzer habe ich eine Ubuntu VM, ein USB Netzwerkadapter an den Router angeschlossen.
Das Linuxsystem aktualisieren und ein paar Pakete nachinstallieren.
Pakete (gegebenfalls mit sudo apt install nachinstallieren):
~~~
    python3 pip3
    git
    telnet
~~~

Die Aktualisierung könnte so aussehen.
~~~

ffhb@ffhb:~$ sudo apt update && sudo apt upgrade
...
Paketlisten werden gelesen... Fertig
...
Alle Pakete sind aktuell.

ffhb@ffhb:~$ sudo apt install python3-pip git telnet 
...
Paketlisten werden gelesen... Fertig
...
python3-pip ist schon die neueste Version (20.0.2-5ubuntu1.6).
0 aktualisiert, 0 neu installiert, 0 zu entfernen und 0 nicht aktualisiert.
~~~
Noch mal gucken, ob der Router noch da ist:
~~~
ffhb@ffhb:~$ ping 192.168.31.1
PING 192.168.31.1 (192.168.31.1) 56(84) Bytes Daten.
64 Bytes von 192.168.31.1: icmp_seq=1 ttl=64 Zeit=1.38 ms
~~~

Invasion durchführen (hier die Verlinkung auf FF-Dresden)

Auf Linux-PC Console öffnen und folgende Befehle ausführen:
Tools zum 'Öffnen' des Routers für Freifunk-Firmware installieren

~~~
git clone https://github.com/Freifunk-Dresden/OpenWRTInvasion
cd OpenWRTInvasion
pip3 install -r requirements.txt 
~~~

Gerät per Tool öffnen

~~~
python3 remote_command_execution_vulnerability.py
~~~

Router IP eintippen, zuvor gewähltes Passwort Eingeben, default Option 1 wählen und warten bis das Script durchgelaufen ist.

Beispiel:

Router IP address [press enter for using the default 'miwifi.com']: 192.168.31.1
Enter router admin password: test1234
There two options to provide the files needed for invasion:
  1. Use a local TCP file server runing on random port to provide files in local directory `script_tools`.
  2. Download needed files from remote github repository. (choose this option only if github is accessable inside router device.)
Which option do you prefer? (default: 1)

****************
router_ip_address: 192.168.31.1
stok: 7508040b98e1b16255c465cf2f5a947c
file provider: local file server
****************
start uploading config file...
start exec command...
local file server is runing on 0.0.0.0:57765. root='script_tools'

Hinweis: Es müssen folgende beide Zeilen zu sehen sein.

local file server is getting 'busybox-mipsel' for 192.168.31.1.
local file server is getting 'dropbearStaticMipsel.tar.bz2' for 192.168.31.1.

Wenn nicht, ist wahrscheinlich eine lokale Firewall (Ubuntu -> ufw / Fedora -> firewalld etc.) aktiv, die Verbindungen blockiert. Diese muss dann temporär deaktiviert werden (sudo ufw disable / sudo systemctl stop firewalld). 

done! Now you can connect to the router using several options: (user: root, password: root)
* telnet 192.168.31.1
* ssh -oKexAlgorithms=+diffie-hellman-group1-sha1 -c 3des-cbc -o UserKnownHostsFile=/dev/null root@192.168.31.1
* ftp: using a program like cyberduck
* 

~~~

ffhb@ffhb:~/OpenWRTInvasion$ 



ffhb@ffhb:~/OpenWRTInvasion$ telnet 192.168.31.1
Trying 192.168.31.1...
Connected to 192.168.31.1.
Escape character is '^]'.

XiaoQiang login: root
Password: 


BusyBox v1.19.4 (2020-08-18 11:07:27 UTC) built-in shell (ash)
Enter 'help' for a list of built-in commands.

 -----------------------------------------------------
       Welcome to XiaoQiang!
 -----------------------------------------------------
  $$$$$$\  $$$$$$$\  $$$$$$$$\      $$\      $$\        $$$$$$\  $$\   $$\
 $$  __$$\ $$  __$$\ $$  _____|     $$ |     $$ |      $$  __$$\ $$ | $$  |
 $$ /  $$ |$$ |  $$ |$$ |           $$ |     $$ |      $$ /  $$ |$$ |$$  /
 $$$$$$$$ |$$$$$$$  |$$$$$\         $$ |     $$ |      $$ |  $$ |$$$$$  /
 $$  __$$ |$$  __$$< $$  __|        $$ |     $$ |      $$ |  $$ |$$  $$<
 $$ |  $$ |$$ |  $$ |$$ |           $$ |     $$ |      $$ |  $$ |$$ |\$$\
 $$ |  $$ |$$ |  $$ |$$$$$$$$\       $$$$$$$$$  |       $$$$$$  |$$ | \$$\
 \__|  \__|\__|  \__|\________|      \_________/        \______/ \__|  \__|


root@XiaoQiang:~# 


curl -4 -k http-link auf mein communityfile

curl -4 -k https://download.freifunk-dresden.de/firmware/.nightly/firmware/ramips.mt7621.generic/openwrt-ramips-mt7621-xiaomi_mi-router-4a-gigabit-initramfs-kernel.bin --output firmware.bin 

mtd -e OS1 -r write firmware.bin OS1

~~~

Wenn das funktioniert, ist der Router nach dem Neustart auf dem OpwnWRT Image.
Ich habe mir vorher die Images per FTP ins /tmp Verzeichnis gelegt.




**[------------------------------------------------------------------------------------------------------------------------- Zurück zum Inhalt:](#inhalt)**

### 7. Systemupgrade

Nun gibt es zwei Optionen das Sysupgrade auszuführen.
1. via Webinterface

Die Website auf http://192.168.1.1 aufrufen und in die Firmware Verwaltung wechseln.

Menü: Verwalten > Wartung > Firmware

Nun das Sysupgrade-Image auswählen und "Firmware laden".

2. via SSH

Mit SSH (ssh root@192.168.1.1) anmelden und Systemupgrade durchführen: Vorher auf OpenWRT einloggen, für den User root ein PW festlegen. Also root/root ist ok.

cd /tmp
wget -4 https://download.freifunk-dresden.de/firmware/.nightly/firmware/ramips.mt7621.generic/openwrt-ramips-mt7621-xiaomi_mi-router-4a-gigabit-squashfs-sysupgrade.bin -O sysupgrade.bin
sysupgrade -n sysupgrade.bin

oder per SCP in das /tmp Verzeichnis kopieren.

Dieser Vorgang dauert ca. 10 Minuten, es werden Neustarts durchgeführt.
Danach ist der Router fertig installiert und über die IP 192.168.1.1 erreichbar. (benötigt statische IP Konfiguration, also mein Rechner bekommt 192.168.1.2) 

Hier Links zu weitern Anleitungen: 

[https://wiki.bremen.freifunk.net/Anleitungen/Firmware/Flashen_Xiaomi-mi_router_4a.md ](https://wiki.bremen.freifunk.net/Anleitungen/Firmware/Flashen_Xiaomi-mi_router_4a.md ) 
[https://regensburg.freifunk.net/news/article/xiaomi-4a-gigabit-edition-support/](https://regensburg.freifunk.net/news/article/xiaomi-4a-gigabit-edition-support/) 

[https://wiki.freifunk-dresden.de/index.php/Router_einrichten_Xiaomi#Xiaomi_MI_Router_4A_Gigabit ](https://wiki.freifunk-dresden.de/index.php/Router_einrichten_Xiaomi#Xiaomi_MI_Router_4A_Gigabit ) 

[https://openwrt.org/toh/xiaomi/mi_router_4](https://openwrt.org/toh/xiaomi/mi_router_4) 




**[------------------------------------------------------------------------------------------------------------------------- Zurück zum Inhalt:](#inhalt)**


**Diese Anleitung ist wie immer ohne Gewähr. Für Anregungen und Tipps immer offen.**

