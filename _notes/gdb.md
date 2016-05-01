on target:
gdbserver HOST:1234 app v 4

if already running, find pid then start gdbserver:
gdbserver --attach HOST:1234 <pid>

to enable core dumps:
ulimit -c, 0 indicates disabled
ulimit -c unlimited

change location:
echo '/var/volatile/core_%e' > core_pattern

to generate core dump in UUT:
send SIGQUIT, Ctrl+\ on terminal or kill -3 <pid>
will have a file called core, to examine on PC:
arm-xilinx-linux-gnueabi-gdb app core
for cleaner startup in GDB (so does not complain about missing libraries):
arm-xilinx-linux-gnueabi-gdb -ex 'set sysroot microzed/petalinux/build/linux/rootfs/targetroot' -ex 'core-file core' app

arm-xilinx-linux-gnueabi-gdb app
(gdb) set sysroot microzed/petalinux/build/linux/rootfs/targetroot
(gdb) target remote 192.168.1.33:1234
(gdb) b main
(gdb) continue
(gdb) continue


info threads               list threads
thread apply all where     get backtraces of all threads
info signals               see signal behavior
handle SIGINT pass         pass sigint to the program
list                       view source


PROFILING:
add -pg as option in CFLAGS and LIBS to Makefile
On UUT, cleanly exit and will produce file called gmon.out
On PC, get gmon.out and execute to get a human-readable output:
arm-xilinx-linux-gnueabi-gprof app gmon.out > prof_output
