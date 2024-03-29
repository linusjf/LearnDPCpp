SHELL := /usr/bin/env bash
HOSTNAME := $(shell hostname)
LOCALHOST = localhost
INTEL_CXX = mpiicpc
CXX = mpicc
CXXFLAGS = -O2 -g -std=c++17

EXE_NAME = HelloMPI
EXE2_NAME = HelloMPI2
SR_EXE_NAME = SendRecv
SOURCES = HelloMPI.cpp
SOURCES2 = HelloMPI2.cpp
SR_SOURCES = SendRecv.cpp

all: build
.PHONY: all clean run build

build:
ifeq ($(HOSTNAME),$(LOCALHOST))
	$(CXX) $(CXXFLAGS) -o $(EXE_NAME) $(SOURCES)
	termux-elf-cleaner $(EXE_NAME) > /dev/null
	$(CXX) $(CXXFLAGS) -o $(EXE2_NAME) $(SOURCES2)
	termux-elf-cleaner $(EXE2_NAME) > /dev/null
	$(CXX) $(CXXFLAGS) -o $(SR_EXE_NAME) $(SR_SOURCES)
	termux-elf-cleaner $(SR_EXE_NAME) > /dev/null
else
	$(INTEL_CXX) $(CXXFLAGS) -o $(EXE_NAME) $(SOURCES)
	$(INTEL_CXX) $(CXXFLAGS) -o $(EXE2_NAME) $(SOURCES2)
	$(INTEL_CXX) $(CXXFLAGS) -o $(SR_EXE_NAME) $(SR_SOURCES)
endif

run: 
ifeq ($(HOSTNAME),$(LOCALHOST))
	mpirun --allow-run-as-root --hostfile hosts -np 5 $(EXE_NAME)
	mpirun --allow-run-as-root --hostfile hosts -np 5 $(EXE2_NAME)
	mpirun --allow-run-as-root --hostfile hosts -np 2 $(SR_EXE_NAME)
else
	echo "Cannot execute run locally in ssh shell. Using qsub..."
	./submitqsub
endif

clean: 
	rm -f $(EXE_NAME) $(EXE2_NAME) $(SR_EXE_NAME) run.sh.* build.sh.*
