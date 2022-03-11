>Incomplete
# how to learn C properly
this isn't one of those guides that tell you the "right" way to learn C.
it's about the tools that make learning, developing and understanding C code easier
## gcc
you already know what this is(except if you're on window, in which case, leave, now). but the compiler has a lot commandline arguments. i'll just give the useful ones.
### Better error reporting:
```
-Wall -Wextra -Werror -pedantic
```
this enables most compiler warnings and convert all of them into errors. this means your code will not compile if you have made any inaccuracy the compiler can detect. Even though this might sound overkill, it should be beneficial considering C is a [very weakly typed language][#1]
### Debugging
```
-ggdb
```
this is necessary for gdb to be able to help debug the code
### Optimizations
```
-O3
```
enables all optimizations supported by the compiler
### Finally
combining the power of all of the above we get
```
gcc -Wall -Wextra -Werror -pedantic -ggdb -O3 -o main main.c
```
where `main` can be replaced by the name of your C file in both the places. from now on, `main` will be used as the default filename in the rest of the text

## gdb
Now that you're using a big boy language, you need to learn to use an actual debugger. begone `printf("debug\n");`
after compiling your code, just run `gdb ./main` in the terminal to start it up. you will be greeted with a shell like interface
you can set breakpoints for functions like `break functionname`,
run `tui enable` for a nice interface,
run the program with just `r [argument1] [argument2]`,
if the running program reaches the function for which the breakpoint was set, the execution will stop and let you step through every step of the code(which is usually a line) using `n`. Conviniently in gcc, after you run a command, you can just press enter to repeat it

## linter
If possible, setup a linter for your editor of choice(its ed isn't it). I personally use cppcheck, and it works great for getting warnings for things without having to compile everytime

[#1](this just means that C allows conversion between its types very freely. for eg. between char and int, size_t and unsigned int)
