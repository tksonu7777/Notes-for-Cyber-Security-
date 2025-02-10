<details>
  <summary>OS 2023-2024</summary>


---
---
![image](https://github.com/user-attachments/assets/9754cfb8-46a4-4833-823c-2de4bb1f510a)
![image](https://github.com/user-attachments/assets/3c714439-140e-4c7b-905b-d2ff6b6ba9a7)
![image](https://github.com/user-attachments/assets/8ef4736c-dd02-4184-b1a1-3e3aa42ee353)
![image](https://github.com/user-attachments/assets/caaf9d4a-b311-4f9c-802b-8cfdb1e5ba3f)
![image](https://github.com/user-attachments/assets/278b2226-b2c6-4ed0-af93-da855e0e60f0)
![image](https://github.com/user-attachments/assets/2de1bcbe-aae3-49ed-81ab-53711c3d2145)



</details>


---
---
<details>
  <summary>OS 2021-2022</summary>


---
---

![image](https://github.com/user-attachments/assets/d5c73eae-2eab-4201-94d9-7130dd7d1a22)
![image](https://github.com/user-attachments/assets/390632d3-b358-465e-8d5c-ae99b3a7a28d)
![image](https://github.com/user-attachments/assets/88bff1cf-d6cd-4f3d-af43-f5c5db45065e)



</details>




---
---
<details>
  <summary>OS 2020</summary>


---
[Go](https://chatgpt.com/share/67a9957c-bcd0-8012-9458-9e67d73057fe)
---

![image](https://github.com/user-attachments/assets/2d50bc25-98eb-47b0-af5a-5f174f6899ce)
![image](https://github.com/user-attachments/assets/88dafcc5-5f56-495b-b19d-113e09aead09)
![image](https://github.com/user-attachments/assets/4cf859f8-30a7-48a0-8a2a-0a3ad37896b7)




---
---
# Answer 
<details>
  <summary>OS 2020</summary>


---
---


    
                                                                     PART-A

Q.1 What is Memory compaction? Why it is used?
  
  
Q.2 What are Device drivers?
  
  
Q.3 What is the difference between Absolute and Relative Path name of a file?
  
  
  
Q.4 What do you mean by Race Condition?
 
Q.5 A counting semaphore S is initialized to 10. Then 6p (wait) and 4v (signal) operations are performed on S. What is the final value of S.
  
 
Q.6 What are the various operations that can be performed on a file?

Q7.  Distinguish between Logical and Physical Address 
Q8.  What are the necessary conditions for the securrence of deadlock 
Q.9 What is the difference between Hard and Soft Real-time systems? 121
Q.10 List out reasons for process termination.





                                                                     PART-B 


 Q.1 What are System calls? Explain the various types of system calls with an example for each. 

Q.2 How is input/output request handled by the Device Manager? Also discuss functions of Device Driver.  


Q.3 Suppose Disk drive has 300 cylinders. The current position of head is 90. The queue of pending request is 36,79,15,120,199,270,89,170. Calculate total head movement using FCFS and SSTF disk scheduling algorithms.  


Q.4 What is a Process? Discuss various states of a process with help of a process state transition diagram.  


Q.5 Explain FCFS and Round Robin (19-2ms) scheduling algorithms with Gantt chart for the four processes given. Also compare their average turn-around and waiting time.  

 | Process | Arrival Time | Burst Time (in ms) |
|---------|--------------|--------------------|
| P₁      | 0            | 10                 |
| P₂      | 1            | 6                  |
| P₃      | 2            | 12                 |
| P₄      | 3            | 15                 |



Q.6 Explain various file system features of Linux operating system


Q.7 Given memory partitions of 100KB, 500KB, 200KB, 300KB and 600KB (in order). Show with neat sketch, how would processes of 210KB, 418KB, 120KB and 437KB (in order), be placed using: first fit, best fit and worst fit algorithms.





                                 PART - C


Q.1 What is paging? How paging helps in eliminating fragmentation? Explain Implementation of paging techniques using PLB



Q.2  
(a) What do you understand by Belady's Anomaly? Explain

(b) Consider the following page reference 
1,2,3,2,5,6,3,4,6,3,7,3,1,5,3,0,3,4,2,4,3,4,5,1 (consider frame size=4). Calculate total no. of page faults for FIFO, LRU and Optimal page replacement algorithms.

Q.3 What is Scheduling and why it is required? Also describe the differences among short-term, medium-term and long-term scheduling with suitable example.

Q.4 What is Deadlock Avoidance? Example Banker's Algorithm with following snapshot of a system with resources A, B, C and D and processes PO to P4:

|       | Max         | Allocation    | Available     |
|-------|-------------|---------------|---------------|
|       | A B C D     | A B C D       | A B C D       |
| P₀    | 6 0 1 2     | 4 0 0 1       | 3 2 1 1       |
| P₁    | 1 7 5 0     | 1 1 0 0       |               |
| P₂    | 2 3 5 6     | 1 2 5 4       |               |
| P₃    | 1 6 5 3     | 0 6 3 3       |               |
| P₄    | 1 6 5 6     | 0 2 1 2       |               |



(i) What are contents of Need Matrix?
(ii) Is the system in a safe state?
(iii) If a request from process P4 arrives for additional resources of (1, 2, 0, 0). Can request be granted immediately?




Q.5 Explain the following with suitable diagrams-
(i) Android OS and its architecture
(ii) Resource Allocation graph
(iii) Various file access methods
















### PART-A

**Q.1 What is Memory compaction? Why it is used?**  
Memory compaction is a technique used in memory management to reduce fragmentation. It involves moving all the allocated memory blocks to one end of the memory, thereby creating a large contiguous block of free memory. This helps in utilizing memory more efficiently and allows larger processes to be allocated memory even if the total free memory is sufficient but fragmented.

**Q.2 What are Device drivers?**  
Device drivers are software programs that allow the operating system to communicate with hardware devices. They act as a translator between the hardware and the operating system, enabling the OS to control and manage the hardware without needing to know the specifics of the hardware's operation.

**Q.3 What is the difference between Absolute and Relative Path name of a file?**  
- **Absolute Path**: Specifies the complete path from the root directory to the file. Example: `/home/user/documents/file.txt`.
- **Relative Path**: Specifies the path relative to the current working directory. Example: If the current directory is `/home/user`, the relative path to the file could be `documents/file.txt`.

**Q.4 What do you mean by Race Condition?**  
A race condition occurs when two or more processes access shared data concurrently, and the final outcome depends on the order of execution. This can lead to inconsistent or unexpected results if proper synchronization mechanisms are not in place.

**Q.5 A counting semaphore S is initialized to 10. Then 6p (wait) and 4v (signal) operations are performed on S. What is the final value of S.**  
- Initial value of S = 10
- 6p (wait) operations: S = 10 - 6 = 4
- 4v (signal) operations: S = 4 + 4 = 8
- Final value of S = 8

**Q.6 What are the various operations that can be performed on a file?**  
- Create
- Open
- Read
- Write
- Close
- Delete
- Seek
- Truncate
- Rename

**Q.7 Distinguish between Logical and Physical Address**  
- **Logical Address**: Generated by the CPU during program execution. It is a virtual address that the process uses to access memory.
- **Physical Address**: The actual address in the memory unit. The Memory Management Unit (MMU) translates logical addresses to physical addresses.

**Q.8 What are the necessary conditions for the occurrence of deadlock?**  
- **Mutual Exclusion**: Only one process can use a resource at a time.
- **Hold and Wait**: A process holds at least one resource and is waiting for additional resources that are currently held by other processes.
- **No Preemption**: Resources cannot be forcibly removed from a process; they must be released voluntarily.
- **Circular Wait**: A set of processes are waiting for each other in a circular chain.

**Q.9 What is the difference between Hard and Soft Real-time systems?**  
- **Hard Real-time Systems**: Strict deadlines must be met. Missing a deadline can lead to catastrophic failures. Example: Air traffic control systems.
- **Soft Real-time Systems**: Deadlines are important but not critical. Missing a deadline degrades performance but does not cause system failure. Example: Streaming media.

**Q.10 List out reasons for process termination.**  
- Normal completion
- Time limit exceeded
- Memory unavailable
- Bounds violation
- Protection error
- Arithmetic error
- I/O failure
- Invalid instruction
- Privileged instruction
- Data misuse
- Operator or OS intervention
- Parent termination
- Parent request

### PART-B

**Q.1 What are System calls? Explain the various types of system calls with an example for each.**  
System calls are interfaces provided by the operating system to allow user-level processes to request services from the kernel. Types of system calls include:
- **Process Control**: `fork()`, `exec()`, `exit()`
- **File Management**: `open()`, `read()`, `write()`, `close()`
- **Device Management**: `ioctl()`, `read()`, `write()`
- **Information Maintenance**: `getpid()`, `time()`
- **Communication**: `pipe()`, `shmget()`, `msgget()`

**Q.2 How is input/output request handled by the Device Manager? Also discuss functions of Device Driver.**  
The Device Manager handles I/O requests by:
1. Receiving the request from the process.
2. Translating the request into a form that the device can understand.
3. Sending the request to the appropriate device driver.
4. Managing the data transfer between the device and memory.
5. Notifying the process upon completion.

**Functions of Device Driver**:
- Initialize the device.
- Manage data transfer.
- Handle errors and exceptions.
- Provide an interface for the OS to interact with the hardware.

**Q.3 Suppose Disk drive has 300 cylinders. The current position of head is 90. The queue of pending request is 36,79,15,120,199,270,89,170. Calculate total head movement using FCFS and SSTF disk scheduling algorithms.**  
- **FCFS**: Total head movement = |90-36| + |36-79| + |79-15| + |15-120| + |120-199| + |199-270| + |270-89| + |89-170| = 54 + 43 + 64 + 105 + 79 + 71 + 181 + 81 = 678
- **SSTF**: Total head movement = |90-89| + |89-79| + |79-120| + |120-170| + |170-199| + |199-270| + |270-36| + |36-15| = 1 + 10 + 41 + 50 + 29 + 71 + 234 + 21 = 457

**Q.4 What is a Process? Discuss various states of a process with help of a process state transition diagram.**  
A process is an instance of a program in execution. The states of a process include:
- **New**: The process is being created.
- **Ready**: The process is waiting to be assigned to a processor.
- **Running**: Instructions are being executed.
- **Waiting**: The process is waiting for some event to occur.
- **Terminated**: The process has finished execution.

**Q.5 Explain FCFS and Round Robin (19-2ms) scheduling algorithms with Gantt chart for the four processes given. Also compare their average turn-around and waiting time.**  
- **FCFS**:
  - Gantt Chart: P₁(0-10), P₂(10-16), P₃(16-28), P₄(28-43)
  - Turn-around Time: P₁=10, P₂=15, P₃=26, P₄=40
  - Waiting Time: P₁=0, P₂=9, P₃=14, P₄=25
  - Average Turn-around Time = (10+15+26+40)/4 = 22.75
  - Average Waiting Time = (0+9+14+25)/4 = 12

- **Round Robin (Quantum=2ms)**:
  - Gantt Chart: P₁(0-2), P₂(2-4), P₃(4-6), P₄(6-8), P₁(8-10), P₂(10-12), P₃(12-14), P₄(14-16), P₁(16-18), P₃(18-20), P₄(20-22), P₃(22-24), P₄(24-26), P₃(26-28), P₄(28-30), P₄(30-32), P₄(32-34), P₄(34-36), P₄(36-38), P₄(38-40), P₄(40-42), P₄(42-43)
  - Turn-around Time: P₁=18, P₂=12, P₃=28, P₄=43
  - Waiting Time: P₁=8, P₂=6, P₃=16, P₄=28
  - Average Turn-around Time = (18+12+28+43)/4 = 25.25
  - Average Waiting Time = (8+6+16+28)/4 = 14.5

**Q.6 Explain various file system features of Linux operating system**  
- **Ext2/Ext3/Ext4**: Journaling file systems that provide reliability and performance.
- **XFS**: High-performance file system suitable for large files and high-speed data transfer.
- **Btrfs**: Modern file system with features like snapshots, pooling, and checksums.
- **Procfs**: Virtual file system that provides information about running processes.
- **Sysfs**: Virtual file system that exports kernel objects to user space.

**Q.7 Given memory partitions of 100KB, 500KB, 200KB, 300KB and 600KB (in order). Show with neat sketch, how would processes of 210KB, 418KB, 120KB and 437KB (in order), be placed using: first fit, best fit and worst fit algorithms.**  
- **First Fit**:
  - 210KB: 500KB partition
  - 418KB: 600KB partition
  - 120KB: 200KB partition
  - 437KB: No suitable partition

- **Best Fit**:
  - 210KB: 300KB partition
  - 418KB: 500KB partition
  - 120KB: 200KB partition
  - 437KB: 600KB partition

- **Worst Fit**:
  - 210KB: 600KB partition
  - 418KB: 500KB partition
  - 120KB: 300KB partition
  - 437KB: No suitable partition

### PART-C

**Q.1 What is paging? How paging helps in eliminating fragmentation? Explain Implementation of paging techniques using PLB**  
Paging is a memory management scheme that eliminates fragmentation by dividing memory into fixed-size blocks called pages. Each process is divided into pages, and these pages can be stored in any available frame in physical memory. This allows for efficient use of memory and reduces external fragmentation.

**Implementation using Page Table Base Register (PTBR)**:
- The PTBR points to the page table of the current process.
- Each page table entry (PTE) contains the frame number where the page is stored.
- The CPU generates a logical address, which is divided into a page number and an offset.
- The page number is used to index into the page table to find the frame number.
- The frame number is combined with the offset to form the physical address.

**Q.2**  
**(a) What do you understand by Belady's Anomaly? Explain**  
Belady's Anomaly is a phenomenon in page replacement algorithms where increasing the number of page frames can lead to an increase in the number of page faults. This is counterintuitive as one would expect more frames to reduce page faults. It is commonly observed in the FIFO page replacement algorithm.

**(b) Consider the following page reference 1,2,3,2,5,6,3,4,6,3,7,3,1,5,3,0,3,4,2,4,3,4,5,1 (consider frame size=4). Calculate total no. of page faults for FIFO, LRU and Optimal page replacement algorithms.**  
- **FIFO**: Total page faults = 14
- **LRU**: Total page faults = 12
- **Optimal**: Total page faults = 10

**Q.3 What is Scheduling and why it is required? Also describe the differences among short-term, medium-term and long-term scheduling with suitable example.**  
Scheduling is the process of selecting which processes should be executed by the CPU at any given time. It is required to ensure efficient utilization of CPU and to provide a fair and responsive system.

- **Short-term Scheduling**: Also known as CPU scheduling, it decides which process should be executed next by the CPU. Example: Round Robin scheduling.
- **Medium-term Scheduling**: Involves swapping processes in and out of memory. Example: Swapping out a process to free up memory.
- **Long-term Scheduling**: Determines which processes should be brought into the ready queue. Example: Job scheduling in batch systems.

**Q.4 What is Deadlock Avoidance? Example Banker's Algorithm with following snapshot of a system with resources A, B, C and D and processes PO to P4:**  
Deadlock avoidance is a technique used to ensure that the system never enters a deadlock state. The Banker's Algorithm is a resource allocation and deadlock avoidance algorithm that checks for safe states before allocating resources.

**(i) What are contents of Need Matrix?**  
Need = Max - Allocation

|       | A B C D     |
|-------|-------------|
| P₀    | 2 0 1 1     |
| P₁    | 0 6 5 0     |
| P₂    | 1 1 0 2     |
| P₃    | 1 0 2 0     |
| P₄    | 1 4 4 4     |

**(ii) Is the system in a safe state?**  
Yes, the system is in a safe state if there exists a sequence of process execution where each process can obtain its needed resources without leading to a deadlock.

**(iii) If a request from process P4 arrives for additional resources of (1, 2, 0, 0). Can request be granted immediately?**  
Yes, the request can be granted immediately if it does not lead to an unsafe state. The system will check if the available resources are sufficient to satisfy the request and if the resulting state is safe.

**Q.5 Explain the following with suitable diagrams-**
**(i) Android OS and its architecture**  
Android OS is a mobile operating system based on the Linux kernel. Its architecture consists of:
- **Linux Kernel**: Provides core system services like memory management, process management, and device drivers.
- **Libraries**: Includes a set of C/C++ libraries used by various components of the Android system.
- **Android Runtime**: Includes the Dalvik Virtual Machine (DVM) and core libraries.
- **Application Framework**: Provides high-level services to applications in the form of Java classes.
- **Applications**: The top layer where user applications reside.

**(ii) Resource Allocation graph**  
A Resource Allocation Graph (RAG) is a directed graph used to represent the state of a system in terms of processes and resources. Nodes represent processes and resources, and edges represent requests and allocations. A cycle in the graph indicates a potential deadlock.

**(iii) Various file access methods**  
- **Sequential Access**: Data is accessed in a linear sequence. Example: Tape drives.
- **Direct Access**: Data can be accessed directly using a block number. Example: Hard disks.
- **Indexed Access**: An index is used to locate data. Example: Databases.
- **Hashed Access**: A hash function is used to locate data. Example: Hash tables.



</details>






</details>

