Suppose you're working on a single terminal window and you're running a command that is taking forever. You can't interact with the shell until it is complete.
however we want to keep working on our machines, so we need that shell open.
There is a way for this. we have to run the process with background jobs.

## **Sending a job to background**

Appending an ampersand (&) sign at the end of the command will run the command in background. You can still use your shell.

```bash
$  sleep 1000 &

[1] 1636

$  sleep 1001 &

[2] 1637
```

## **View all background jobs**

To view the jobs you add use `jobs` commands.

```bash
$  jobs

[1]   Running                 sleep 1000 &
[2]-  Running                 sleep 1001 &
[3]+  Running                 sleep 1002 &
```
This will show you:
- The job id in the first column, then the status and the command that was run. 
- The **+** next to the job ID means that it is the most recent background job that started. 
- The job with the **-** is the second most recent command.

## **Sending a job to the background on existing job**

If you already ran a job and want to send it to the background, you don't have to terminate it and start over again. First suspend the job with Ctrl-Z, then run the **bg** command to send it to the background.

```bash
$  sleep 1003

^Z
[4]+  Stopped                 sleep 1003

$  bg

[4]+ sleep 1003 &
```

## **Moving a job from the background to the foreground**

To move a job out of the background just specify the job ID you want. If you run fg without any options, it will bring back the most recent background job (the job with the + sign next to it)

```bash
$  fg %1
```

## **Kill background jobs**

Similar to moving jobs out of the background, you can use the same form to kill the processes by using their Job ID.
```bash
$  kill %1
```

