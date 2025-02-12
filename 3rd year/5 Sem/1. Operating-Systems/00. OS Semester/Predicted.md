## **OPERATING SYSTEM – 2025 PREDICTED QUESTION PAPER**  
*(Based on analysis of past papers from 2013-2024)*  

---

### **PART A – Short Answer Questions (2 Marks Each)**
**(Answer in up to 25 words each. All questions are compulsory.)**  
1. Define an Operating System and its primary functions.  
2. What is a system call? Give an example.  
3. Explain the difference between a process and a thread.  
4. What is a race condition? Give one example.  
5. Define deadlock and list its necessary conditions.  
6. What is the difference between internal and external fragmentation?  
7. Explain the purpose of a Translation Lookaside Buffer (TLB).  
8. What is the advantage of multi-level paging over single-level paging?  
9. Define thrashing in virtual memory management.  
10. What are the different types of file allocation methods?  

---

### **PART B – Analytical and Problem-Solving Questions (8 Marks Each)**  
**(Attempt any four questions.)**  

11. **Process Scheduling:** Consider the following processes and compute the **average turnaround time and waiting time** using **Shortest Job First (SJF) and Round Robin (Quantum = 3ms) Scheduling.**  

   | Process | Arrival Time | Burst Time |  
   |---------|--------------|------------|  
   | P1      | 0            | 6          |  
   | P2      | 2            | 8          |  
   | P3      | 4            | 7          |  
   | P4      | 5            | 3          |  

12. **Memory Management:**  
   - Explain **paging and segmentation** with proper diagrams.  
   - Given a page reference string **1, 2, 3, 4, 2, 1, 5, 6, 2, 1, 2, 3, 7, 6, 3, 2, 1, 2, 3, 6**, calculate **page faults using FIFO and LRU page replacement algorithms** (Assume 4-page frames).  

13. **Deadlock Avoidance:** Explain **Banker’s Algorithm** with the following system snapshot. Determine whether the system is in a safe state.  

   | Process | Max (A B C) | Allocated (A B C) | Available (A B C) |  
   |---------|------------|------------------|----------------|  
   | P1      | 7 5 3      | 0 1 0            | 3 3 2          |  
   | P2      | 3 2 2      | 2 0 0            |                |  
   | P3      | 9 0 2      | 3 0 2            |                |  
   | P4      | 2 2 2      | 2 1 1            |                |  
   | P5      | 4 3 3      | 0 0 2            |                |  

14. **File Systems:**  
   - Compare **Contiguous, Linked, and Indexed file allocation** methods.  
   - Explain **journaling file systems** and their role in crash recovery.  

15. **Disk Scheduling:** A disk queue has requests at **82, 170, 43, 140, 24, 16, 190** (initial head position at **50**). Calculate total head movement using **FCFS, SSTF, and SCAN scheduling algorithms.**  

---

### **PART C – Descriptive and Design-Based Questions (15 Marks Each)**  
**(Attempt any two questions.)**  

16. **Virtual Memory and Performance:**  
   - What is **Belady’s Anomaly**? Which page replacement algorithm suffers from it?  
   - Consider a system with a memory-access time of **100 nanoseconds** and page fault service time of **8 milliseconds** (for an unmodified page) or **20 milliseconds** (for a modified page). Assuming **70% of replaced pages are modified**, compute the maximum acceptable **page fault rate** to keep the effective memory access time below **200 nanoseconds**.  

17. **Concurrency & Synchronization:**  
   - Explain **Readers-Writers problem** and implement a solution using **semaphores**.  
   - How does **Peterson’s Algorithm** solve mutual exclusion? Provide a code snippet.  

18. **Process Communication & Synchronization:**  
   - Explain the difference between **Inter-Process Communication (IPC) using Message Passing vs. Shared Memory.**  
   - What are the advantages of using **Monitors over Semaphores**? Illustrate with an example.  

---

### **BONUS HIGH-PROBABILITY QUESTIONS:**  
*(These may appear as alternative questions or internal choices.)*  
- Explain **Real-Time Operating Systems (RTOS)** with examples.  
- How do **Virtual Machines** work in Cloud Computing?  
- Compare **Android vs. iOS process scheduling**.  
- Discuss the advantages of **RAID-5 vs. RAID-1** for data storage.  
- How does **multi-threading improve CPU performance**?  

---
---
---
---
---

---
---
---
---
---



## **Predicted Future Exam Questions – Operating System**  
Based on the analysis of **2013 to 2024** Operating System question papers, I have identified key recurring topics and trends. Below are **possible future exam questions**, categorized by unit. These questions follow the same structure and difficulty level as past years' papers.  

---

## **UNIT I: Introduction to Operating Systems**  
### **Past Exam Topics Covered:**  
- Definition, functions, and objectives of OS  
- Types of OS (Batch, Multiprogramming, Real-time, etc.)  
- OS as a resource manager and virtual machine  
- Kernel and system calls  
- Process vs. Program  

### **Predicted Future Questions:**  
1. Explain the role of an **Operating System as a Control Program** and as a **Resource Manager** with relevant examples.  
2. Compare and contrast **Monolithic Kernel, Microkernel, and Hybrid Kernel architectures**.  
3. Discuss the role of the **Bootstrap Loader** during system startup. How does it differ from a Boot Manager?  
4. Explain the **difference between multitasking, multiprocessing, and multithreading** with examples.  
5. Describe the **System Call Life Cycle** with an example of a process making a system call.  
6. Explain how an **Interrupt Handling Mechanism** works in a modern OS.  
7. What are the **different scheduling levels in OS**? Discuss their importance with examples.  

