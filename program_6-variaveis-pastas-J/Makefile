#Compiler and linker
COMPILER = gfortran
LINKER = gfortran
BASIC_OPTS = -cpp -fmax-errors=1 -ffree-line-length-0 -Wall
DEBUG_OPTS = $(BASIC_OPTS) -g -fbacktrace -O0 -fcheck=all
FAST_OPTS = $(BASIC_OPTS)
.PHONY: .FORCE

#Target directories.
OBJDIR = obj
SRCDIR = src
RUNDIR = run

OBJLIST = \
         $(OBJDIR)/main.o \
         $(OBJDIR)/mod.o

.DEFAULT_GOAL := $(RUNDIR)/main.elf

.PHONY: .FORCE

.FORCE:

$(OBJDIR)/mod.o: $(SRCDIR)/mod.f90
	$(COMPILER) $(DEBUG_OPTS) -c $< -J$(OBJDIR) -o $@

$(OBJDIR)/main.o: $(SRCDIR)/main.f90 $(OBJDIR)/mod.o
	$(COMPILER) $(DEBUG_OPTS)  -c $< -J$(OBJDIR) -o $@

$(RUNDIR)/main.elf: $(OBJLIST)
	$(LINKER) $^ -o $@

roda: $(RUNDIR)/main.elf .FORCE
	$(RUNDIR)/main.elf

clean: .FORCE
	rm -f $(RUNDIR)/*.elf
	rm -f $(OBJDIR)/*.o
	rm -f $(OBJDIR)/*.mod
