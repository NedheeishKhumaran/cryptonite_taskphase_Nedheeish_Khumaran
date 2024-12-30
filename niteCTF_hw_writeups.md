# Hardware Challenges
## yoU ARe The detective
- There is a signal.sr file given in the description. The challenge name has few characters in upper case, from that we understand that it is related to UART protocol. I opened the file in PulseView to analayse the signal.
There was a single uptick in only D1 (digital pin 1). I zoomed the uptick to find that it had signal wave form. I used the UART decoder in the software. Set the Rx to D1, data bits to 8, data format to ascii. To find the baud rate,
measure the width in terms of time of a single pulse. Invert it to get the baud rate. It was 5333333 Hz. Then open the binary decoder output view to view the decoded data in asscii and hex. The flag was the decoded ascii output.

`Flag: nite{n0n_std_b4ud_r4t3s_ftw}`

