# Little facts learned.
- > Linux uses **Completely Fair Schedular (CFS)** which aims to distribute CPU time fairly among all running processes by using a Red-Black tree data structure to manage them effectively. 

- > Does pages related to kernel process are being swapped? YES, they are, kernel has its own seperate Virtual address space and it manages its own memory mapping. Detailed refrence: [here](https://chatgpt.com/share/67a574e3-a608-8012-a718-48fe55632ef5)


- > A "`.so`" file in Linux stands for "shared object" and is a type of dynamically linked library, meaning it is a collection of code that can be loaded and used by multiple programs at runtime. It is analogous to windows DLL.
    - On Linux, archive libraries end with the `.a` extension, and shared object libraries end with the `.so` extension.
    - For more details: [here](./shared_objects.md)


- > The `/etc/fstab` file contains information about filesystems that are typically mounted at boot time.


- [Loadable Kernel Modules](https://docs.legato.io/latest/getStartedKO.html) (.ko files) are object files that are used to extend the kernel of the Linux Distribution.