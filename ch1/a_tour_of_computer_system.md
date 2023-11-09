## Infomation is bits and context

又回到了这章，熟悉的开始，这次挑战英文版

```c
#include<stdio.h>

int main() {
    printf("hello, world!\n");
    return 0;
}
```

The representation of hello.c illustrates a fundamental idea: All information in a system is represented as a bunch of bits;
![Alt text](image.png)
## Programs Are Translated by Other Programs into Different Forms

![Alt text](image-1.png)

the compilation system. 

![Alt text](image-2.png)

gcc compile the text file to object executable program by -o args;

The programs that perform the four phases:

### preprocessor phase 


Modified source program to .i text file, in this phase, preprocessor modify the original C program according to directives that begin with the 
'#' character; For example, the #include<stdio.h> command in line 1 of hello.c tells the preprocessor to read the contents of the system head file stdio.h and insert it dircetly 
into the program text.(only insert .h but not insert .cpp before linker ?)

### Compilation phase

The compiler translates the text file hello.i into the text file hello.s, whih contains an assembly-language program.
```s
main:
    subq $8, %rsp
    movl $.LC0, %edi
    call puts
    movl $0, %eax
    addq $8, %rsp
    ret
```

### Assembly phase

the assember translates hello.s into machine language instructions, packages them in a form known as relocatable object program, ans stores the result in the object file hello.o;(so,x86 machine language is closed? or riscv)

### linking phase

In Assembly phase , we get hello.o, but we import a c library, it 
repered a cpp file -printf.cpp.
so pre phase, we get 2 object 
programs.In linking phase, we will link printf.o into hello.o,
and get a executable that is ready to be loaded into memory and executed by the system.

## It Pays to Understand How Compilation Systems Work

There are some important reason why programmers need to understand how compilation systems work :
### Optimizing program performance

### Understanding link-time errors

### Avoiding security holes

### Processors Read and Interpret Instructions Stored in Memory

disk -> vfs -> fs -> shell -> user