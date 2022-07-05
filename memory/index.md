# Problems in memory

Some problems that you may have in memory!

<!--more-->

I believe that many people will encounter memory problems at one time or another when programming, such as the very common memory leaks and memory overflows, so today we will talk about the problems we may encounter in the memory mechanism.

## Memory overflow

A memory overflow is when a program does not have enough memory space for the program to use when it requests memory.

I believe that anyone who has written a program must have encountered this problem of memory leak. The most likely place for this problem to occur is when we call a recursive equation, but the recursive equation can't finish the calculation, or really the amount of data is too large causing the memory to be really insufficient. This time our program will report a memory overflow error.

## Memory Leak

A memory leak is when a program fails to free up the memory space that has been requested and takes up useful memory after it has requested it.

Memory leaks can also eventually lead to memory overflows.

### Different types of Memory leak 

1. Recurring memory leaks

    If the code that causes a memory leak is executed multiple times, then each execution of the program will result in a memory leak.

2. Episodic memory leaks

    A memory leak is caused only when the code causing the memory leak is executed under specific circumstances.

3. One-time memory leak

    The code that causes a memory leak is executed only once. This is mostly seen when the destructor does not release memory during the constructor.

4. Implicit leaks

    If the program keeps allocating memory while running and doesn't release memory until the end, which means we don't release memory in time leading to memory exhaustion.

## Memory out of bounds

It simply means that after requesting memory from the system, the actual memory used is more than the requested memory.

## Stack overflow

First of all, we know that the stack is a small automatically allocated buffer when the system is running, so when the amount of data is too large for the buffer to hold, it will cause the stack to overflow.

## Memory fragmentation
    
Anyone who knows a little bit about memory allocation should know that when we apply for a memory area or when the system automatically allocates memory areas, it is randomly looking for space to allocate instead of allocating areas consecutively, so this creates a problem that some areas are released after being used, but the adjacent areas are occupied by very small data. Later, we will have fewer contiguous areas to use and fewer contiguous storage areas to choose from, thus causing memory fragmentation.

These are the problems I know we will encounter in the memory mechanism, if you still until other problems, welcome to add!
