# Memory Align

A very important point in memory management, memory align!

<!--more-->

## What is memory align

First we know that each data has a different size, maybe 1,2,4,8 byte, and each data element is put into memory one by one in the order they are defined. Most of the time data is read in units of 4. So to increase the speed of data reading and to make the different sizes of data less impact on the speed of data reading, we start using memory alignment and can define the alignment factor with #pragma pack(n).

Starting from the first address of the structure storage, when each element is placed into memory, they all think that the memory is divided according to their size, so the element placement must start on an integer multiple of their width, this is called memory alignment.

### Examples

```
struct
{
    int x;
    char y;
}
```
When I ask you how big the struct is, someone may say 5 bytes without thinking, but in fact he took up 8 bytes; this time it will ask, int accounted for 4 bytes char accounted for 1 byte, 4 + 1 = 5 ah, why would it be 8, this is the memory align caused by the.

## Why memory align then?

1. Platform reasons: not all hardware platforms can access any data at any address, so for better compatibility, we have to use memory align.
2. Performance reasons: when the processor accesses unaligned memory at its own access length, the processor needs to access the memory twice, while it only needs to access it once if it is aligned.

## Rules of memory align

1. n for basic type alignment is the value obtained by sizeof.
2. Data members are aligned by the smaller of their own size and #pragma pack(n).
3. Structure or union alignment rules are in accordance with the length of the largest data member and the smaller of #pragma pack(n).

// The general default is n=4;

