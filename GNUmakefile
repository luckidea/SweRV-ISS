OFLAGS := -O3
IFLAGS := -I/usr/local/include
LFLAGS := /usr/local/lib/libboost_program_options.a

COMP := $(CXX) -std=gnu++14 $(OFLAGS) $(IFLAGS)

%.o:  %.cpp
	$(COMP) -c -o $@ $^

OBJ := CsRegs.o Core.o sim.o Inst.o Memory.o

sim: $(OBJ)
	$(COMP) -o $@ $^ $(LFLAGS)

gen16codes: gen16codes.o CsRegs.o Core.o Inst.o Memory.o
	$(COMP) -o $@ $^ $(LFLAGS)

trace-compare: trace-compare.o
	$(COMP) -o $@ $^ $(LFLAGS)

adjust-spike-log: adjust-spike-log.o
	$(COMP) -o $@ $^ $(LFLAGS)

all: sim gen16codes trace-compare adjust-spike-log

RELEASE_DIR := /home/jrahmeh/bin

release: all
	cp sim $(RELEASE_DIR)/visper
	cp gen16codes trace-compare adjust-spike-log $(RELEASE_DIR)

clean:
	$(RM) sim gen16codes trace-compare $(OBJ) gen16codes.o \
	trace-compare.o

.PHONY: all clean release

