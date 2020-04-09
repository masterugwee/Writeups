## Challenge RedVelvet.              

Basic assesment of the file.

```bash
info RedVelvet 

RedVelvet: ELF 64-bit LSB executable, x86-64, version 1 (SYSV), dynamically linked, 
interpreter /lib64/ld-linux-x86-64.so.2, for GNU/Linux 2.6.32, BuildID[sha1]=84e7ef91c33878cf9eefc00a7a450895aa573494, not stripped

```
A linux binary. The next step is to disassemble it, here I used Ida pro. 

Opening up the binary in Ida shows that the binary is doing a string comparison there is an SHA256 function the has to be for hashing.
The input is handled by fgets the lenght is defined as 27, so the input should be 26 characters accounting for the last null character.

Opening up the functions reveals another info on how the input is being manipulated. Each function is a mathematical equation 
for cross-checking the inputs. This is where the z3 library in python comes in handy. We can create a model using z3, implement the conditions 
present in the functions to create a script that produces the desired input, which is the flag. Finally re-arranging the values in the order they were taken up in the functions would present us the flag.
