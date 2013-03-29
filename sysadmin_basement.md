# 基本部分
## 一、 系统硬件
### 1. 主板
a. 序列号

➜  ~  sudo dmidecode -t system |grep -i Serial

	Serial Number: CNU9032T3N

b. 厂商和型号

➜  ~  sudo dmidecode -t system                
	
	# dmidecode 2.11	
	SMBIOS 2.4 present.

	Handle 0x0001, DMI type 1, 27 bytes
	System Information
	        Manufacturer: Hewlett-Packard
	        Product Name: HP 540
        Version: F.02
        Serial Number: CNU9032T3N
        UUID: 7E2B6111-7C15-E011-5A8C-6D991201D929
        Wake-up Type: Power Switch
        SKU Number: NL385PA#AB2
        Family: 103C_5336AN

	Handle 0x0012, DMI type 32, 11 bytes
	System Boot Information
        Status: No errors detected

c. 出厂日期

➜  ~  sudo dmidecode -t bios|grep -i date

        Release Date: 08/20/2008

### 2. CPU
a. /proc/cpuinfo

➜  ~ cat /proc/cpuinfo

	processor       : 0
	vendor_id       : GenuineIntel
	cpu family      : 6
	model           : 15
	model name      : Genuine Intel(R) CPU           T1400  @ 1.73GHz
	stepping        : 13
	microcode       : 0xa3
	cpu MHz         : 1729.060
	cache size      : 512 KB
	physical id     : 0
	siblings        : 2
	core id         : 0
	cpu cores       : 2
	apicid          : 0
	initial apicid  : 0
	fdiv_bug        : no
	hlt_bug         : no
	f00f_bug        : no
	coma_bug        : no
	fpu             : yes
	fpu_exception   : yes
	cpuid level     : 10
	wp              : yes
	flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm
	bogomips        : 3458.12
	clflush size    : 64
	cache_alignment : 64
	address sizes   : 36 bits physical, 48 bits virtual
	power management:
b. lscpu

➜  ~ lscpu

	Architecture:          x86_64
	CPU op-mode(s):        32-bit, 64-bit
	CPU(s):                24
	Thread(s) per core:    2
	Core(s) per socket:    6
	CPU socket(s):         2
	NUMA node(s):          2
	Vendor ID:             GenuineIntel
	CPU family:            6
	Model:                 44
	Stepping:              2
	CPU MHz:               2526.869
	Virtualization:        VT-x
	L1d cache:             32K
	L1i cache:             32K
	L2 cache:              256K
	L3 cache:              12288K
b. dmidecode -t processor

➜  ~  sudo dmidecode -t processor

	# dmidecode 2.11
	SMBIOS 2.4 present.

	Handle 0x0004, DMI type 4, 35 bytes
	Processor Information
        Socket Designation: U10
        Type: Central Processor
        Family: Pentium M
        Manufacturer: Intel(R)
        ID: FD 06 00 00 FF FB EB BF
        Signature: Type 0, Family 6, Model 15, Stepping 13
        Flags:
                FPU (Floating-point unit on-chip)
                VME (Virtual mode extension)
                DE (Debugging extension)
                PSE (Page size extension)
                TSC (Time stamp counter)
                MSR (Model specific registers)
                PAE (Physical address extension)
                MCE (Machine check exception)
                CX8 (CMPXCHG8 instruction supported)
                APIC (On-chip APIC hardware supported)
                SEP (Fast system call)
                MTRR (Memory type range registers)
                PGE (Page global enable)
                MCA (Machine check architecture)
                CMOV (Conditional move instruction supported)
                PAT (Page attribute table)
                PSE-36 (36-bit page size extension)
                CLFSH (CLFLUSH instruction supported)
                DS (Debug store)
                ACPI (ACPI supported)
                MMX (MMX technology supported)
                FXSR (FXSAVE and FXSTOR instructions supported)
                SSE (Streaming SIMD extensions)
                SSE2 (Streaming SIMD extensions 2)
                SS (Self-snoop)
                HTT (Multi-threading)
                TM (Thermal monitor supported)
                PBE (Pending break enabled)
        Version: Genuine Intel(R) CPU           T1400  @ 1.73GHz
        Voltage: 1.1 V
        External Clock: 133 MHz
        Max Speed: 1733 MHz
        Current Speed: 1733 MHz
        Status: Populated, Enabled
        Upgrade: None
        L1 Cache Handle: 0x0005
        L2 Cache Handle: 0x0006
        L3 Cache Handle: Not Provided
        Serial Number: Not Specified
        Asset Tag: Not Specified
        Part Number: Not Specified
	
	
