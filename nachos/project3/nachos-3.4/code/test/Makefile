# use normal make for this Makefile
#
# Makefile for building user programs to run on top of Nachos
#
# Several things to be aware of:
#
#    Nachos assumes that the location of the program startup routine (the
# 	location the kernel jumps to when the program initially starts up)
#       is at location 0.  This means: start.o must be the first .o passed 
# 	to ld, in order for the routine "Start" to be loaded at location 0
#

# if you are cross-compiling, you need to point to the right executables
# and change the flags to ld and the build procedure for as

GCCDIR = ../../../gnu-decstation-ultrix/decstation-ultrix/2.95.3/

LDFLAGS = -T script -N
ASFLAGS = -mips2
CPPFLAGS = $(INCDIR)

# if you aren't cross-compiling:
# GCCDIR =
# LDFLAGS = -N -T 0
# ASFLAGS =
# CPPFLAGS = -P $(INCDIR)

PATH = $(GCCDIR):/lib:/usr/bin:/bin

CC = $(GCCDIR)gcc -B../../../gnu-decstation-ultrix/
AS = $(GCCDIR)as
LD = $(GCCDIR)ld

CPP = gcc -E
INCDIR =-I../userprog -I../threads
CFLAGS = -G 0 -c $(INCDIR)

all: halt shell matmult sort fork join exit yield exec execchild killAndExit OpenAndRead OpenAndWrite CreateAndWrite concurrentRead cp



start.o: start.s ../userprog/syscall.h
	$(CPP) $(CPPFLAGS) start.c > strt.s
	$(AS) $(ASFLAGS) -o start.o strt.s
	rm strt.s

halt.o: halt.c
	$(CC) $(CFLAGS) -c halt.c
halt: halt.o start.o
	$(LD) $(LDFLAGS) start.o halt.o -o halt.coff
	../bin/coff2noff halt.coff halt

shell.o: shell.c
	$(CC) $(CFLAGS) -c shell.c
shell: shell.o start.o
	$(LD) $(LDFLAGS) start.o shell.o -o shell.coff
	../bin/coff2noff shell.coff shell

sort.o: sort.c
	$(CC) $(CFLAGS) -c sort.c
sort: sort.o start.o
	$(LD) $(LDFLAGS) start.o sort.o -o sort.coff
	../bin/coff2noff sort.coff sort

matmult.o: matmult.c
	$(CC) $(CFLAGS) -c matmult.c
matmult: matmult.o start.o
	$(LD) $(LDFLAGS) start.o matmult.o -o matmult.coff
	../bin/coff2noff matmult.coff matmult

fork.o: fork.c
	$(CC) $(CFLAGS) -c fork.c
fork: fork.o start.o
	$(LD) $(LDFLAGS) start.o fork.o -o fork.coff
	../bin/coff2noff fork.coff fork

join.o: join.c
	$(CC) $(CFLAGS) -c join.c
join: join.o start.o
	$(LD) $(LDFLAGS) start.o join.o -o join.coff
	../bin/coff2noff join.coff join

exit.o: exit.c
	$(CC) $(CFLAGS) -c exit.c
exit: exit.o start.o
	$(LD) $(LDFLAGS) start.o exit.o -o exit.coff
	../bin/coff2noff exit.coff exit   
    
yield.o: yield.c
	$(CC) $(CFLAGS) -c yield.c
yield: yield.o start.o
	$(LD) $(LDFLAGS) start.o yield.o -o yield.coff
	../bin/coff2noff yield.coff yield

killAndExit.o: killAndExit.c
	$(CC) $(CFLAGS) -c killAndExit.c
killAndExit: killAndExit.o start.o
	$(LD) $(LDFLAGS) start.o killAndExit.o -o killAndExit.coff
	../bin/coff2noff killAndExit.coff killAndExit
   
exec.o: exec.c
	$(CC) $(CFLAGS) -c exec.c
exec: exec.o start.o
	$(LD) $(LDFLAGS) start.o exec.o -o exec.coff
	../bin/coff2noff exec.coff exec

execchild.o: execchild.c
	$(CC) $(CFLAGS) -c execchild.c
execchild: execchild.o start.o
	$(LD) $(LDFLAGS) start.o execchild.o -o execchild.coff
	../bin/coff2noff execchild.coff execchild

CreateAndWrite.o: CreateAndWrite.c
	$(CC) $(CFLAGS) -c CreateAndWrite.c
CreateAndWrite: CreateAndWrite.o start.o
	$(LD) $(LDFLAGS) start.o CreateAndWrite.o -o CreateAndWrite.coff
	../bin/coff2noff CreateAndWrite.coff CreateAndWrite
 
OpenAndWrite.o: OpenAndWrite.c
	$(CC) $(CFLAGS) -c OpenAndWrite.c
OpenAndWrite: OpenAndWrite.o start.o
	$(LD) $(LDFLAGS) start.o OpenAndWrite.o -o OpenAndWrite.coff
	../bin/coff2noff OpenAndWrite.coff OpenAndWrite
    
OpenAndRead.o: OpenAndRead.c
	$(CC) $(CFLAGS) -c OpenAndRead.c
OpenAndRead: OpenAndRead.o start.o
	$(LD) $(LDFLAGS) start.o OpenAndRead.o -o OpenAndRead.coff
	../bin/coff2noff OpenAndRead.coff OpenAndRead

concurrentRead.o: concurrentRead.c
	$(CC) $(CFLAGS) -c concurrentRead.c
concurrentRead: concurrentRead.o start.o
	$(LD) $(LDFLAGS) start.o concurrentRead.o -o concurrentRead.coff
	../bin/coff2noff concurrentRead.coff concurrentRead

cp.o: cp.c
	$(CC) $(CFLAGS) -c cp.c
cp: cp.o start.o
	$(LD) $(LDFLAGS) start.o cp.o -o cp.coff
	../bin/coff2noff cp.coff cp
