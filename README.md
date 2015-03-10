Lab 1
=============

### 2.1
```
[osdi@localhost linux-0.11]$ vim Makefile
.c.s:
        @$(CC) $(CFLAGS) -S -o $*.s $<
.s.o:
        @$(AS)  -o $*.o $<
.c.o:
        @$(CC) $(CFLAGS) -c -o $*.o $<
```
Add **Tab** at the beginning of three linea

```
make: execvp: tools/build.sh: Permission denied
make: *** [Image] Error 127
```
[osdi@localhost linux-0.11]$ chmod tools/build.sh 777

- Compiling works well to **Image**

[osdi@localhost linux-0.11]$ qemu -m 16M -boot a -fda Image -hda ../osdi.img

### 2.2

Hint: Use backtrace command to find the kernel bugs, there are 2 bugs in lab1 linux kernel.

```
(gdb) c
Continuing.
Stopped due to shared library event
```

```
--- include/linux/sched.h	(revision 37)
+++ include/linux/sched.h	(working copy)
@@ -1,7 +1,7 @@
 #ifndef _SCHED_H
 #define _SCHED_H
 //hoho
-#define NR_TASKS 1//64
+#define NR_TASKS 64//64
 #define HZ 100
 
 #define FIRST_TASK task[0]
Index: init/main.c
```
```
--- init/main.c	(revision 37)
+++ init/main.c	(working copy)
@@ -137,7 +137,6 @@
 	hd_init();
 	floppy_init();
 	sti();
-	panic(""); //hahaha
 	move_to_user_mode();
 	if (!fork()) {		/* we count on this going ok */
 		init();
Index: Makefile
```
Debug using **QEMU** with **gdb** command in two different window (as follows)

[osdi@localhost linux-0.11]$ qemu -m 16M -boot a -fda Image -hda ../osdi.img -s -S -serial stdio

[osdi@localhost linux-0.11]$ gdb tools/system


Lab 2
=============