### 3. 内存
a. /proc/meminfo

➜  ~  cat /proc/meminfo 

	MemTotal:        1016844 kB
	MemFree:          107484 kB
	Buffers:          470592 kB
	Cached:           110684 kB
	SwapCached:          904 kB
	Active:           262476 kB
	Inactive:         453672 kB
	Active(anon):      24572 kB
	Inactive(anon):   142096 kB
	Active(file):     237904 kB
	Inactive(file):   311576 kB
	Unevictable:           0 kB
	Mlocked:               0 kB
	HighTotal:        126664 kB
	HighFree:           5312 kB
	LowTotal:         890180 kB
	LowFree:          102172 kB
	SwapTotal:       1038332 kB
	SwapFree:        1005956 kB
	Dirty:                 0 kB
	Writeback:             0 kB
	AnonPages:        134068 kB
	Mapped:            19084 kB
	Shmem:             31796 kB
	Slab:             174980 kB
	SReclaimable:     162588 kB
	SUnreclaim:        12392 kB
	KernelStack:        1664 kB
	PageTables:         2940 kB
	NFS_Unstable:          0 kB
	Bounce:                0 kB
	WritebackTmp:          0 kB
	CommitLimit:     1546752 kB
	Committed_AS:     404708 kB
	VmallocTotal:     122880 kB
	VmallocUsed:       12628 kB
	VmallocChunk:     108240 kB
	HardwareCorrupted:     0 kB
	AnonHugePages:         0 kB
	HugePages_Total:       0
	HugePages_Free:        0
	HugePages_Rsvd:        0
	HugePages_Surp:        0
	Hugepagesize:       2048 kB
	DirectMap4k:       32760 kB
	DirectMap2M:      880640 kB

b. dmidecode -t memory

➜  ~  sudo dmidecode -t memory 

	# dmidecode 2.11
	SMBIOS 2.4 present.

	Handle 0x000A, DMI type 16, 15 bytes
	Physical Memory Array
        Location: System Board Or Motherboard
        Use: System Memory
        Error Correction Type: None
        Maximum Capacity: 4 GB
        Error Information Handle: No Error
        Number Of Devices: 2

	Handle 0x000B, DMI type 17, 27 bytes
	Memory Device
        Array Handle: 0x000A
        Error Information Handle: No Error
        Total Width: Unknown
        Data Width: Unknown
        Size: No Module Installed
        Form Factor: SODIMM
        Set: None
        Locator: DIMM #1
        Bank Locator: Not Specified
        Type: DDR2
        Type Detail: Synchronous
        Speed: Unknown
        Manufacturer:                          
        Serial Number:         
        Asset Tag: Not Specified
        Part Number:                   

	Handle 0x000C, DMI type 17, 27 bytes
	Memory Device
        Array Handle: 0x000A
        Error Information Handle: No Error
        Total Width: 64 bits
        Data Width: 64 bits
        Size: 1024 MB
        Form Factor: SODIMM
        Set: None
        Locator: DIMM #2
        Bank Locator: Not Specified
        Type: DDR2
        Type Detail: Synchronous
        Speed: 667 MHz
        Manufacturer: Hyundai Electronics      
        Serial Number: 04008096
        Asset Tag: Not Specified
        Part Number: HYMP112S64CP6-Y5  

c. 内存插槽数，每条内存大小

