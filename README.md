# A Better Malloc
<br>

## Abstract:
### In this project, implementing a memory allocator for the heap of a user-level process.
### The basic idea of this project was to understand how a simple memory
### allocator works using basic system calls.
 <br> The implementation must pass through some basic guidelines:
1) When requesting memory from the OS, we must use mmap (rather than sbrk).
2) Although a real memory allocator requests more memory from the OS whenever it
can't satisfy a request from the user, our memory allocator must call mmap only one
time (when it is first initialized).
3) The choice for Data Structures is to maintain the free list and policy for choosing the
chunk of memory was upto us.
4) The memory allocator should be more flexible in how the user can specify what
memory should be freed.

# Program Description:-

1. ## mem.cpp:
    ### This contains all the function definitions.
    1. ### int Mem_Init(int userRequestedMemory):
        mmap() will be called one time with userRequestedMemory + Extra Memory (for Metadata)
        <br>For success: returns 0
        <br>For failure: returns -1  
    2. ### void *Mem_Alloc(int size):
        Used First Fit to find the big enough hole for allocation.
        <br>For Success: returns base address of allocated memory.
        <br>For Failure: returns NULL, if no block of memory found.
    3. ### int Mem_Free(void *ptr, bool PARTIAL/FULL):
        Deallocates block of memory pointed by the ptr, Flag(PARTIAL/FULL) indicates the parial or full deallocation of the block.
        <br>For Success: returns 0
        <br>For Failure: returns -1, if ptr is invalid.
    4. ### void *Mem_IsValid(void *ptr):
        <br>For Success: returns base address of block allocated.
        <br>For Failure: returns NULL, if it is invalid ptr.
    5. ### int Mem_GetSize(void *ptr):
        <br>For Success: returns size of block allocated.
        <br>For Failure: returns -1, if ptr is invalid.
    6. ### void display():
        Prints the Allocated Block Addresses, Free Block Addresses in output.txt
    7. ### void Mem_Clear():
        Frees all the Allocated Blocks and makes one free hole.
    8. ### void merge_left(metadata *ptr):
        Merges with a free hole found on the leftside of ptr.
    9. ### void merge_right(metadata *ptr):  
        Merges with a free hole found on the rightside of ptr.

2. ## main.cpp:
     This file is just for the debugging purpose and contains main function.
3. ## mem.h:
     Contains all the function declarations.
4. ## run.sh:
    To run the program. 