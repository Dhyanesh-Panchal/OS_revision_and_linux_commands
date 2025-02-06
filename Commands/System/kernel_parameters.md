# kernel parameters
- Kernel parameters are tunable values that you can adjust while the system is running.
- Note that for changes to take effect, you do not need to reboot the system or recompile the kernel.

## `sysctl` for kernel parameter changes.
- `sysctl -a` displays kernel parameters.
- `sysctl <TUNABLE_CLASS>.<PARAMETER>=<TARGET_VALUE>` for Temporary changes.
- `sysctl -w <TUNABLE_CLASS>.<PARAMETER>=<TARGET_VALUE> >> /etc/sysctl.conf` for permanent changes.

#### `/etc/sysctl.conf` is the config file for kernel parameters.
