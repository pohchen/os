OSDI
=============

### Lab 1

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

- compiling works well to **Image**

### Lab 2
