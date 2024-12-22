# Starting GDB

GDB, as much as I researched, is a great debugger program, allowing the user to see all
developments in the program.

This challenge starts us off with basic gdb commands like adding breakpoints, running and 
disassembling programs and also reading registers.

It is given to us we need to read the eax function at the end of the main function.

So add a breakpoint at main, then read the registers

```
root@TurboMachine:~# gdb debugger0_a
GNU gdb (Ubuntu 15.0.50.20240403-0ubuntu1) 15.0.50.20240403-git
Copyright (C) 2024 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.
Type "show copying" and "show warranty" for details.
This GDB was configured as "x86_64-linux-gnu".
Type "show configuration" for configuration details.
For bug reporting instructions, please see:
<https://www.gnu.org/software/gdb/bugs/>.
Find the GDB manual and other documentation resources online at:
    <http://www.gnu.org/software/gdb/documentation/>.

For help, type "help".
Type "apropos word" to search for commands related to "word"...
Reading symbols from debugger0_a...

This GDB supports auto-downloading debuginfo from the following URLs:
  <https://debuginfod.ubuntu.com>
Enable debuginfod for this session? (y or [n]) y
Debuginfod has been enabled.
To make this setting permanent, add 'set debuginfod enabled on' to .gdbinit.
(No debugging symbols found in debugger0_a)
(gdb) break main
Breakpoint 1 at 0x1131
(gdb) run
Starting program: /root/debugger0_a
[Thread debugging using libthread_db enabled]
Using host libthread_db library "/lib/x86_64-linux-gnu/libthread_db.so.1".

Breakpoint 1, 0x0000555555555131 in main ()
(gdb) next
Single stepping until exit from function main,
which has no line number information.
Download failed: Invalid argument.  Continuing without source file ./csu/../sysdeps/nptl/libc_start_call_main.h.
__libc_start_call_main (main=main@entry=0x555555555129 <main>, argc=argc@entry=1,
    argv=argv@entry=0x7fffffffe158) at ../sysdeps/nptl/libc_start_call_main.h:74
warning: 74     ../sysdeps/nptl/libc_start_call_main.h: No such file or directory
(gdb) print $eax
$1 = 549698
```

the answer is 

**picoCTF{549698}**
