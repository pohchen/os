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
Add Tab in the beginning of line

```
make: execvp: tools/build.sh: Permission denied
make: *** [Image] Error 127
```
[osdi@localhost linux-0.11]$ chmod tools/build.sh 777

- Compiling works well to **Image**

[osdi@localhost linux-0.11]$ qemu -m 16M -boot a -fda Image -hda ../osdi.img

### 2.2

Hint: Use backtrace command to find the kernel bugs, there are 2 bugs in lab1 linux kernel.



Lab 2
=============


