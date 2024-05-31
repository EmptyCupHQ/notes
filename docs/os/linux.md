# Linux
## Processes
1. `systemd`: This daemon is an `Init process` started first and thus has the process ID (PID) `1`. This daemon monitors and takes care of the orderly starting and stopping of other services.

2. All the background services can be listed using:
```
systemctl list-units --type=service
```

3. All running processes can be listed using `ps -aux`.

4. To add any service to the SysV script(/lib/systemd/systemd-sysv-install) to tell the system to run this service after startup, we can link it with the following command:
```
systemctl service_name start
```

5. Automatically set a process to run in background by adding an `&` to the end of command.
`ping -c 10 www.google.com &`

6. We can use the `jobs` command to list all background processes. `fg <ID>` to bring a background process to foreground.

7. Processes can be controlled using `kill`, `pkill`, `pgrep`, and `killall`. To interact with a process, we must send a signal to it.

```
kill 9 <PID>
```

The most commonly used are:

| Signal      | Description                          |
| ----------- | ------------------------------------ |
| `SIGHUP`       | **1** This is sent to a process when the terminal that controls it is closed.  |
| `SIGINT`       | **2** Sent when a user presses [Ctrl] + C in the controlling terminal to interrupt a process. |
| `SIGQUIT`    |  **3** Sent when a user presses [Ctrl] + D to quit. |
| `SIGKILL`    |  **9** Immediately kill a process with no clean-up operations. |
| `SIGTERM`    |  **15** Program termination. |
| `SIGSTOP`    |  **19** Stop the program. It cannot be handled anymore. |
| `SIGTSTP`    |  **20** Sent when a user presses [Ctrl] + Z to request for a service to suspend. The user can handle it afterward. (Background a process) |

## Threads
1. A process can do more than one unit of work concurrently by creating one or more threads. These threads, being lightweight processes(LWP), can be spawned quickly.

2. Therefore, a process can be single-threaded or multi-threaded. Use `ps -eLf` and check which process(`PID`) is running how many threads(`NLWP`)

3. Any thread created within the process shares the same memory and resources of the process. In a single-threaded process, the process and thread are the same, as there’s only one thing happening.

4. Spawning a new thread within a process becomes cheap (in terms of the system resources) compared to starting a new process.

## Memory Paging
1. Memory paging is a memory management scheme by which a computer stores and retrieves data from secondary storage for use in main memory.

2. Memory Division into Pages and Frames:<br>
**Pages**: The process's virtual memory is divided into fixed-size blocks called pages.<br>
**Frames**: The physical memory (RAM) is divided into blocks of the same size called frames.

3. Page Table: Each process has a page table that maps its virtual pages to the physical frames in RAM. The page table keeps track of where each page of the process's virtual memory is stored in physical memory.

4. Address Translation: When a process accesses memory, the CPU translates the virtual address to a physical address using the page table. The virtual address consists of a page number and an offset within that page. The page number is used to find the corresponding frame number from the page table.

5. Page Faults: If a process tries to access a page that is not currently in physical memory, a page fault occurs.
The operating system then loads the required page from secondary storage (like a hard drive) into a free frame in physical memory.

6. Benefits:<br>
**Efficient Use of Memory**: Paging allows for efficient use of physical memory by loading only the necessary pages into RAM, rather than the entire process.<br>
**Isolation and Protection**: It provides isolation between processes, as each process operates in its own virtual address space, which enhances security and stability.



## Process Forking
1. The `fork()` system call is used for creating a new process in Unix/Linux.

2. The child process created by the process that makes the `fork()`​ call. After child process creation, both parent and child process executes the next instruction.

3. `fork()`​​ will not take any arguments but return integer.
Return Values:

| Return Value      | Description                          |
| ----------- | ------------------------------------ |
| **+ve**       | The creation of child process is unsuccessful.  |
| **0**       | Returned to the newly created child process.  |
| **-ve**       | Returned to the parent or Caller. The value contains the process ID of the newly created child process.  |

## Race Condition
1. A Race condition is a scenario that occurs in a multithreaded environment due to multiple threads sharing the same resource or executing the same piece of code. If not handled properly, this can lead to an undesirable situation, where the output state is dependent on the order of execution of the threads.
In simple words, if two threads/processes try to execute the same operations at the same time, then these two threads are in a `race`, in which one thread has to lose.

2. There are two types of race conditions in an OS:<br>
**Read-modify-write**: This kind of race condition happens when two processes read a value in a program and write back a new value.<br>
**check-then-act**: This race condition happens when two processes check a value on which they will take external action.

3. `Critical Section` of a code: part that is executed by multiple threads.

4. The ideal way to prevent a race-around condition is by controlling access to the critical section of your code.

5. Race conditions can leave the system vulnerable to security attacks where attackers can tamper with the shared data.

## Mutual Exclusion (Mutex)
1. A mutual exclusion (`mutex`) is a program object that prevents multiple threads from accessing the same shared resource simultaneously.

