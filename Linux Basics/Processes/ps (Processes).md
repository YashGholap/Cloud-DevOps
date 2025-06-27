Processes are the programs that are running on your machine. They are managed by the kernel and each process has an ID associated with it called the **process ID (PID).**
To see the processes running type `ps` in bash:

```bash
$  ps

PID TTY          TIME CMD
571 pts/0    00:00:00 bash
1489 pts/0    00:00:00 ps
```

Another Important command is:

```bash
$  ps aux
```

The `a` here displays all processes running, including the ones being ran by other users.
The `u` shows more details about the processes.
The `x` ists all processes that don't have a TTY associated with it. These programs show `?` in TTY field.

You'll notice you're seeing a lot more fields now:
- USER: The effective user (the one whose access we are using)
- PID: Process ID
- %CPU: CPU time used divided by the time the process has been running
- %MEM: Ratio of the process's resident set size to the physical memory on the machine
- VSZ: Virtual memory usage of the entire process
- RSS: Resident set size, the non-swapped physical memory that a task has used
- TTY: Controlling terminal associated with the process
- STAT: Process status code
- START: Start time of the process
- TIME: Total CPU usage time
- COMMAND: Name of executable/command

# top

Another very useful command is the **top** command, top gives you real time information about the processes running on your system instead of a snapshot. By default you'll get a refresh every 10 seconds. Top is an extremely useful tool to see what processes are taking up a lot of your resources.

```bash
$  top
```
