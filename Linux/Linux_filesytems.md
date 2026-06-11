# Linux Notes: Filesystem & Kernel

Quick reference for essential Linux directories and core concepts.

## Essential Directories
* `/home` - Your user directory. Safe to create, modify, and delete files here without breaking the OS.
* `/etc` - System-wide configuration files. Always backup a file before editing it.
* `/var/log` - Logs. The first place to look for troubleshooting when a service or app crashes.

## The Kernel & Compiling
* **Kernel:** The core software layer bridging applications and physical hardware.
* **Compiling:** The process of translating human-readable source code into machine-readable binary (0s and 1s).
* **Custom Kernels:** Building a kernel from scratch lets you strip out generic drivers to optimize for specific hardware. Mostly done today for specialized systems or learning purposes.
