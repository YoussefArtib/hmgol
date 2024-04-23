# Handmade Game of life executable:

After watching [Handmade Linux x86 executables](https://www.youtube.com/playlist?list=PLZCIHSjpQ12woLj0sjsnqDH8yVuXwTy3p) by [David Smith](https://www.youtube.com/@davidsmith7791), I decided to write [Conway's game of life](https://en.wikipedia.org/wiki/Conway's_Game_of_Life) executable by hand.

The C and ASM code can be found in this [repo](https://github.com/YoussefArtib/GameOfLife).

# Why doing this ?
It is fun and exciting.

# Quick Start
```console
$ ./make.sh
$ ./gol64
```

# Things to change to make it better:
- For example:
    ```
        add DWORD [rbp - 4], 1          ; x++
        ADD r/m32, imm8     83 /0 ib        01 000 101
        83 45 FC 01
    ```
can be less bytes:
    ```
        inc DWORD [rbp - 4]
        INC r/m32           FF /0           01 000 101
        FF 45 FC
    ...
    ```
- Instead of using ```CALL rel32``` we can use ```CALL rel8``` or ```CALL rel16```
- Instead of ```mov rdi, 1```, we can ```xor rdi, rdi``` then ```inc rdi.```

# TODO:
    - [ ] Write the 32 bit version.
    - [ ] Optimize the byte code.
    - [ ] Create a .data section instead of putting the data in the program header.

# References:
- https://en.wikipedia.org/wiki/Executable_and_Linkable_Format
- https://www.felixcloutier.com/x86/
- https://wiki.osdev.org/X86-64_Instruction_Encoding
- http://www.c-jump.com/CIS77/CPU/x86/lecture.html
