
### Volatile memory
The devices that can store data only when it is powered. 



### Page cache

When a part of a memory is used for keeping data that are used frequently, that section is called page cache. When you read a data from disk, the first load is usually slow and the second read is much faster. This is due to page cache storing the data in the main memory as page cache. Similarly, while writing to disk, the data is first updated in cache thereby delaying the write to disk. But eventually within seconds, the data is updated on the disk.



### Dirty pages

Data on page cache which has to be written to disk. 


### Thread
What the hell is Thread? It is nothing but a set of register values which makes it a unit that can be independently executed on a CPU core. Universally, thread has stack pointer and instruction pointer. So during multithreading, threads save where they left before reliquishing the CPU. How nice is that :) 


### Reactive Programming
Reactive programming is a different style of programming, where you build composable components and do hold onto a execution waiting for a task to complete. Instead, you resume the task when it's complete. It is also confusing to associate this as synonym for asynchronous programming, but actually here abstractions are at much lower layer like operating systems allowing non-blocking calls, handling back-pressure and message passing etc. Yes, it is close to asynchronous, but here we are at the benefit of using the system resources much more efficiently such as multicore CPUs. This results in cost effective resource utilization due to this 
style of programming. 

Example: Think of it as cells in spreadsheets. When a cell A1 gets updated, then other cells depending on A1 also gets updated. 


### Bearer Token
It is a token issued by authorization server which can be used to access resources protected by that auth server.
