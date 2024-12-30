# Hardware Challenges
## yoU ARe The detective
- There is a signal.sr file given in the description. The challenge name has few characters in upper case, from that we understand that it is related to UART protocol. I opened the file in PulseView to analayse the signal.
There was a single uptick in only D1 (digital pin 1). I zoomed the uptick to find that it had signal wave form. I used the UART decoder in the software. Set the Rx to D1, data bits to 8, data format to ascii. To find the baud rate,
measure the width in terms of time of a single pulse. Invert it to get the baud rate. It was 5333333 Hz. Then open the binary decoder output view to view the decoded data in asscii and hex. The flag was the decoded ascii output.

`Flag: nite{n0n_std_b4ud_r4t3s_ftw}`

![WhatsApp Image 2024-12-30 at 17 18 19_ec7ecf9e](https://github.com/user-attachments/assets/8946f555-7b12-48f2-8e0f-faa17000184e)

![WhatsApp Image 2024-12-30 at 17 18 21_63e42896](https://github.com/user-attachments/assets/41ab16e5-7bef-478e-a400-0cb3a9e2a2cd)

## Ancient Ahh Display 
- There are two files in the description. One is a .xlxs file and the other is a .txt file. From the description, It is understood that it is based on 7 segment display.
  The verilog code given in the .txt file was straight forward to understand that it has input - output combinations table, the columns in the .xlxs file that correspond to the input bits.
  Appending the input bits from across the given columns and matching them with the corresponding outputs gave the data in 7 bits to be displayed in the 7 segment display. Drawing all the
  display outputs based on the output column gives the flag.

  `Flag: nite{tr0UbLe_bUbbLe_L0L}`

  <img width="817" alt="image" src="https://github.com/user-attachments/assets/9b64a367-9413-49e1-9790-da94be443c59" />
  <img width="224" alt="image" src="https://github.com/user-attachments/assets/1da32704-14f8-4da0-9647-2cbf97fd8aed" />
  <img width="277" alt="image" src="https://github.com/user-attachments/assets/84fe3e3d-a2b4-4ef7-9b79-b16889b4bfab" />

  ![WhatsApp Image 2024-12-30 at 17 29 54_c19bd585](https://github.com/user-attachments/assets/ed8aff33-4dea-487c-8cf3-2585defe429f)

## Seek-Quence
- There is a scheme given in the description. From the description, it is understood that the circuit given in the scheme.pdf file is an electronic lock that needs to be opened. On looking upon the scheme, it is understood that the output at the bottom most end should be 0 to open the lock. We need to find the input combinations to be inputted to unlock the lock.
  <img width="360" alt="image" src="https://github.com/user-attachments/assets/c0221cf5-7677-4224-a0ba-d15cdd30b5c2" />

The final output is from an OR gate which will give 0 only when both the inputs are 0. The 2 comparators above give the input for the OR gate. The output P=R is active low (the output is 0 when P=R). So the bits entering the comparators need to be equal to that of the R bits that are predefined. Looking further above, there are two SIPO shift registers. The input for the RHS shift reg. is from the further above circuitry (output at U5A). The input for the LHS shift reg. comes from the Q7 output bit of the RHS shift reg. The datasheet tells that the registers shift the bits from Q0 to Q7. So, the 8 bit shift registers are used as 16 bit shift reg. of same operation over 16 clock pulses.

  <img width="203" alt="image" src="https://github.com/user-attachments/assets/64c99e7c-13d7-4ddf-9456-d09d90316f4d" />

The needed sequence of bits from U5A will be equal to that of the input needed by the comparators. That is `0001010000000101`.
The top most circuitry that has to deal with the inputs is mysterious here. For the inputs 0 or 1 both it gives 0 as output. But `0001010000000101` is the needed output from U5A (the output from the top most cicuit). If it gives only 0 for both 1 or 0 as input then , it has to be a sequence detector which gives 1 only when it detects an occurence of the sequence it is detecting.

<img width="620" alt="image" src="https://github.com/user-attachments/assets/2b7784da-2cae-4a58-9b50-05bf4710c1fd" />

From the needed output which starts with `0001....` it is understood that the 1st occurence is detected at 4th bit. Therefore it is a 4 bit sequence detector. Then, the needed output continues as `00010101...` we can see that the 2nd occurence is found just after 2 bits. This infers that overlapping is happening over 2 bits. Then the sequence it is detecting must be having 1st two bits and last two bits same `(i.e, 0000,0101,1010,1111)`. But then the problem with `0000, 1111` will be having too much overlapping and the output will not be as desired.
Only 2 sequences are left in the suspect list. Upon googling the circuit of each of those sequences with overlapping, the circuit given turns out that it detects the sequence `1010`. Now the part left is to find the input combination needed to detect 1010 and give `0001010000000101` as output from U5A. 

![WhatsApp Image 2024-12-30 at 18 02 52_67dc5d3d](https://github.com/user-attachments/assets/9da1f1c0-5f24-43f5-a5d5-23a7fec99be7)

The input combination to open the lock is 1010101011101010

`Flag: nite{1010101011101010}`



