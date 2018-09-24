.DEFAULT_GOAL := main.elf

mod.o: mod.f90
	gfortran -c $< -o $@

main.o: main.f90 mod.o
	gfortran -c $< -o $@

main.elf: main.o mod.o
	gfortran $^ -o $@
