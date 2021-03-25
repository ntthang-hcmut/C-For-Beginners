# C Programming Language Standard

The idea of this article is to introduce C standard.

## What to do when a C program produces different results in two different compilers ?

For example, consider the following simple C program.

```c
void main() {}
```

The above program fails in gcc as the return type of main is void, but it compiles in Turbo C. How do we decide whether it is a legitimate C program or not?

Consider the following program as another example. It produces different results in different compilers.

```c
#include<stdio.h>
int main()
{
	int i = 1;
	printf("%d %d %d\n", ++i, i++, i);
	return 0;
}
```

```bash
2 1 3 - using g++ 4.2.1 on Linux.i686
1 2 3 - using SunStudio C++ 5.9 on Linux.i686
2 1 3 - using g++ 4.2.1 on SunOS.x86pc
1 2 3 - using SunStudio C++ 5.9 on SunOS.x86pc
1 2 3 - using g++ 4.2.1 on SunOS.sun4u
1 2 3 - using SunStudio C++ 5.9 on SunOS.sun4u
```

Which compiler is right?

The answer to all such questions is C standard. In all such cases we need to see what C standard says about such programs.

## What is C standard ?

The latest C standard is [ISO/IEC 9899:2011](https://en.wikipedia.org/wiki/C11_(C_standard_revision)), also known as [C11](https://en.wikipedia.org/wiki/C11_(C_standard_revision)) as the final draft was published in 2011. Before C11, there was [C99](https://en.wikipedia.org/wiki/C99). The C11 final draft is available [here](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n1570.pdf). See [this](https://en.wikipedia.org/wiki/C_(programming_language)#History) for complete history of C standards.

### Can we know behavior of all programs from C standard ?

C standard leaves some behavior of many C constructs as undefined and some as unspecified to simplify the specification and allow some flexibility in implementation. For example, in C the use of any automatic variable before it has been initialized yields undefined behavior and order of evaluations of subexpressions is unspecified. This specifically frees the compiler to do whatever is easiest or most efficient, should such a program be submitted.

## So what is the conclusion about above two examples ?

Let us consider the first example which is `“void main() {}”`, the standard says following about prototype of `main()`.

```c
// The function called at program startup is named main. The implementation 
// declares no prototype for this function. It shall be defined with a return 
type of int and with no parameters:
       int main(void) {}
// or with two parameters (referred to here as argc and argv, though any names 
// may be used, as they are local to the function in which they are declared):
       int main(int argc, char *argv[]) {}
// or equivalent;10 or in some other implementation-defined manner.
```

So the return type void doesn’t follow the standard and it’s something allowed by certain compilers.

Let us talk about second example. Note the following statement in C standard is listed under unspecified behavior.

```
The order in which the function designator, arguments, and 
subexpressions within the arguments are evaluated in a function 
call (6.5.2.2). 
```

### What to do with programs whose behavior is undefined or unspecified in standard ?

As a programmer, it is never a good idea to use programming constructs whose behaviour is undefined or unspecified, such programs should always be discouraged. The output of such programs may change with compiler and/or machine.