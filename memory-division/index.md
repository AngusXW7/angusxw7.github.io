# Memory Division

Memory Division!

<!--more-->

First of all, I would like to say that some materials will divide the memory partition into four zones, and some materials will divide it into five zones. I was learning about quad partitioning, and I would have been more inclined to accept quad partitioning, but after reviewing some of the materials I started to understand quad partitioning as well.

## 4 Parts

We need to know that the memory that a C++ compiled program needs to occupy is divided into the following parts, they are.

heap : this memory area is generally allocated by the program apes, that is, we take the initiative, and will be released by the active recycling at the end of the program, and the pointer operations we often perform are also done in this area.

Stack: This area is automatically allocated and released by the compiler, and generally holds function parameters, local variables, etc.

Global / static: global variables and static variables stored in the area, initialized global variables and static variables are in one area, uninitialized global variables and uninitialized static variables are in another adjacent area, this area is also automatically released by the system after the end of the program.

Code : this area is the paper meaning, that is, all our binary code is stored here.

## 5 Parts

For the five zones it is just one more constant storage area, namely:

heap, stack, Code, Global /Static

Constants: This area stores constants that are not allowed to be modified and are automatically released after the program is finished running.

So why this partitioning difference, because the global static storage area stores .bss and .data segments, while the constant storage area stores .data segments, so there is this partitioning difference.

Well, that's all for today!
