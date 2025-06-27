The most common state codes you'll see are described below:

- R: running or runnable, it is just waiting for the CPU to process it.
- S: Interruptible sleep, waiting for an event to complete, such as input from the terminal.
- D: Uninterruptible sleep, processes that cannot be killed or interrupted with a signal, usually to make them go away you have to reboot or fix the issue.
- Z: Zombie, we discussed in a previous lesson that zombies are terminated processes that are waiting to have their statuses collected.
- T: Stopped, a process that has been suspended/stopped.