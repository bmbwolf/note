# vmstat

    Procs
        r: The number of processes waiting for run time.
        b: The number of processes in uninterruptible sleep.

    Memory
        swpd: the amount of virtual memory used.
        free: the amount of idle memory.
        buff: the amount of memory used as buffers.
        cache: the amount of memory used as cache.
        inact: the amount of inactive memory.  (-a option)
        active: the amount of active memory.  (-a option)

    Swap
        si: Amount of memory swapped in from disk (/s).
        so: Amount of memory swapped to disk (/s).

    IO
        bi: Blocks received from a block device (blocks/s).
        bo: Blocks sent to a block device (blocks/s).

    System
        in: The number of interrupts per second, including the clock.
        cs: The number of context switches per second.

    CPU
        These are percentages of total CPU time.
        us: Time spent running non-kernel code.  (user time, including nice time)
        sy: Time spent running kernel code.  (system time)
        id: Time spent idle.  Prior to Linux 2.5.41, this includes IO-wait time.
        wa: Time spent waiting for IO.  Prior to Linux 2.5.41, included in idle.
        st: Time stolen from a virtual machine.  Prior to Linux 2.6.11, unknown.

    vmstat -SM 1
    procs -----------memory---------- ---swap-- -----io---- -system-- ----cpu----
     r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa
     2  1      0   6460   1325  18597    0    0     1    54    0    0  3  4 91  2
     0  0      0   6462   1325  18598    0    0     0  2752 103941 48702  4  5 87  4
     1  0      0   6458   1325  18599    0    0     0   752 107797 42520  5  6 89  0
     1  0      0   6459   1325  18600    0    0     0  2716 100859 44200  4  6 87  2
     2  0      0   6457   1325  18601    0    0     0     0 114574 46797  5  6 89  0


context switch cause system interrupts
