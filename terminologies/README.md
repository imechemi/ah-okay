
### Volatile memory
The devices which can store data while it is powered. 



### Page cache

When a part of a memory is used for keeping data that are used frequently, that section is called page cache. When you read a data from disk, the first load is usually slow and the second read is much faster. This is due to page cache storing the data in the main memory as page cache. Similarly, while writing to disk, the data is first updated in cache thereby delaying the write to disk. But eventually within seconds, the data is updated on the disk.



### Dirty pages

Data on page cache which has to be written to disk. 


### Thread
What the hell is Thread? It is nothing but a set of register values which makes it a unit that can be independently executed on a CPU core. Universally, thread has stack pointer and instruction pointer. So during multithreading, threads save where they left before reliquishing the CPU. How nice is that :) 
