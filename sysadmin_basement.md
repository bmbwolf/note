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
### 4. 硬盘
### 5. 网卡
## 二、内存
### 1. free
### 2. vmstat
### 3. ps
### 4. dstat
### 5. top
### 6. slabtop
### 7. buffer 与 cache
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