---

## **UNIT II: Process Management & CPU Scheduling**  
### **Past Exam Topics Covered:**  
- Process states and scheduling  
- Context switching  
- Threads (User-level vs. Kernel-level)  
- CPU Scheduling Algorithms (FCFS, SJF, Round Robin, Priority Scheduling)  
- Process Synchronization (Semaphores, Mutex, Deadlock)  

### **Predicted Future Questions:**  
1. Explain the role of a **Process Control Block (PCB)** and its components with a detailed diagram.  
2. Consider the following set of processes and compute **average turnaround time and waiting time** using **SJF and Round Robin (Quantum = 3ms) Scheduling**.  
   
   | Process | Arrival Time | Burst Time |  
   |---------|--------------|------------|  
   | P1      | 0            | 6          |  
   | P2      | 2            | 8          |  
   | P3      | 3            | 7          |  
   | P4      | 5            | 3          |  
   
3. **Compare and contrast Preemptive and Non-Preemptive scheduling** with real-world examples.  
4. Discuss the **differences between cooperative and competitive multithreading**.  
5. **Explain Banker’s Algorithm** with an example and determine whether a given state is safe or unsafe.  
6. Explain the **Readers-Writers Problem** and give two different solutions for it using semaphores.  
7. How do **Spinlocks and Mutexes** work in achieving process synchronization? Compare their efficiency.  

---

## **UNIT III: Memory Management**  
### **Past Exam Topics Covered:**  
- Paging and Segmentation  
- Virtual Memory and Demand Paging  
- Page Replacement Algorithms (FIFO, LRU, Optimal)  
- Thrashing  
- Fragmentation  

### **Predicted Future Questions:**  
1. Given a page reference string **1, 2, 3, 4, 2, 1, 5, 6, 2, 1, 2, 3, 7, 6, 3, 2, 1, 2, 3, 6**, calculate the **number of page faults using LRU and FIFO page replacement algorithms**. Assume **four-page frames**.  
2. Discuss **Belady’s Anomaly** and explain why FIFO suffers from it.  
3. Explain **inverted page tables** and compare them with **multi-level page tables**.  
4. Differentiate between **Global and Local page replacement policies**. Which is more efficient?  
5. Explain the **concept of Working Set Model** in virtual memory management.  
6. What is **Copy-on-Write (COW)**? How does it optimize memory usage in modern operating systems?  
7. Explain **how TLB (Translation Lookaside Buffer) speeds up address translation** in paging.  

---

## **UNIT IV: File & Disk Management**  
### **Past Exam Topics Covered:**  
- File System Concepts and Directory Structures  
- Disk Scheduling Algorithms (FCFS, SSTF, SCAN, C-SCAN, LOOK)  
- File Allocation Methods (Contiguous, Linked, Indexed)  
- RAID Levels  

### **Predicted Future Questions:**  
1. Explain the **Indexed Allocation File System** with an example and compare it with **Linked Allocation**.  
2. Given the disk queue: **95, 180, 34, 119, 11, 123, 62, 64**, and initial position at **50**, calculate total **head movement using FCFS, SSTF, and C-SCAN disk scheduling**.  
3. Explain **how memory-mapped files improve file system performance**.  
4. Discuss the **trade-offs between Journaling File Systems and Non-Journaling File Systems**.  
5. Compare **i-nodes and File Allocation Tables (FAT)** in file system implementation.  
6. What is **Disk Caching**? How does it improve file system performance?  
7. Explain the **working of RAID-5** and discuss how parity bits are used in error correction.  

---

## **UNIT V: Advanced OS Concepts**  
### **Past Exam Topics Covered:**  
- Distributed Operating Systems  
- Mobile OS (Android, iOS, RTOS)  
- Security and Protection in OS  
- Cloud Computing and Virtualization  

### **Predicted Future Questions:**  
1. Explain the **differences between Monolithic, Microkernel, and Hybrid OS architectures**.  
2. How does **Android’s Zygote Process** improve app launch time?  
3. Discuss the **role of Virtual Machines in Cloud Computing**.  
4. Explain the **features of Real-Time Operating Systems (RTOS)** and their applications.  
5. How does **Role-Based Access Control (RBAC)** improve security in multi-user OS?  
6. Compare the **process scheduling in Linux and Windows operating systems**.  
7. Discuss the **challenges of process synchronization in a distributed OS**.  

---

## **Bonus: High-Probability Numerical & Scenario-Based Questions**  
1. **Calculate turnaround time and waiting time** for a given set of processes using various scheduling algorithms.  
2. **Apply Banker's Algorithm** to check if a system is in a safe state.  
3. **Simulate page replacement algorithms** using a given reference string.  
4. **Determine total head movement in disk scheduling algorithms** like SCAN, SSTF, and C-SCAN.  
5. **Analyze a given deadlock scenario** and determine if it can be avoided.  

---

[GO](https://chatgpt.com/share/67acbf83-32b8-8012-93d6-35aa35904d68)
 
