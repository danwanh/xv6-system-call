# xv6 system call lab

## Description

This lab is designed to understand how to add system calls to **xv6**, providing deeper insights into its internals. It is part of my *Operating Systems* course.

This lab extends the **xv6** operating system by adding two new system calls:

- **trace** system call: Enables tracking of system calls made by a process.  
- **sysinfo** system call: Provides information about free memory, active processes, and open files.

## How to Test
Compile and run xv6:
```sh
$ make qemu
```
## Testing the trace system call

Run the `trace` program to track system calls:
```sh
$ trace 32 grep hello README 

```
Output may be like this:
```
3: syscall read -> 1023 
3: syscall read -> 966 
3: syscall read -> 70 
3: syscall read -> 0 
```
or
```sh
$ trace 2147483647 grep hello README 

```
Output may be like this:
```
4: syscall trace -> 0 
4: syscall exec -> 3 
4: syscall open -> 3 
4: syscall read -> 1023 
4: syscall read -> 966 
4: syscall read -> 70 
4: syscall read -> 0 
4: syscall close -> 0 
```
or
```sh
$ trace 2 usertests forkforkfork 

```
Output may be like this:
```
usertests starting 
test forkforkfork: 407: syscall fork -> 408 
408: syscall fork -> 409 
409: syscall fork -> 410 
410: syscall fork -> 411 
409: syscall fork -> 412 
410: syscall fork -> 413 
409: syscall fork -> 414 
411: syscall fork -> 415 
... 
```
## Testing the sysinfo system call
Run the `sysinfotest` program to check system information:
```sh
$ sysinfotest
```
Output may be like this:
```
Free memory: 123456 bytes
Active processes: 5
Open files: 12
```

