# shell2
# 2019 - Created by Fred Nora and Luciano Gonçalez.
# todo: Covert this code to 64bit.

VERSION = 0
PATCHLEVEL = 0
SUBLEVEL = 0
EXTRAVERSION =
#NAME = shell2

# todo: Covert this code to 64bit.
CFLAGS = -m32 \
	--std=gnu89 \
	-nodefaultlibs \
	-nostdinc \
	-nostdlib \
	-static \
	-fgnu89-inline \
	-ffreestanding \
	-fno-builtin \
	-fno-pie \
	-no-pie \
	-fno-stack-protector \
	-s


LIBC    = ../alpha/libs/rtl/include/
LIBCOBJ = ../alpha/libs/rtl/obj

# Objects
myObjects = crt0.o \
main.o \
shellui.o \
ctype.o \
stdio.o \
stdlib.o \
string.o \
conio.o \
builtins.o \
desktop.o \
unistd.o \
stubs.o    


.PHONY: all all-c shell-link finalize clean

all: crt0.o main.o all-c shell-link finalize clean
	@echo "Ok?"

#head.o:
#	nasm  head.s  -felf -o head.o

#nao compilar, pegar compilado. tem que ajustar os argumentos recebidos por main.
crt0.o:
	gcc  -c  crt0.c  $(CFLAGS) -I $(LIBC) -I $(API) -o crt0.o
main.o:
	gcc  -c  main.c  $(CFLAGS) -I $(LIBC) -I $(API) -o main.o
all-c:
	gcc  -c  shellui.c   -I $(LIBC) -I $(API)  $(CFLAGS) -o shellui.o
	gcc  -c  builtins.c  -I $(LIBC) -I $(API)  $(CFLAGS) -o builtins.o
	gcc  -c  desktop.c   -I $(LIBC) -I $(API)  $(CFLAGS) -o desktop.o
	
#	gcc  -c  parser.c    -I ../../../lib/libc01/include/ -I ../../../lib/api01/include/ $(CFLAGS) -o parser.o
#	gcc  -c  lexer.c     -I ../../../lib/libc01/include/ -I ../../../lib/api01/include/ $(CFLAGS) -o lexer.o
#	gcc  -c  net.c       -I ../../../lib/libc01/include/ -I ../../../lib/api01/include/ $(CFLAGS) -o net.o
#	gcc  -c  terminal.c  -I ../../../lib/libc01/include/ -I ../../../lib/api01/include/ $(CFLAGS) -o terminal.o

	cp $(LIBCOBJ)/ctype.o   .
	cp $(LIBCOBJ)/stdio.o .
	cp $(LIBCOBJ)/stdlib.o .
	cp $(LIBCOBJ)/string.o .
	cp $(LIBCOBJ)/conio.o .
	cp $(LIBCOBJ)/wait.o .
	cp $(LIBCOBJ)/unistd.o .
	cp $(LIBCOBJ)/stubs.o .


shell-link:
#todo: Convert this code to 64bit.
	ld -m elf_i386 -T ../link.ld -o SHELL2.BIN $(myObjects)  
finalize:
#	cp SHELL2.BIN ../../bin
clean:
	-rm *.o
	-rm SHELL2.BIN 
	

