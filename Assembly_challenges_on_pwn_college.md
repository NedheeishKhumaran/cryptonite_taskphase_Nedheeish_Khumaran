# Assembly challenges on pwn.college 
## Set Register 
-	Create a file with .asm extension. Enter the file and write code for setting a register with a number given. `mov rdi, 0x1337` . Then convert this file to elf format by, `nasm -f elf64 register.asm -o register.o`  and `ld register.o -o register`. Now execute `/challenge/run /home/hacker/register`  to set the register to 0x1337 and get the flag.

Flag : `pwn.college{09W1eYB1a3e3P9jCAiCkzJw8rtN.0FN5EDL5QzM1czW}`
## Set-multiple-registers 
-	Create an asm file with code, 
`mov rax,0x1337
mov r12,0xCAFED00D1337BEEF
mov rsp,0x31337`. Then convert it to binary file like the previous challenge using nasm.
Execute `/challenge/run reg2` to set multiple registers to given values and get the flag.

Flag: pwn.college{UIRT1nAktZ21t0Grkj5K1oy_JoD.dBTM4MDL5QzM1czW}
## Add to register 
-	Create an asm file with code, `add rdi,0x331337` and then convert it to binary using nasm. Then execute `/challenge/run addreg` to add the given number to the register rdi and get the flag.

Flag: pwn.college{IjVf3Hv2mwhUzPlT2OiEhp4xDYO.0VN5EDL5QzM1czW}
##  Linear equation register
-	Create an asm file with code 
`mov rax, rsi
imul rax, rdi
add rax, rdx`. Convert it to a binary file using nasm and then execute `/challenge/run leqr` to get the linear equation and the flag.

Flag: pwn.college{UXwVMrV2IIACu7RgaxcY97TcDva.0lN5EDL5QzM1czW}
## Division on register
-	Create an asm file with code
`mov rax, rdi
  Div rsi`. Convert the asm file to binary and execute `/challenge/run div` to divide rdi by rsi and store the result in rax and get the flag.

Flag: pwn.college{ENqTR8GCl3u200fHpQWGi4L1kV5.01N5EDL5QzM1czW}



## Modulo operation 
-	Create an asm file with code
`mov rax,rdi
Div rsi
Mov rax, rdx` and convert to binary file. Execute `/challenge/run mod` to store the remainder of the division rdi by rsi and get the flag.

Flag: pwn.college{4RqUPS_RNZGbwmyyuIzdrEbJnGq.0FO5EDL5QzM1czW}
## Set upper byte
-	Create an asm file with code
`mov ah, 0x42` and convert it to binary file. Execute `/challenge/run ub` to set the upper bits of ax to 0x42 and get the flag.

Flag: pwn.college{U6q3zNjabpYnFL7sLG0lw8A05Ix.dFTM4MDL5QzM1czW}
## Efficient Modulo
-	Create an asm file with code
`mov al, dil
Mov bx, si` to move the last 8 bits of rdi to last 8 bits of rax and move last 16 bits of rsi to last 16 bits of rbx. Convert to binary and execute `/challenge/run em` to get the flag.

Flag: pwn.college{w_XcztJjx1hv0U1b5ztYXNXSb4j.0VO5EDL5QzM1czW}
## Byte Extraction
-	Create an asm file with code
‘shl rdi, 24
Shr rdi, 56
Mov rax, dil’. 
To extract the 5th byte from least significant side, we move the whole value to the left until the 5th byte, there are 3 bytes to the left of the 5th byte so we move 3*8 bits to the left. Then we have 7 bytes to the right of the desired byte. So shift right 7*8 bits to get the desired byte to the lowest 8 bits. Then move the last 8 bits of rdi to the last 8 bits of rax. This will yield the flag.

Flag: pwn.college{Uohag7Z9_Ul3QfFvXQniNtgOR9B.0FMwIDL5QzM1czW}
## Bitwise and
-	Create an asm file with code
`xor rax,rax
Or rax,rsi
And rax, rdi`.
To perform AND operation for rdi and rsi without using mov, we have to set the value of rsi to rax first. For that we can use OR operation but, for this method to work we need to ensure that the rax is 0. So initially XOR rax with rax to make it 0. Then OR it with rsi to get rax value equal to that of rsi. Then and rax with rdi to get the result in rax.
Flag: pwn.college{gW-kfTpNgDSJR5sJIsiIMdGtBVM.0VMwIDL5QzM1czW}
## Check even
-	Create an asm file with code
`and rdi, 1
Xor rax, rax
Or rax, 1
Xor rax, rdi`. To check even or odd in binary number we just need to see the LSB. If it is 0 then even else odd. To extract the LSB, we AND rdi with 1 to make rdi equal to the LSB (other bits except LSB become 0 and LSB is retained). Then make rax equal to 0 by XOR rax with rax. Then OR rax with 1 to make rax equal to 1.  Now we have rax equal to 1 and rdi containing LSB. If rdi equal to 0 (even), result becomes 1 due to XOR with rax (=1). If rdi equal to 1 (odd), result becomes 0.

