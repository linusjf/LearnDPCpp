CXX = dpcpp
CXXFLAGS = -std=c++17  -Wall -Wformat-security -Werror=format-security

EXE_NAME = histogram
SOURCES = histogram.cpp

all: build
.PHONY: all clean run build

build:
	$(CXX) $(CXXFLAGS) -o $(EXE_NAME) $(SOURCES)

run: 
	./$(EXE_NAME)

clean: 
	rm -f $(EXE_NAME) run.sh.* build.sh.*
