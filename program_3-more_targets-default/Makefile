.DEFAULT_GOAL := main.elf

mod.o: mod.f90
	gfortran -c mod.f90 -o mod.o

main.o: main.f90 mod.o
	gfortran -c main.f90 -o main.o

main.elf: main.o mod.o
	gfortran main.o mod.o -o main.elf
