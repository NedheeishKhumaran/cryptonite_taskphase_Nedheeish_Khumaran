# ASM Challenges
## asm1
-	At <+3>, the arg is being compared to 0x3a2. The arg (0x6fa) is greater so jump to <+37>. At <+37>, arg is compared to 0x6fa. It is equal to the ar. So mov arg into eax. Then subtract 0x12 from eax. The value at eax is the answer.
Flag: 0x6e8
## asm2
-	The program takes two arguments. These are stored in the stack. Now, it compares, the 1st arg with 0xfb46 and if its less then it enters a while loop where the second arg is added 1 and 1st arg is added 0x74. This loops until 2nd arg equals to 0xfb46. The flag is the value of 2nd arg at the end. We have to calculate how many times 0x74 can be added to 0x21 to reach the point its equal to 0xfb46. Then add it with 0x21.
Flag : 0x24c
## asm3
- The program takes 3 arguments. eax is XORed with itself to make it 0. The most significant byte (ebp+0x8 is the LSByte of arg 1 so ebp+0xb is the MSByte) from arg 1 is moved into ah. Then ax is shifted left 16 bits. This means ax becomes 0. Now al is being subtracted by the 2nd LSByte from arg 2 (ebp+c is LSByte of arg 2 then ebp+d is 2nd LSByte). That will be 0x00 - 0xe3 = 0x1d in al. The LSByte from arg2 (ebp+c) is moved into ah. ax becomes 0xdd1d. Then ax is XORed with 2 MSBytes from arg3 (ebp+0x10 has the LSByte of arg3 then WORD PTR ebp+0x12 denotes 2 bytes from MSByte). 0xbb86 ^ 0xdd1d = 0x669b.
Flag : 0x669b

## Bit-O-Asm-1
- The initial lines of code doesn't affect eax register. There is one line `mov eax, 0x30` and then just returning it. This means `eax` has 0x30 (48 in decimal).
  Flag : picoCTF(48)
## Bit-O-Asm-2
- The program has some lines of code where contents of registers edi, rsi are moved onto the stack. Also the DWORD `0x9fe1a` is moved onto the stack at `[rbp-0x4]`. Then the contents at `[rbp-0x4]` is moved into eax.
Therefore, `0x9fe1a` (654874 in decimal) is stored in eax.
Flag : picoCTF{654874}
## Bit-O-Asm-3
- The initial lines of code have moving contents of edi, rsi onto the local variables portion of the stack. Then DWORD `0x9fe1a` is moved onto the stack at `[rbp-0xc]` and DWORD `0x4` at `[rbp-0x8]`. The contents of `[rbp-0xc]` are moved into eax. Then eax is multiplied by the contents at `[rbp-0x8]`. Then eax is added with `0x1f5`. Contents of eax are moved into `[rbp-ox4]` and then again moved back to eax from that location. eax = 0x9fe1a * 0x4 + 0x1f5 = 2619997 in dec.
Flag : picoCTF{2619997}
## Bit-O-Asm-4
- Initial lines have unwanted actions. `0x9fe1a` is moved into `[rbp-0x4]`. Compares the content at `[rbp-0x4]` with 0x2710. Then there is a jump less than equal to condition which is false in this case. Moving on, subtract `0x65` from `[rbp-0x4]`. Then jump to instruction <main+41> which moves `[rbp-0x4]` into eax.
  eax = 0x9fe1a - 0x65 = 654773 in dec.
Flag : picoCTF{654773}
