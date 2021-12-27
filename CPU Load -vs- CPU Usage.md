# CPU Load -vs- CPU Usage:

Even though `CPU load` and `CPU usage` sound similar, they are not interchangeable.  
`CPU load` is defined as the number of processes using or waiting to use one core at a single point in time.  

**CPU Load:**  
Let's say we have a single-core system, and our CPU load average is always below 0.6.  
This indicates that every process that needs to use the CPU can use it instantly without waiting.  
If the CPU load average is above 1,  
this indicates that there are processes that need to use the CPU but cannot at the moment due to the unavailability of the CPU.  

However, the load average above 1 in a multi-processor system won’t be an issue since more cores are readily available.  

The `uptime` command gives us a view of the `cpu load average` at 1, 5, and 15-minute intervals:  
```shell
[root@localhost ~]# uptime
12:40:05 up  2:29,  1 user,  load average: 0.37, 0.08, 0.03
```

Now, to interpret the above output, let's know how many cores are present on the machine:  
```shell
[root@localhost ~]# cat /proc/cpuinfo | grep core
core id		: 0
cpu cores	: 1
```

**CPU Usage:**  
`CPU usage` is the percentage of time a CPU takes to process non-idle tasks.  
`CPU Usage` can only be measured over a specified interval of time.  
We can determine the `CPU usage` by taking the percentage of time spent idling and subtracting it from 100.  

**Reference:**  
1. https://www.baeldung.com/linux/get-cpu-usage