➜  ~  sudo dmidecode -t memory |grep -i size

        Size: 8192 MB
        Size: 8192 MB
        Size: 8192 MB
        Size: 8192 MB
        Size: 8192 MB
        Size: 8192 MB
        Size: No Module Installed
        Size: No Module Installed
        Size: No Module Installed
        Size: 8192 MB
        Size: 8192 MB
        Size: 8192 MB
        Size: 8192 MB
        Size: 8192 MB
        Size: 8192 MB
        Size: No Module Installed
        Size: No Module Installed
        Size: No Module Installed

d. 最大支持内存

➜  ~  sudo dmidecode -t memory |grep -i max    

      Maximum Capacity: 288 GB

e. 内存频率

➜  ~  sudo dmidecode -t memory |grep -i speed

        Speed: 1333 MHz (0.8 ns)
        Speed: 1333 MHz (0.8 ns)
        Speed: 1333 MHz (0.8 ns)
        Speed: 1333 MHz (0.8 ns)
        Speed: 1333 MHz (0.8 ns)
        Speed: 1333 MHz (0.8 ns)
        Speed: Unknown
        Speed: Unknown
        Speed: Unknown
        Speed: 1333 MHz (0.8 ns)
        Speed: 1333 MHz (0.8 ns)
        Speed: 1333 MHz (0.8 ns)
        Speed: 1333 MHz (0.8 ns)
        Speed: 1333 MHz (0.8 ns)
        Speed: 1333 MHz (0.8 ns)
        Speed: Unknown
        Speed: Unknown
        Speed: Unknown


### 4. 硬盘
#### 4.1. lspci
a. LSI MagaSAS

➜  ~ lspci |grep -i raid

	03:00.0 RAID bus controller: LSI Logic / Symbios Logic LSI MegaSAS 9260 (rev 05)

tools

	megacli
	megasasctl/megactl
	megaraidsas-status/megaraid-status
	megclisas-status
	megamgr
		
b. Adaptec

➜  ~ lspci |grep -i raid

	02:00.0 RAID bus controller: Adaptec AAC-RAID (rev 09)

tools

	arcconf

#### 4.2. lsscsi
a. lsscsi

➜  ~ sudo lsscsi

	[0:0:0:0]    cd/dvd  Dell     Virtual  CDROM   123   /dev/scd0
	[1:0:0:0]    disk    Dell     Virtual  Floppy  123   /dev/sdc
	[2:0:0:0]    disk    ATA      Maxtor 7L250S0   1G10  /dev/sda
	[2:0:4:0]    disk    SEAGATE  ST3300555SS      T105  /dev/sdb

b. /proc/scsi/scsi

➜  ~ cat /proc/scsi/scsi

	Attached devices:
	Host: scsi2 Channel: 00 Id: 00 Lun: 00
	  Vendor: ATA      Model: Maxtor 7L250S0   Rev: 1G10    
	  Type:   Direct-Access                    ANSI SCSI revision: 05
	Host: scsi0 Channel: 00 Id: 00 Lun: 00
	  Vendor: Dell     Model: Virtual  CDROM   Rev: 123
	  Type:   CD-ROM                           ANSI SCSI revision: 02
	Host: scsi1 Channel: 00 Id: 00 Lun: 00
	  Vendor: Dell     Model: Virtual  Floppy  Rev: 123
	  Type:   Direct-Access                    ANSI SCSI revision: 02
	Host: scsi2 Channel: 00 Id: 04 Lun: 00
	  Vendor: SEAGATE  Model: ST3300555SS      Rev: T105
	  Type:   Direct-Access                    ANSI SCSI revision: 05

#### 4.3. smartctl
a. smartctl -a /dev/sda

➜  ~ sudo smartctl -a /dev/sda

	=== START OF INFORMATION SECTION ===
	Model Family:     Hitachi Travelstar 5K320
	Device Model:     Hitachi HTS543216L9A300
	Serial Number:    090107FB0200LCJJVXPB
	LU WWN Device Id: 5 000cca 561e3da05
	Firmware Version: FB2OC40F
	User Capacity:    160,041,885,696 bytes [160 GB]
	Sector Size:      512 bytes logical/physical
	Device is:        In smartctl database [for details use: -P show]
	ATA Version is:   8
	ATA Standard is:  ATA-8-ACS revision 3f
	Local Time is:    Tue Mar 26 12:52:42 2013 CST
	SMART support is: Available - device has SMART capability.
	SMART support is: Enabled