2. A mutex ensures that the threads carry out their operations like the two threads, with each thread accessing the critical section of code one at a time. This way, they don't step over each other and return undesired results, but instead behave in a controlled and predictable manner.

## Locks
1. A multithreaded program can specifically request a mutex for each shared resource from the underlying system.

2. If a thread needs to access the resource, it must first verify whether the mutex for that resource is locked. If it is unlocked, the thread can execute the code's critical section. If it is locked, the system typically queues the thread until the mutex becomes unlocked. When this occurs, the thread can execute the critical section, while the mutex is again locked to prevent other threads from using the resource.

## Semaphores
1. It is a process synchronization tool. A semaphore is an integer variable, shared among multiple processes.

2. The main aim of using a semaphore is process synchronization and access control for a common resource in a concurrent environment.

3. There are two types of semaphores:<br>
Binary semaphore<br>
Counting Semaphore

4. A binary semaphore can have only two integer values: 0 or 1. It’s simpler to implement and provides mutual exclusion. We can use a binary semaphore to solve the critical section problem.

__NOTE__:  A semaphore is a signaling mechanism where on the other hand, a mutex is a locking mechanism.

5. A counting semaphore is again an integer value, which can range over an unrestricted domain. We can use it to resolve synchronization problems like resource allocation.

## Load Average
1. Load average in Linux measures the usage of system resources. Understanding this metric helps sysadmins identify and troubleshoot performance issues.

2. There are various tools to monitor the load average such as: `uptime`, `top`, `w`, `cat /proc/loadavg`, `glances`

```
$ uptime
16:02:11 up  7:56,  3 users,  load average: 1.06, 0.55, 0.37
```

The system is running from 7 hours and 56 mins since last boot.<br>
The load average for 3 users is:<br>
1.06 for the past 1 minute.<br>
0.55 for the past 5 minutes.<br>
0.37 for the past 15 minutes.<br>

The results are calculated by dividing the number of running and waiting processes by the number of available CPU cores.

## Signals
1. A signal is a kind of (usually software) interrupt, used to announce asynchronous events to a process.

2. The name of a LINUX signal begins with "SIG". Although signals are numbered, we normally refer to them by their names.

3. List all the signals that can be sent to any process.
```
$ kill -l
 1) SIGHUP       2) SIGINT       3) SIGQUIT      4) SIGILL       5) SIGTRAP
 6) SIGABRT      7) SIGBUS       8) SIGFPE       9) SIGKILL     10) SIGUSR1
11) SIGSEGV     12) SIGUSR2     13) SIGPIPE     14) SIGALRM     15) SIGTERM
16) SIGSTKFLT   17) SIGCHLD     18) SIGCONT     19) SIGSTOP     20) SIGTSTP
21) SIGTTIN     22) SIGTTOU     23) SIGURG      24) SIGXCPU     25) SIGXFSZ
26) SIGVTALRM   27) SIGPROF     28) SIGWINCH    29) SIGIO       30) SIGPWR
31) SIGSYS      34) SIGRTMIN    35) SIGRTMIN+1  36) SIGRTMIN+2  37) SIGRTMIN+3
38) SIGRTMIN+4  39) SIGRTMIN+5  40) SIGRTMIN+6  41) SIGRTMIN+7  42) SIGRTMIN+8
43) SIGRTMIN+9  44) SIGRTMIN+10 45) SIGRTMIN+11 46) SIGRTMIN+12 47) SIGRTMIN+13
48) SIGRTMIN+14 49) SIGRTMIN+15 50) SIGRTMAX-14 51) SIGRTMAX-13 52) SIGRTMAX-12
53) SIGRTMAX-11 54) SIGRTMAX-10 55) SIGRTMAX-9  56) SIGRTMAX-8  57) SIGRTMAX-7
58) SIGRTMAX-6  59) SIGRTMAX-5  60) SIGRTMAX-4  61) SIGRTMAX-3  62) SIGRTMAX-2
63) SIGRTMAX-1  64) SIGRTMAX
```

4. Kill a process with id = PID
```
$ kill 9 <PID>
```

## Unix Domain Sockets
1. `Unix Domain Sockets` (UDS) are a communication mechanism in Unix-based systems that enable data exchange between processes running on the same machine. They are used for `inter-process communication` (IPC) and offer several advantages over traditional network sockets when the communication does not need to cross the network boundary.

2. Sockets provide a means of communication between processes, i.e. a way for them to exchange data. The way it usually works is that `process_a` has `socket_x`, `process_b` has `socket_y`, and the two `sockets` are connected. Each process can then use its socket to receive data from the other process and/or send data to the other process.

2. **Local Communication**: Unlike network sockets, UDS only work within the same host.

3. **File System Integration**: UDS are represented as files (for eg. `/var/run/docker.sock`) in the file system.

4. **Performance**: They are generally faster than TCP/IP sockets because they bypass the network stack and have lower overhead.
5. **Security**: UDS benefit from Unix file system permissions, which can be used to restrict access.