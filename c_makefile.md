# Creating Makefiles

### Example Makefile
```
// Anytime there is a change in main.o and message.o, recompile an executable called output
output: main.o message.o
    g++ main.o message.o -o output

// Don't create an executable, just make an object file
main.o: main.cpp
    g++ -c main.cpp

// Compile message.cpp and .h to a .o upon a detected change
message.o: message.cpp message.h
    g++ -c message.cpp

// use 'make clean' to remove unnecessary files
clean:
    rm *.0 output

/*
Example: 
target: dependencies
    action
*/
```
