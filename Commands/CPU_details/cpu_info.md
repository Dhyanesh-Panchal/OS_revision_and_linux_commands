# Commands related to CPU details.

## `lscpu`
- This is used to display Detailed information of the CPU.
```sh
dhyanesh@dhyanesh-ThinkPad-T14s-Gen-1:~/Desktop/test_go$ lscpu
Architecture:                         x86_64
CPU op-mode(s):                       32-bit, 64-bit
Byte Order:                           Little Endian
Address sizes:                        39 bits physical, 48 bits virtual
CPU(s):                               8
On-line CPU(s) list:                  0-7
Thread(s) per core:                   2
Core(s) per socket:                   4
Socket(s):                            1
NUMA node(s):                         1
Vendor ID:                            GenuineIntel
CPU family:                           6
Model:                                142
Model name:                           Intel(R) Core(TM) i7-10610U CPU @ 1.80GHz
Stepping:                             12
CPU MHz:                              600.036
CPU max MHz:                          4900.0000
CPU min MHz:                          400.0000
BogoMIPS:                             4599.93
Virtualization:                       VT-x
L1d cache:                            128 KiB
L1i cache:                            128 KiB
L2 cache:                             1 MiB
L3 cache:                             8 MiB
NUMA node0 CPU(s):                    0-7
Vulnerability Gather data sampling:   Mitigation; Microcode
Vulnerability Itlb multihit:          KVM: Mitigation: VMX disabled
Vulnerability L1tf:                   Not affected
Vulnerability Mds:                    Not affected
Vulnerability Meltdown:               Not affected
Vulnerability Mmio stale data:        Mitigation; Clear CPU buffers; SMT vulnerable
Vulnerability Reg file data sampling: Not affected
Vulnerability Retbleed:               Mitigation; Enhanced IBRS
Vulnerability Spec rstack overflow:   Not affected
Vulnerability Spec store bypass:      Mitigation; Speculative Store Bypass disabled via prctl and seccomp
Vulnerability Spectre v1:             Mitigation; usercopy/swapgs barriers and __user pointer sanitization
Vulnerability Spectre v2:             Mitigation; Enhanced / Automatic IBRS; IBPB conditional; RSB filling; PBRSB-eIBRS SW sequence; BHI SW loop, KVM SW loop
Vulnerability Srbds:                  Mitigation; Microcode
Vulnerability Tsx async abort:        Mitigation; TSX disabled
Flags:                                fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall 
                                      nx pdpe1gb rdtscp lm constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf pni pclmulqdq d
                                      tes64 monitor ds_cpl vmx smx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes
                                       xsave avx f16c rdrand lahf_lm abm 3dnowprefetch cpuid_fault epb invpcid_single ssbd ibrs ibpb stibp ibrs_enhanced tpr_shadow vn
                                      mi flexpriority ept vpid ept_ad fsgsbase tsc_adjust sgx bmi1 avx2 smep bmi2 erms invpcid mpx rdseed adx smap clflushopt intel_pt
                                       xsaveopt xsavec xgetbv1 xsaves dtherm ida arat pln pts hwp hwp_notify hwp_act_window hwp_epp md_clear flush_l1d arch_capabiliti
                                      es
dhyanesh@dhyanesh-ThinkPad-T14s-Gen-1:~/Desktop/test_go$ 
```
- **NUMA-Node(s)**: NUMA (Non-Uniform Memory Access) is a computer memory design used in multiprocessing systems where memory access time depends on the memory location relative to the processor. So, NUMA node(s): 1 means there is only one memory node, so memory access is uniform across all CPUs (not NUMA in this case).
- **BogoMIPS**: BogoMIPS is a simple, crude measurement of CPU speed which is calculated during Linux Kernel Boot.
- **L1d cache**: Level 1 data cache. Stores data for quick access by the CPU. Size: 128 KiB.
- **L1i cache**: Level 1 instruction cache. Stores instructions for quick access by the CPU. Size: 128 KiB.
- **L2 cache**: Level 2 cache. Larger than L1 but slower. Stores both data and instructions. Size: 1 MiB.
- **L3 cache**: Level 3 cache. Shared among all CPU cores. Larger but slower than L2. Size: 8 MiB.

## `dmidecode -t processor` – Fetch CPU details from BIOS.

## `/proc/cpuinfo` containes Detailed CPU specifications aswell.. 