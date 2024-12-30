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