b. smartctl -a -d megaraid,1 /dev/sda

c. smartctl -a /dev/sda|grep -i serial

➜  ~ sudo smartctl -a /dev/sda|grep -i serial

	Serial Number:    090107FB0200LCJJVXPB

### 5. 网卡
#### 5.1. 网卡类型

lspci｜grep -i net

➜  ~ lspci|grep -i net

	16:00.0 Ethernet controller: Emulex Corporation OneConnect 10Gb NIC (be3) (rev 03)

	05:00.0 Ethernet controller: Broadcom Corporation NetXtreme II BCM5708 Gigabit Ethernet (rev 12)

	00:19.0 Ethernet controller: Intel Corporation 82562GT 10/100 Network Connection (rev 03)

	10:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)

#### 5.2. 网卡驱动
`升级系统的时候，就要查看下网卡驱动安装上了没，尤其是bnx系列网卡特别要注意`

update-initramfs -u -k \`uname -r\`

#### 5.3. 查看工具
a. ethtool

➜  ~  sudo ethtool eth0 

	Settings for eth0:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
        Supported pause frame use: No
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
        Advertised pause frame use: No
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 1
        Transceiver: internal
        Auto-negotiation: on
        MDI-X: off
        Supports Wake-on: pumbg
        Wake-on: g
        Current message level: 0x00000001 (1)
                               drv
        Link detected: yes

b. mii－tool

➜  ~ sudo mii-tool

	eth0: negotiated 1000baseT-FD flow-control, link ok
	eth1: negotiated 1000baseT-FD flow-control, link ok
	SIOCGMIIPHY on 'eth2' failed: Resource temporarily unavailable
	SIOCGMIIPHY on 'eth3' failed: Resource temporarily unavailable

c. ip addr

➜  ~  ip addr

	1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
	2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
    link/ether 00:24:81:36:37:a7 brd ff:ff:ff:ff:ff:ff
    inet 192.168.144.242/22 brd 192.168.147.255 scope global eth0
    inet6 fe80::224:81ff:fe36:37a7/64 scope link 
       valid_lft forever preferred_lft forever
	3: eth2: <BROADCAST,MULTICAST> mtu 1500 qdisc pfifo_fast state DOWN qlen 1000
    link/ether 00:21:00:a4:49:f6 brd ff:ff:ff:ff:ff:ff

## 二、内存
### 1. free
	➜  ~  free -m
             total       used       free     shared    buffers     cached
	Mem:           993        914         78          0        132        607
	-/+ buffers/cache:        174        818
	Swap:         1013         10       1003
	
	free 详解
	1. total: 内存总数
	2. used：已经使用的内存数
	3. free： 空闲的内存数
	4. shared： 多个进程共享的内存总额
	5. -buffers/cache: （已用）的内存数，即used-buffers-cached //反映实际被用掉的内存数
	6. +buffers/cache: (可用)的内存数，即free+buffers+cached //反映可以使用的内存数
	可用内存的计算公式为：
           可用内存=free+buffers+cached,即399M+109M+723M=1232M
	内存总数与已使用内存数和空闲内存数的关系：
         total（1968M）=used（1569M）+free（399M）

	注：观察Linux的内存使用情况时，只要没有发现用swap的交换空间，就不用担心自己的内存太少；如果常常看到swap用了很多，那么就要考虑增加物理内存了。这也是在Linux服务器上看内存是否够用的标准。

### 2. vmstat
a. vmstat 1 

➜  ~ vmstat -S M 1 5

	procs -----------memory---------- ---swap-- -----io---- -system-- ----cpu----
	r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa
 	1  0      1  56541    384  36313    0    0    10   152    0    0  3  1 95  1
 	1  0      1  56543    384  36313    0    0   128   168 7271 11527  1  0 99  0
	0  0      1  56542    384  36313    0    0     0   112 6045 9615  1  0 99  0
 	0  0      1  56543    384  36313    0    0   132   192 11305 17468  1  1 98  0
 	0  0      1  56539    384  36313    0    0   128   456 13028 20222  1  1 98  0

b. vmstat -a

➜  ~ vmstat -S M 1 5 -a

	procs -----------memory---------- ---swap-- -----io---- -system-- ----cpu----
 	r  b   swpd   free  inact active   si   so    bi    bo   in   cs us sy id wa
	 2  0      1  56540  30690   7020    0    0    10   152    0    0  3  1 95  1
 	1  0      1  56543  30690   7017    0    0   128   200 8258 12908  1  1 99  0
 	0  0      1  56540  30691   7020    0    0     0   176 8696 13414  1  1 98  0
 	1  0      1  56543  30691   7017    0    0   128  1116 11617 17652  1  0 98  0
 	0  0      1  56541  30691   7019    0    0     0   176 7946 12529  1  0 99  0

c. vmstat -s

➜  ~ vmstat -s

	     99197360 K total memory
	     41313428 K used memory
	      7193792 K active memory
	     31438464 K inactive memory
	     57883936 K free memory
	       394068 K buffer memory
	     37204624 K swap cache
	      2096444 K total swap
	         1992 K used swap
	      2094452 K free swap
	   1277643835 non-nice user cpu ticks
	           11 nice user cpu ticks
	    371033881 system cpu ticks
	  41192773129 idle cpu ticks
	    247499620 IO-wait cpu ticks
	        39100 IRQ cpu ticks
	     48138900 softirq cpu ticks
	            0 stolen cpu ticks
	   4450333523 pages paged in
	  65678511936 pages paged out
	       132467 pages swapped in
	       180917 pages swapped out
	   1237774778 interrupts
	   3301154853 CPU context switches
	   1346296992 boot time
	     44515969 forks


### 3. ps
a. ps aux
b. ps -e -o "%c : %p : %z :%a" |sort -k5 -nr|head

### 4. dstat
a. dstat -ms

➜  ~ dstat -ms 1 5

    ------memory-usage----- ----swap---
     used  buff  cach  free| used  free
    3639M  385M 35.6G 55.1G|1992k 2045M
    3641M  385M 35.6G 55.1G|1992k 2045M
    3638M  385M 35.6G 55.1G|1992k 2045M
    3638M  385M 35.6G 55.1G|1992k 2045M
    3638M  385M 35.6G 55.1G|1992k 2045M
    3641M  385M 35.6G 55.1G|1992k 2045M

b. dstat --top-mem

➜  ~ dstat --top-mem 1 5

    --most-expensive-
      memory process 
    mongod      35.0G
    mongod      35.0G
    mongod      35.0G
    mongod      35.0G
    mongod      35.0G
    mongod      35.0G

c. dstat -v

➜  ~ dstat -v 1 5

    ---procs--- ------memory-usage----- ---paging-- -dsk/total- ---system-- ----total-cpu-usage----
    run blk new| used  buff  cach  free|  in   out | read  writ| int   csw |usr sys idl wai hiq siq
    0.0   0 2.5|3649M  385M 35.6G 55.1G|  30B   41B| 247k 3638k|3162    20k|  3   1  95   1   0   0
    3.0   0 2.0|3646M  385M 35.6G 55.1G|   0     0 |   0   144k|7217    11k|  1   1  99   0   0   0
      0   0 1.0|3650M  385M 35.6G 55.1G|   0     0 | 176k  376k|  17k   28k|  1   1  98   0   0   0
    1.0   0 1.0|3647M  385M 35.6G 55.1G|   0     0 | 128k  160k|8258    13k|  1   0  99   0   0   0
    1.0   0 5.0|3648M  385M 35.6G 55.1G|   0     0 |   0   120k|8138    12k|  1   1  99   0   0   0
      0   0 1.0|3646M  385M 35.6G 55.1G|   0     0 | 128k  336k|  15k   23k|  1   1  98   0   0   0

### 5. top
### 6. slabtop
### 7. buffer 与 cache
		buffer与cache操作的对象不一样。
    	buffer(缓冲)是为了提高内存和硬盘(或其它I/O设备)之间的数据交换的速度而设计的。
    	cache(缓存)是为了提高cpu和内存之间的数据交换而设计的，也就是平常见到的一级缓存、二级缓存、三级缓存等。

    	cpu在执行程序所用的指令和读数据都是针对内存的，也就是从内存中取得的。由于内存的读写速度慢，为了提高cpu和内存之间的数据交换的速度，在cpu 和内存之间增加了cache，他的速度比内存块，但是造价高，又由于在cpu内不能集成太对集成电路，所以一般cache比较小，以后intel等公司为 了进一步提高速度，又增加了二级cache，甚至三级cache，它是根据程序的局部性原理而设计的，就是cpu执行的指令和访问的数据往往在集中的某一块，所以把这块内容放入cache后，cpu就不用再访问内存了，这就提高了访问速度。当然若cache中没有cpu所需要的内容，还是要访问内存的。
    	缓冲(buffers) 是根据磁盘的读写设计的，把分散的写操作集中进行，减少了磁盘碎片和硬盘的反复寻道，从而提高系统性能。linux有一个守护进程定期清空缓冲内容(即写入磁盘)，也可以通过sync命令手动清空缓冲。举个例子吧：我这里有一个ext2的U盘，我往里面copy一个3M的MP3.但U盘的灯没有跳动，过了 一会儿(或者手动输入sync)U盘的灯就跳动起来了。卸载设备时会清空缓冲，所以有些时候卸载一个设备要等上几秒钟。
    	修改/etc/sysctl.conf中的vm.swappiness右边的数字可以在下次开机时调节swap使用策略。该数字范围是0-100，数字越大越倾向于使用swap。默认为60，可以改一下试试。--两者都是RAM中的数据。
    	简单来说，buffer是即将要写入磁盘的，而cache是被从磁盘中读出来的。
    	buffer是由各种进程分配的，被用在如输入队列等方面。一个简单的例子如某个进程要求有多个字段读入，在所有字段被读入完整之前，进程就先前读入的字段放在buffer中保存。
    	cache经常被用在磁盘的I/O请求上，如果有多个进程都要访问某个文件，于是该文件便被做成cache以方便下次被访问，这样可提高系统性能。

## 三、CPU和进程状态
### 1.CPU
#### 1.1. top
#### 1.2. ps
#### 1.3. vmstat
#### 1.4. dstat
#### 1.6. pidstat
#### 1.7. mpstat
### 2. 进程
#### 2.1. 状态
#### 2.2. ps
#### 2.3. top 
#### 2.4. lsof
## 四、网络
### 1. 网卡状态
### 2. 网卡流量
### 3. 网络配置
### 4. 防火墙
### 5. 调试工具
#### 5.1. lsof
#### 5.2. telnet
#### 5.3. nc
#### 5.4. netstat
#### 5.5. tcpdump/wireshark
#### 5.6. nmap
#### 5.7. tc
## 五、文件系统和磁盘IO
### 1. 了解ext3，ext4，xfs，swap
### 2. 会使用文件系统调试工具
### 3. 熟悉iostat，iotop
### 4. 了解目录挂载，磁盘挂载，阅读fstab
### 5. 增减swap
### 6. 查看文件占用空间
### 7. 查看文件系统占用空间
### 8. 查找进程打开的文件
### 9. raid管理
## 六、Troubleshooting
### 1. dmesg
### 2. vmstat
### 3. top/iostat/free
### 4. last/lastlog
### 5. log
### 6. shell
### 7. 经验
## 七、在线资源调整
### 1. /etc/sysctl.conf
### 2. /etc/sysfs.conf
### 3. sysctl
### 4. /proc
### 5. /sys
## 八、其他
### 1. 基本命令
#### 1.1. awk
#### 1.2. sed
#### 1.3. find
#### 1.4. grep/egrep
### 2. 配置管理
#### 2.1. git
#### 2.2. svn
### 3. 窗口管理
#### 3.1. tmux
#### 3.2. screen 