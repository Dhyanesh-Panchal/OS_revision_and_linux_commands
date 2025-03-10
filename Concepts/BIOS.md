# BIOS (Basic Input Output System)
- BIOS comes included with computers, as firmware on a chip on the motherboard.
- When BIOS boots up a computer, it first determines whether all of the necessary attachments are in place and operational.
- Any piece of hardware containing files the computer needs to start is called a boot device.
- After testing and ensuring boot devices are functioning, BIOS loads the OS into the computer's random access memory (RAM) from a hard disk or diskette drive (the boot device).

## Booting Sequence:
1. **Power on**
2. **Power on Self test (POST)**: POST is a set of routine performed by firmware immediately after the boot.
    - POST sequence is executed irrespective of the Operating System and is handled by the system BIOS/UEFI. Once the tests are passed the POST would generally notify the OS with beeps while the number of beeps can vary from system to system.
    - The checks are performed majorly on:
        - Hardware elements like processor, storage devices and memory.
        - Basic System Devices like keyboard, and other peripheral devices.
        - CPU Registers
        - DMA (Direct Memory Access)
        - Timer
        - Interrupt controller
3. **Look for a Boot device**: The BIOS searches for bootable device based on the boot priority order. The first device with the valid **boot sector** is selected.
4. **Boot loader**: Loading the Bootloader. If the selected boot device has a valid boot sector:
    - BIOS loads the first sector (512 bytes) of the disk (MBR - Master Boot Record) into RAM.
    - BIOS passes control to the bootloader (located in the MBR or EFI partition).
    - The bootloader is responsible for loading the operating system.
    - Linux systems uses `GRUB` while macs uses `boot.efi`. 
5. **Kernel Load**: The Bootloader loads the OS kernel.

6. **Kernel executes `systemd`** and system service starts.

[Reference](https://youtu.be/XpFsMB6FoOs?si=bQVk4iPIz2Kyo3cW)
