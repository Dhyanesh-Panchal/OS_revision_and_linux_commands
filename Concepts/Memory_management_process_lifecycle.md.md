# How OS Handles memory when process starts and terminates?

## Memory allocation when Process starts
1. The OS allocates a **PCB (Process Control Block)** in the kernel.

2. Each process gets its own **Virtual Address Space (VAS)**
    - When a process starts, the OS **does not allocate physical memory immediately** for the entire address space. Instead, it sets up virtual memory pages and maps them to physical frames dynamically using paging.
    - A page table is created for the process, mapping virtual pages to physical frames.
    - VAS is divided into Segments:
        1. **Code Segement**: Stores executable instructions *(read-only)*.
        2. **Data**: Stores global and static variables.
        3. **Stack**: Stores function call frames, local variables.
        4. **Heap**: Stores dynamically allocated memory.
    - The Layout of Virtual memory for particular process: `/proc/<PID>/maps` or `pmap <pid>`
3. The OS **maps virtual memory pages to physical memory** using a **page table**.
    - If there isn't enough RAM, OS uses swap space(on disk) as a temporary storage.
    - Memory regions (stack, heap) **may not be physically allocate yet**—they are **demand-paged**.
4. The **binary executable files are loaded** into Code segment. The OS sets the program’s entry point.
5. Allocating the Stack and Heap.
    - Stack overflow is prevented by placing a guard page.

#### Context Switching to the New Process
- CPU updates the process state in PCB.
- And then OS switches.

## Memory Deallocation
1. **Releasing Virtual Memory**: The OS removes all page table entries for the process.
2. **Freeing the Physical Frames**: The OS identifies physical frames assigned to the terminated process. These frames are, Returned to the free list (so they can be reassigned to other processes). Pages are marked as "clean" or "dirty" (dirty pages need to be written back to disk before reuse).
3. **Closing Open files and kernel objects**: The OS closes all open file descriptors.If the process had:
- Sockets → Closed.
- Pipes → Disconnected.
- Shared memory → Unlinked (if no other process is using it).
4. **Handling Child Processes (Orphans & Zombies)**: If the process has child processes, they are reparented to init (PID 1). The process becomes a zombie until the parent collects its exit status (`wait()`)
5. Then OS **removes the PCB from process table**.
