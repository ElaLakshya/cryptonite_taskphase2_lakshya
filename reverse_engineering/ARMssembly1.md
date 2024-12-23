# Journey through Assembly Language

We are required to learn some functions of assembly language. I can't learn the 
language or even learn to read it within a few days, so using some references I was able to go through 
the program.

List of commands is:

1. sub subtracts source 2 from 1
1. str stores value from first source to address provided
1. mov moves value from first to second
1. ldr loads value from first to second
1. lsl bitwise shift to left of first value by second value
1. sdiv division of first by second
1. add stores sum of first and third in first
1. stp Stores two registers into consecutive memory locations
1. ldp loads value into registers
1. ret 
1. bl calls the destination function
1. cmp compares 
1. bne not of bl
1. adrp loads page address 
1. nop no operation

w0 is the input to func. It's stored at [sp, 12].
Constants are initialized:

79 is stored in [𝑠𝑝,16]

7 is stored as [sp,20]

3 is stored as [sp,24]

->

7 is stored in w0

79 in w1, then bitshift to left is performed resulting in the result stored in stack 28.

After a series of actions, we are able to see that to print
"You win", the return value of function func is supposed to be 0.

therefore 3370-input is = 0. Therefore input=3370.

The input to the main function is a string, 
and it is converted to an integer using the atoi function.
Then decimal to hex=0D2A. Then lowercase, 0d2a, then to have 32 bits, 32/4 digits=8 digits,
therefore 00000d2a.

Flag is **picoCTF{00000d2a}**
