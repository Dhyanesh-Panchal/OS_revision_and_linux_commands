# `demidecode`
- The dmidecode command in Linux is used to retrieve hardware information from the system's DMI (Desktop Management Interface) table. It provides details about the BIOS, processor, memory, cache, and other system components.
- since dmidecode accesses lower level system-info, it requires superuser privileges.
Syntax: `sudo dmidecode [options]`

| Option | Description |
|--------|-------------|
| `-t TYPE` | Retrieve specific hardware information (e.g., bios, system, processor, memory, etc.). |
| `-s STRING` | Get specific information by keyword (e.g., bios-version, system-serial-number). |
| `-u` | Show raw, uninterpreted output. |
| `-q` | Display less verbose output. |
| `-V` | Show dmidecode version. |
| `-h` | Display help information. |