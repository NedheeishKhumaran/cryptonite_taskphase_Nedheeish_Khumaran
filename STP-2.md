# STP-2
## Reverse Engineering
## Vault Door Challenges:
### Vault Door training
-	Open the given `.java` file to see that the check condition for password has the password in string. Wrap it up with picoCTF{}.
Flag – picoCTF{w4rm1ng_Up_w1tH_jAv4_3808d338b46}
### Vault-door-1
-	The code now has password checking mechanism a little different. It has indexes and the respective character but in a jumbled fashion. Arranging them in proper order according to its index will give the password.
Flag – picoCTF{d35cr4mbl3_tH3_cH4r4cT3r5_75092e}
### Vault-door-3
-	The code has loops that scramble the entered password and checks across the reference. We need to alter the code such that, it takes the reference and scrambles it and prints the output. This output is the password. This works because the scrambling pattern is symmetric. (just the reverse order)
Flag – picoCTF{jU5t_a_s1mpl3_an4gr4m_4_u_1fb380}
### Vault-door-4
-	The code has bytes which were decimal , hexadecimal octal and direct characters. Now convert them to ascii and combine to get the flag.
Flag – picoCTF{jU5t_4_bUnCh_0f_bYt3s_f4a8cd8f7e}
### Vault-door-5
-	The code has byte wise url encoding and then the same is base64 encoded. The reference needed to be decoded base64 first and then url decode to get the password.
Flag- picoCTF{c0nv3rt1ng_fr0m_ba5e_64_e3152bf4} 
### Vault-door-6
-	The code’s checking mechanism is password  byte XORed with 0x55 and then checked if its equal to reference byte. So now XOR the reference bytes with 0x55 and then convert them to characters to get flag.
Flag – picoCTF{n0t_mUcH_h4rD3r_tH4n_x0r_3cE2919}
### Vault-door-7
-	The code takes the password and converts them into bytes. The password is 32 bytes. It iterates 8 times when handling 4 bytes each time. (4 bytes make 32 bit, int can hold 32 bit. 8 iteration needed to cover all the 32 bytes). Each of these are pushed left accordingly and bitwise ORed such that they are just joined. This gives a list of 32bit int values. To obtain the password, we can make a code to reverse this. Lets create a function that takes list of integers (our reference list of integers from source goes into this). This function iterates through every integer in the list one by one and creates 4 bytes per iteration. Each of the bytes will be shifting the number by the same exact amount as in the source but to the right instead of left. After that each byte is done bit wise and with 0xFF to make sure there is just last 8 bits considered. Now join the strings together and append it to the new list. 
Code: 
```
def int_array_to_hex_string(int_array):
    hex_chars = []
    
    for num in int_array:
        //Extract each byte from the 32-bit integer and convert it to a character
        byte1 = (num >> 24) & 0xFF
        byte2 = (num >> 16) & 0xFF
        byte3 = (num >> 8) & 0xFF
        byte4 = num & 0xFF
        
        //Append each byte as a character to the list
        hex_chars.extend([chr(byte1), chr(byte2), chr(byte3), chr(byte4)])
    
    //Join the list of characters to form the final hex string
    return ''.join(hex_chars)

// Example usage
int_array = [1096770097,1952395366,1600270708,1601398833,1716808014,1734291511,960049251,1681089078]
// Convert the int array back to the hex string
hex_string = int_array_to_hex_string(int_array)
print("Reconstructed hex string:", hex_string)

Flag: picoCTF{A_b1t_0f_b1t_sh1fTiNg_07990cd3b6}
### Vault-door-8
-	The code has a bit swapping algorithm for the password and checks it across the reference. It is a series of swapping. So we need to do the same but in reverse for the reference to get the password. I altered the code accordingly to get the password to print.
Code: 
// import java.util.*;
public class VaultDoor8Solver {
    public static void main(String[] args) {
        // Expected scrambled characters
        char[] expected = {
            0xF4, 0xC0, 0x97, 0xF0, 0x77, 0x97, 0xC0, 0xE4,
            0xF0, 0x77, 0xA4, 0xD0, 0xC5, 0x77, 0xF4, 0x86,
            0xD0, 0xA5, 0x45, 0x96, 0x27, 0xB5, 0x77, 0xE0,
            0x95, 0xF1, 0xE1, 0xE0, 0xA4, 0xC0, 0x94, 0xA4
        };
        
        // Unscramble each character
        char[] unscrambled = new char[expected.length];
        for (int i = 0; i < expected.length; i++) {
            unscrambled[i] = unscrambleBits(expected[i]);
        }
        
        // Convert to password string
        System.out.println("Password: " + new String(unscrambled));
    }
    
    public static char unscrambleBits(char c) {
        // Apply the inverse operations in reverse order
        c = switchBits(c, 6, 7);
        c = switchBits(c, 2, 5);
        c = switchBits(c, 3, 4);
        c = switchBits(c, 0, 1);
        c = switchBits(c, 4, 7);
        c = switchBits(c, 5, 6);
        c = switchBits(c, 0, 3);
        c = switchBits(c, 1, 2);
        return c;
    }
    
    public static char switchBits(char c, int p1, int p2) {
        // Same as original switchBits function
        char mask1 = (char)(1 << p1);
        char mask2 = (char)(1 << p2);
        char bit1 = (char)(c & mask1);
        char bit2 = (char)(c & mask2);
        char rest = (char)(c & ~(mask1 | mask2));
        char shift = (char)(p2 - p1);
        char result = (char)((bit1 << shift) | (bit2 >> shift) | rest);
        return result;
    }
}
```
Flag – picoCTF{s0m3_m0r3_b1t_sh1fTiNg_2e762b0ab}
## ARM challenges :
### ARMssembly 0
-	The file is in .S format. Now we need to execute this program with the arguments to get the code. As I don’t use x86 machine I need qemu-user-static to emulate it. Now convert the assembly file into object file of aarch64 (`$ aarch64-linux-gnu-as -o chall.o chall.S`). Then convert it into actual binary file (`$ aarch64-linux-gnu-gcc -static -o chall chall.o`).
Now run the file, `./chall  1765227561 1830628817` to get result. The flag has to be in hex format so convert the result to hex and wrap it up in picoCTF to get the flag.
Flag – picoCTF{6d1d2dd1}

### ARMssembly 1
-	`vi ./chall_1.S`. this will open the assembly code. 

### ARMssembly 2
-	Put the given argument when executing the file. Convert the result to hex.
Flag: picoCTF{9c174346}
### ARMseebly 3
-	Put the given argument when executing the file. Convert the result to hex.
Flag: picoCTF{00000039}


