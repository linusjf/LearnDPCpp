SHELL := /usr/bin/env bash
HOSTNAME := $(shell hostname)
LOCALHOST = localhost
CXX = icc
CXXFLAGS = -O2 -g -std=c++17

EXE_NAME = OpenMPPi
SOURCES = OpenMPPi.cpp

all: 
	./submitqsub

.PHONY: all clean run build

build:
	$(CXX) $(CXXFLAGS) -qopenmp -o $(EXE_NAME) $(SOURCES)

run: 
	./$(EXE_NAME)

clean: 
	rm -f $(EXE_NAME) run*.sh.* build*.sh.*