Flag: pwn.college{MA3W2wS_gQeJedeY2o8xnNNj38s.0lMwIDL5QzM1czW}
##  memory read
-	`mov rax, [0x404000]` to move the contents at the address 0x404000 to rax. Execute `/challenge/run <file name>` to get the flag.

Flag: pwn.college{cwdxPZUKSM6T3bS8scMuWj5BRMG.dJTM4MDL5QzM1czW}
## Memory write
-	`mov [0x404000], rax` to move the contents of rax to address 0x404000. Execute `/challenge/run <file name>` to get the flag.

Flag: pwn.college{UPASfNBP8bg8uUG6M04ZoqX7QFL.dNTM4MDL5QzM1czW}
## memory increment
-	`mov rax, [0x404000]
Add qword [0x40400], 0x1337`. This will move the original value at the address to rax and then increment the value at the address by 0x1337. Qword is used to denote that it is a 64 bit operation. 

Flag: pwn.college{Q3GCyCt15vifrBRI3s5SFKMYR4q.01MwIDL5QzM1czW}
## Byte access 
-	`mov al, [0x404000]`. This will move the LS Byte from the address and set LS Byte of rax.
Flag: pwn.college{kE2jA0AGsqfZ6Pq4m5CAXMM7LTf.dRTM4MDL5QzM1czW}
## Memory Size access
-	` mov al, [0x404000]
mov bx,[0x404000]
mov ecx, [0x404000]
mov rdx, [0x404000]`. This will move a byte, a word, a double word and a quad word to these registers from the address respectively. 

Flag: pwn.college{EuD641S6J_90YVfWZVzimOycoPs.0FNwIDL5QzM1czW}
## Little Endian Write
-	` mov rax, 0xdeadbeef00001337
mov rbx, 0xc0ffee0000
mov [rdi], rax
mov [rsi], rbx`. To handle bigger constants we need to set them to registers first and then set to dereferenced register. 

Flag: pwn.college{w43gWJVcgxyEc0mpL4vFTOL3O5L.0VNwIDL5QzM1czW}
## Memory sum
-	` mov rax, [rdi+0]
mov rbx, [rdi+8]
add qword rbx, rax
mov [rsi], rbx`. This will put the first qword of the address to rax and the other to rbx. Then rbx+rax is stored in rbx. Now rbx’s value is set to the address at rsi.

Flag: pwn.college{M98kIZs2vS2O6Y4MbVNBfZw2l7c.0lNwIDL5QzM1czW}
## Stack subtraction
-	`pop rax
Sub qword rax, rdi
Push rax`. This code will pop the top element and set it in rax. Then subtract rdi from rax and then push contents of rax to the stack. 

Flag: pwn.college{cKah2XLqKmn00rTH7ubnLlu0qOV.01NwIDL5QzM1czW}
## Stack swap values
-	`push rdi
Push rsi
Pop rdi
Pop rsi`. First we push the contents of rdi to the stack then push contents of rsi on top of the rdi’s contents in the stack. So rsi becomes the top. When popping we pop it alternatively to swap. As rsi value is in top, pop it to rdi and then pop rdi’s value to rsi.

Flag: pwn.college{UryqjbmVs-HbFOD7DXNx81N1QyO.0FOwIDL5QzM1czW}
## Stack average
-	` mov rax, [rsp+0x0]
mov rbx, [rsp+0x8]
mov rsi, [rsp+16]
mov rdi, [rsp+24]
add qword rax, rbx
add qword rax,rsi
add qword rax, rdi
shr rax, 2
push rax`. 
Here we pop values from the stack and store them in registers. Then add all of them and store in rax. Rax is now divided by 4 for averaging the values. This is done by shifting it to the right by 2 times. Then push the average value to the stack.

Flag: pwn.college{oUNB-rgbBlHIaR1AygB58WHDFf0.0VOwIDL5QzM1czW}
## Absolute jump
-	`mov rsi, 0x403000
Jmp rsi`. This will make the rip jump to the address at rsi.

