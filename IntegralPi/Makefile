SHELL := /usr/bin/env bash
HOSTNAME := $(shell hostname)
LOCALHOST = localhost
INTEL_CXX = icpc
CXX = g++
CXXFLAGS = -O2 -g -std=c++17 -fopenmp
INTEL_CXXFLAGS = -O2 -g -std=c++17 -fiopenmp -fopenmp-targets=spir64 -fsycl

EXE_NAME = OpenMPPi
SOURCES = OpenMPPi.cpp

all: build
.PHONY: all clean run build

build:
ifeq ($(HOSTNAME),$(LOCALHOST))
	$(CXX) $(CXXFLAGS) -o $(EXE_NAME) $(SOURCES)
	termux-elf-cleaner $(EXE_NAME) > /dev/null
else
	$(INTEL_CXX) $(INTEL_CXXFLAGS) -o $(EXE_NAME) $(SOURCES)
endif

run: 
	./$(EXE_NAME)

clean: 
	rm -f $(EXE_NAME) run*.sh.* build*.sh.*
