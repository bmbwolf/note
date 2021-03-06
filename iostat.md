#Linux iostat监测IO状态
----

Linux系统出现了性能问题，一般我们可以通过top、iostat、free、vmstat等命令来查看初步定位问题。其中iostat可以给我们提供丰富的IO状态数据。
#####1. 基本参数
	$iostat -d -k 1 10

	参数 -d 表示，显示设备（磁盘）使用状态；-k某些使用block为单位的列强制使用Kilobytes为单位；1 10表示，数据显示每隔1秒刷新一次，共显示10次。

	$iostat -d -k 1 10
	Device: tps kB_read/s kB_wrtn/s kB_read kB_wrtn
	sda 39.29 21.14 1.44 441339807 29990031
	sda1 0.00 0.00 0.00 1623 523
	sda2 1.32 1.43 4.54 29834273 94827104
	sda3 6.30 0.85 24.95 17816289 520725244
	sda5 0.85 0.46 3.40 9543503 70970116
	sda6 0.00 0.00 0.00 550 236
	sda7 0.00 0.00 0.00 406 0
	sda8 0.00 0.00 0.00 406 0
	sda9 0.00 0.00 0.00 406 0
	sda10 60.68 18.35 71.43 383002263 1490928140

	Device: tps kB_read/s kB_wrtn/s kB_read kB_wrtn
	sda 327.55 5159.18 102.04 5056 100
	sda1 0.00 0.00 0.00 0 0
	...

	tps：该设备每秒的传输次数（Indicate the number of transfers per second that were issued to the device.）。“一次传输”意思是“一次I/O请求”。多个逻辑请求可能会被合并为“一次I/O请求”。“一次传输”请求的大小是未知的。

	kB_read/s：每秒从设备（drive expressed）读取的数据量；	kB_wrtn/s：每秒向设备（drive expressed）写入的数据量；	kB_read：读取的总数据量；kB_wrtn：写入的总数量数据量；这些单位都为Kilobytes。

	上面的例子中，我们可以看到磁盘sda以及它的各个分区的统计数据，当时统计的磁盘总TPS是39.29，下面是各个分区的TPS。（因为是瞬间值，所以总TPS并不严格等于各个分区TPS的总和）

#####2. -x 参数

	使用-x参数我们可以获得更多统计信息。

	iostat -d -x -k 1 10
	Device: rrqm/s wrqm/s r/s w/s rsec/s wsec/s rkB/s wkB/s avgrq-sz avgqu-sz await svctm %util
	sda 1.56 28.31 7.80 31.49 42.51 2.92 21.26 1.46 1.16 0.03 0.79 2.62 10.28
	Device: rrqm/s wrqm/s r/s w/s rsec/s wsec/s rkB/s wkB/s avgrq-sz avgqu-sz await svctm %util
	sda 2.00 20.00 381.00 7.00 12320.00 216.00 6160.00 108.00 32.31 1.75 4.50 2.17 84.20

	rrqm/s：每秒这个设备相关的读取请求有多少被Merge了（当系统调用需要读取数据的 时候，VFS将请求发到各个FS，如果FS发现不同的读取请求读取的是相同Block的数据，FS会将这个请求合并Merge）；wrqm/s：每秒这个 设备相关的写入请求有多少被Merge了。

	rsec/s：每秒读取的扇区数；wsec/：每秒写入的扇区数。r/s：The number of read requests that were issued to the device per second；w/s：The number of write requests that were issued to the device per second；

	await：每一个IO请求的处理的平均时间（单位是微秒毫秒）。这里可以理解为IO的响应时间，一般地系统IO响应时间应该低于5ms，如果大于10ms就比较大了。
	----------------------------
	%util：在统计时间内所有处理IO时间，除以总共统计时间。例如，如果统计间隔1秒，该 设备有0.8秒在处理IO，而0.2秒闲置，那么该设备的%util = 0.8/1 = 80%，所以该参数暗示了设备的繁忙程度。一般地，如果该参数是100%表示设备已经接近满负荷运行了（当然如果是多磁盘，即使%util是100%，因 为磁盘的并发能力，所以磁盘使用未必就到了瓶颈）。
	----------------------------

#####3. -c 参数

	iostat还可以用来获取cpu部分状态值：

	iostat -c 1 10
	avg-cpu: %user %nice %sys %iowait %idle
	1.98 0.00 0.35 11.45 86.22
	avg-cpu: %user %nice %sys %iowait %idle
	1.62 0.00 0.25 34.46 63.67

#####4. 常见用法

	iostat -d -k 1 10 #查看TPS和吞吐量信息
	iostat -d -x -k 1 10 #查看设备使用率（%util）、响应时间（await）
	iostat -c 1 10 #查看cpu状态

######5. 实例分析

	$iostat -d -k 1 |grep sda10
	Device: tps kB_read/s kB_wrtn/s kB_read kB_wrtn
	sda10 60.72 18.95 71.53 395637647 1493241908
	sda10 299.02 4266.67 129.41 4352 132
	sda10 483.84 4589.90 4117.17 4544 4076
	sda10 218.00 3360.00 100.00 3360 100
	sda10 546.00 8784.00 124.00 8784 124
	sda10 827.00 13232.00 136.00 13232 136

	上面看到，磁盘每秒传输次数平均约400；每秒磁盘读取约5MB，写入约1MB。

	iostat -d -x -k 1
	Device: rrqm/s wrqm/s r/s w/s rsec/s wsec/s rkB/s wkB/s avgrq-sz avgqu-sz await svctm %util
	sda 1.56 28.31 7.84 31.50 43.65 3.16 21.82 1.58 1.19 0.03 0.80 2.61 10.29
	sda 1.98 24.75 419.80 6.93 13465.35 253.47 6732.67 126.73 32.15 2.00 4.70 2.00 85.25
	sda 3.06 41.84 444.90 54.08 14204.08 2048.98 7102.04 1024.49 32.57 2.10 4.21 1.85 92.24

	可以看到磁盘的平均响应时间<5ms，磁盘使用率>80。磁盘响应正常，但是已经很繁忙了。