Flag: pwn.college{0OnqxpUFQxYCT3jk-n2KfyyzDr-.dVTM4MDL5QzM1czW}
## Relative jump
-	`_start:
     Jmp short jump_target
    Times 0x51 nop
Jump_target:
    Mov rax, 0x1`. 
This code will jump 0x51 bytes using `nop` and `times`. In the target label, move 0x1 into rax.

Flag: pwn.college{IT2Ce6NjeaTKSPayp-8MM4kl5SC.dZTM4MDL5QzM1czW}
## Jump trampoline
-	‘_start:
     Jmp short trmp
    Times 0x51 nop
Trmp:
    Pop rdi
    Mov rsi, 0x403000
    Jmp rsi’.
This code will initially jump 0x51 bytes and under its label it pops the stack and stores in rdi, also jumps to the absolute address 0x403000.

Flag: pwn.college{I3re20c3_PimH1a2vZMDLK_je3W.0FMxIDL5QzM1czW}
## Conditional Jump
-	`mov rax, 0               
-	cmp dword [rdi], 0x7f454c46   
-	jne ie                      
-	add eax, [rdi+4]            
-	add eax, [rdi+8]            
-	add eax, [rdi+12]           
-	jmp done                   
-	ie:
-	cmp dword [rdi], 0x00005A4D   
-	jne e                         
-	add eax, [rdi+4]            
-	sub eax, [rdi+8]            
-	sub eax, [rdi+12]           
jmp done           
-	e:
-	mov eax, 1                  
-	imul eax, [rdi+4]   
-	imul eax, [rdi+8]   
-	imul eax, [rdi+12] 
done:`. 
Rax is set to 0, cmp is used to compare the given number with the number at the address in rdi.  If its not equal, it’ll jump to `ie`. Otherwise, the addition steps will occur. Then it jumps to `done` for the code to end. Under `ie`,  when the first comparison fails It directs it to the else if (`ie`). Here is another comparison with the given number and the number at the address in rdi. If its not equal, then jumps to `e` (else). Otherwise, performs the addition and subtraction steps given.  Then jumps to done. Under `e`, it will directly do the multiplication steps as given. `done` label has no operation and thus is empty. This whole code works as if, else-if and else conditions.

Flag: pwn.college{00hviXJslmeRNgyLva7xEIAkGJQ.0VMxIDL5QzM1czW}
## Indirect Jump
`cmp rdi, 4
jl otw
jmp [rsi+4*0x8]
jmp done
otw:
jmp [rsi+(rdi*0x8)]
done:`

Here we need to execute switch condition based on what number it is in rdi. Instead of comparison in each case, there is a jump table with base address given. Cases have numbers 0,1,2,3 and default. Any number greater than 3 will go to default case (No negative numbers in this case). Compare rdi with 4 and jump to `otw` if the number is less than 4. If not, then jump to default case at rsi + 4 bytes. Under `otw`, jump to rsi + rdi-th byte as the cases are arranged according to the number(rdi)  with base address, in the given jump table.

Flag: pwn.college{8cOaGHVlq8lav4iXVHQLDO5qM10.0lMxIDL5QzM1czW}
## Average loop
-`mov rax,0
mov rbx, 0
cmp rbx, rsi
jl loop
loop:
add rax, [rdi+(rbx*8)]
add rbx, 1
cmp rbx, rsi
jl loop
jmp done
done:
div rsi`
 
the result of the average should be stored in rax. So initially set rax to 0. Then et rbx to 0 to use it as the counter for number of loops. Compare rbx and rsi, if rbx is less than rsi then enter the loop. Add the qword at that iteration of the loop to the rax. Rdi is the base address and the rbx*8 (8 bytes, 1 qword) depends on the iteration. Then increment rbx with 1 for next iteration and compare rbx and rsi to decide to loop again or exit to calculate the avg by dividing rsi to the rax. Now rax has the average.

Flag: pwn.college{Y6QyEQ_xXlj188pHFeZIbHSWS0b.01MxIDL5QzM1czW}

## Count non zero
-	`mov rax, 0
cmp rdi, 0
je done
wloop:
cmp byte [rdi],0
je done
add rax, 1
add rdi, 1
jmp wloop
done:`

rax is set to 0 intially as it is the counter of non zero bytes. Compare rdi with 0 and if its is equal then jump to done to end program with rax being 0. Then under `wloop`, compare the byte at the address of rdi with 0 and if its equal jump to done so that the program ends. Else, add 1 to rax, and add one to rdi. Then jump to `wloop` for next iteration.

Flag: pwn.college{0_XAZFUTZCHDFIFy5I1qB89ACnE.0FNxIDL5QzM1czW}

