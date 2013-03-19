# Linux硬件信息查看


----------------------------------

##1, 主板信息
	查看主板的序列号
	--------------------------------------------------
	#使用命令
	dmidecode | grep -i 'serial number'
	#查看板卡信息
	cat /proc/pci

##2, cpu信息
	#通过/proc文件系统
	1) cat /proc/cpuinfo
	#通过查看开机信息
	2) dmesg | grep -i 'cpu'
	3)dmidecode -t processor
	--------------------------------------------------
##3, 硬盘信息
	#查看分区情况
	fdisk -l
	#查看大小情况
	df -h
	#查看使用情况
	du -h
	#
	hdparm -I /dev/sda
	#
	dmesg | grep sda
	实例:
	#查看硬盘sn
	[root@]# smartctl -d scsi -a /dev/sda | grep -i Serial
	--------------------------------------------------
##4, 内存信息
	1) cat /proc/meminfo
	2) dmesg | grep mem
	3) free -m
	4) vmstat
	5) dmidecode | grep -i mem
	--------------------------------------------------

#####a. 内存的插槽数,已经使用多少插槽.每条内存多大，已使用内存多
	dmidecode | grep -P -A 5 "Memory\s+Device" | grep Size | grep -v Range
	Size: 2048 MB
	Size: 2048 MB
	Size: No Module Installed
	Size: No Module Installed
	Size: No Module Installed
	Size: No Module Installed
	Size: No Module Installed
	Size: No Module Installed

#####b. 支持的最大内存容量
	dmidecode | grep -P 'Maximum\s+Capacity'
	Maximum Capacity: 64 GB

#####c. 查看内存的频率 
	dmidecode | grep -A16 "Memory Device"
	dmidecode | grep -A16 "Memory Device" | grep 'Speed'
	Speed: 667 MHz (1.5 ns)
	Speed: 667 MHz (1.5 ns)
	Speed: 667 MHz (1.5 ns)
	Speed: 667 MHz (1.5 ns)
	Speed: 667 MHz (1.5 ns)
	Speed: 667 MHz (1.5 ns)
	Speed: 667 MHz (1.5 ns)
	Speed: 667 MHz (1.5 ns)
##5, 网卡信息
	1) dmesg | grep -i 'eth'
	2) cat /etc/sysconfig/hwconf | grep -i eth
	3) lspci | grep -i 'eth'
	--------------------------------------------------
##6, 鼠标键盘和USB信息
	查看键盘和鼠标：cat /proc/bus/input/devices
	查看USB设备：cat /proc/bus/usb/devices
	查看各设备的中断请求(IRQ):cat /proc/interrupts
##7, 显卡信息
	1)lspci |grep -i 'VGA'
	2)dmesg | grep -i 'VGA'
	--------------------------------------------------
##8, 声卡信息
	1)lspci |grep -i 'VGA'
	2)dmesg | grep -i 'VGA'
	--------------------------------------------------
##9, 其他命令
	用硬件检测程序kuduz探测新硬件：service kudzu start ( or restart)
	dmesg (查看所有启动时检测到的硬件信息)
	lspci (显示外设信息, 如usb，网卡等信息)
	cat /etc/sysconfig/hwconf
	mpstat
##dmidecode信息查看	
	查看机器型号    # dmidecode | grep "Product"
    查看厂商    # dmidecode| grep  "Manufacturer"
    查看序列号    # dmidecode | grep  "Serial Number"
    查看CPU信息    # dmidecode | grep  "CPU"
    查看CPU个数    # dmidecode | grep  "Socket Designation: CPU" |wc --l
    查看出厂日期    # dmidecode | grep "Date"