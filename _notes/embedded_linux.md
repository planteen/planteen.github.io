Embedded Linux Notes
====================

These are tips for working on an embedded Linux system with BusyBox, perhaps
built by Yocto (e.g., not a full Linux distro on a workstation or server).

Kernel Debugging
----------------
Useful debugging information can be obtained by enabling the following kernel
menuconfig options:

Kernel hacking
  Magic SysRq key
  Debug Lockups and Hangs
    Detect Hard and Soft Lockups
    Detect Hung Tasks

  Stack backtrace support (get it in /proc)
  also need:
  Compile-time checks and compiler options
    
  also CONFIG_FRAME_POINTER, CONFIG_UNWIND_INFO, CONFIG_STACK_UNWIND

Magic SysRq
-----------
Once enabled, see available features:

echo ? > /proc/sysrq-trigger

SysRq : HELP : loglevel(0-9) reboot(b) crash(c) terminate-all-tasks(e) memory-full-oom-kill(f) kill-all-tasks(i) thaw-filesystems(j) sak(k) show-backtrace-all-active-cpus(l) show-memory-usage(m) nice-all-RT-tasks(n) poweroff(o) show-registers(p) show-all-timers(q) unraw(r) sync(s) show-task-states(t) unmount(u) show-blocked-tasks(w)

To send a break to a Linux target from a Linux host using picocom, press
Ctrl+A, Ctrl+\, then desired mode. Picocom will display `*** break sent ***`. For
example, Ctrl+A, Ctrl+\, c does the following:
    SysRq : Trigger a crash
    Unable to handle kernel NULL pointer dereference at virtual address 00000000
    pgd = 40004000
    [00000000] *pgd=00000000
    Internal error: Oops - BUG: 817 [#1] PREEMPT SMP ARM
    Modules linked in:

procfs
------
Lots of useful debugging information at multiple levels (system, process, and
thread) exists in /proc. CONFIG_STACKTRACE gives a stack file which is very
useful.

Interrupt monitoring
--------------------
To actively monitor interrupts with a refresh rate of 1 Hz:
watch -n 1 "cat /proc/interrupts"

Process priority
----------------
On BusyBox, there is not full version of ps and top does not exist. To print process priority:
awk '{print $18}' /proc/1337/stat

Userspace I/O
-------------
Userspace I/O (uio) is perfect for interfacing with custom peripherals like FPGA logic without worrying about the complexity and licensing issues of a kernel module. The performance is also higher, due to the fact that there is a direct mapping to memory and a system call is not needed to access the device.

You should not need to worry about manually issuing cache flush instructions. All uio pages are marked VM_IO. So simply open and mmap() the UIO device to access it from a userspace program.

You do need to worry about memory operations being re-ordered and use memory barriers to ensure correct ordering.
