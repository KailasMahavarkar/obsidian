
### Program
A **program** is an executable file that contains processing **instructions**. They can be **application programs** or **system programs:**

- Application programs: word processors, games, Google Chrome, etc.
- System programs: compilers, file management programs, etc

### Process  & Threads
A process is an instance of a running program. For example, when we run VSCode, we are running an instance of it, and this instance represents a process. We can simultaneously launch multiple processes, such as opening CarWale in one instance and the Oxygen repo in another.

Similarly, within a single instance of VSCode, imagine editing as one task, displaying multiple files as another task, and generating IntelliSense as another task. These tasks share the same memory space but are managed by multiple threads.

![](https://i.imgur.com/JOuCHqn.png)


### Process states
A process may change state among the below ones. When a process is running it can get interrupted by a higher priority process so it goes back to **Ready** state again. Also, when the process is running it may need to wait for an **_Input/Output operation_** or an **_Event wait_**. In that case the process changes to **Waiting** state, and when the waiting state finished it goes back to **Ready**.

![](https://i.imgur.com/lanKDkF.png)


>Note: If you have a single threaded architecture &  multiple multiple process in execution, context switching happen with factor of time-slicing (A -> B -> A -> B .... until its over)


### Concurrency
Concurrency refers to the execution of multiple tasks or processes that overlap in time but may not necessarily be executed simultaneously

Concurrency is like juggling multiple tasks at the same time. You might not be doing them all at once, but you switch between them quickly enough that it seems like they're happening simultaneously (concurrency often involves using multiple threads).

##### Can concurrency can still be achieved with one process and one thread within that process?
Yes, concurrency can indeed be achieved with one process and one thread within that process. Although it's somewhat limited, it can be simulated through:
1. **Single Threaded Concurrency**: This involves rapidly switching between tasks, known as interleaving, where the processor switches between different tasks quickly enough to give the appearance of simultaneous execution.
2. **Asynchronous Programming**: Techniques such as callbacks, promises, or async/await in modern languages allow a single-threaded program to handle multiple tasks concurrently by efficiently managing tasks that are waiting for external resources without blocking the thread.

These methods enable a single-threaded program to appear responsive and handle multiple tasks effectively, although they may not achieve the same level of efficiency as using multiple threads or processes on multi-core systems.


---

### Difference between concurrency & parallelism ?

**Parallelism**: Imagine you have two chefs in a kitchen, each working on separate dishes at the same time. They're both chopping vegetables, stirring pots, and cooking on different burners simultaneously. They work independently, but their actions overlap in time, and you see progress on both dishes happening at once. This is parallelism—multiple things happening truly at the same time.

**Concurrency without Parallelism**: Now, picture a single chef in the kitchen. This chef has to cook two different dishes, but there's only one stove and one set of knives. To handle this, the chef works on one dish for a short while, then switches to the other dish. While it may seem like the dishes are progressing at the same time, the chef is actually switching back and forth quickly between tasks. This is concurrency without parallelism—tasks overlap in time, but they're not happening simultaneously; instead, they're interleaved or switched rapidly.

In essence, parallelism is like having multiple chefs cooking different dishes at the same time, whereas concurrency without parallelism is like one chef multitasking between different dishes, alternating their attention to keep progress moving forward on both tasks.


### advantages of concurrency & parallelism?

**Scenario 1:**
Task 1 (I/O bound operation)         -> assume I/O takes 2 sec to complete 
Task 2 (compute bound)                 -> takes 1 sec to complete
Task 3 (I/O bound operation)         -> takes 2 sec to complete

since these task are dependent on IO... don't you think executing them on context switching makes sense?

**Scenario 2:**
Task 1 (compute bound) ->  takes 2 sec to complete 
Task 2 (compute bound) ->  takes 1 sec to complete
Task 3 (compute bound)  -> takes 2 sec to complete

But when tasks are more dependent on compute (CPU compute) then executing them on context switching does not give us any edge... instead we can use parallelism here

### multi-task vs multi-processing?

Multi-tasking - Uses time-slicing to switch between tasks on a single CPU/core.
Multi-processing Uses multiple CPU cores or CPUs to run tasks truly in parallel.

Example:
Imagine you have a computer doing two things:

1. **Playing music**
2. **Rendering a video**

**With Multi-tasking**:
- The computer quickly switches between playing music and rendering video, handling small chunks of each task in rapid succession. (this isn't noticeable since context switching happens so fast)

**With Multi-processing**:

- One CPU core handles playing music while another core simultaneously handles rendering the video. Both tasks proceed independently and truly simultaneously.


Reference:
https://webcache.googleusercontent.com/search?q=cache:https://levelup.gitconnected.com/introduction-to-concurrency-and-parallelism-807a789f49c0&strip=0&vwsrc=1&referer=medium-parser

https://chatgpt.com/c/c56e0e67-d43e-49c5-9c0c-d9298ac3d0c5

-----
#parallelism #concurrency #multi-threading #multi-processing #threads #multi-processing #muti-tasking