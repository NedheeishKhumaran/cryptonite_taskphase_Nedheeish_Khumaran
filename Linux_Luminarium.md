Welcome file
Welcome file


# Linux Luminarium:

## Hello Hacker:

### Intro to commands:

invoked the hello command to get the flag

### Intro to arguments :

Invoked hello command with hackers as argument to get the flag

## Pondering Paths:

### The root :

invoke the program pwn with absolute address /pwn to get the flag

### Program and Absolute path :

access run program using absolute addressing (`/challenge/run`) to get the flag.

### Position Thy self –

Use cd to navigate to / and then access /challenge/run to get the flag

### Position elsewhere –

Use cd to navigate to /sys/kernel and access /challenge/run to get the flag.

### Position Yet elsewhere –

Use cd to navigate to /proc/67 and access /challenge/run to get the flag.

### Implicit Relative path from / -

Use cd to navigate to / and then relative addressing (challenge/run) to get the flag.

### Explicit Relative path from /-

Use cd to navigate to / and then access run by ./challenge/run to get the flag.

### Implicit Relative path –

use cd to navigate to / and then use cd to go to challenge and then use ./run to get the flag.

### Home sweet Home –

invoke /challenge/run with argument using absolute addressing in the home directory and make sure argument is only 3 chars long (/challenge/run ~/h) to get the flag

## Comprehending Commands:

### Cat : not the pet, the command –

Use cat to read the file flag to get the flag

### Catting absolute paths –

use cat to read flag file using its absolute address /flag as an argument to the cat command to get the flag.

### More catting practise –

use cat to read flag file which is in a different directory. Put its absolute address as an argument for cat.

### Grepping for a needle in a haystack –

use grep to search for pwn.college(all the flags start like this) and use the absolute address as an argument.

### Listing files –

use cd to navigate to /challenge and use ls to list out all the files in it. There we find the name of the renamed run. Accessing from there directly wouldn`t unlock the flag. So go back to home and /challenge/<the renamed one> , this will get the flag

### Touching flags –

use cd to reach /tmp and touch a file pwn and another file college. Then go back to home and then execute /challenge/run to get the flag

### Removing files –

use ls to see what is the to be deleted file and then use rm command with the file name as argument then execute /challenge/check to get the flag

### Hidden files –

use cd to navigate to / and then use ls -a to see the .<file> then use cat command to execute that file to get the flag.

### An epic filesystem quest –

follow clues across different directories to find the flag. Sometimes straightforward due to use of cd. A few times its mandatory not to use cd. In those cases I used ls with relative addressing to reach the corresponding directory to see the name of the clue file. Then use cat <that relative path>/<clue file name>.

### Making directories – use cd to navigate to / .

Then using mkdir create /tmp/pwn. cd into the newly created directory and invoke touch pwn to create an empty file pwn. Now execute /challenge/run to get the flag

### Finding files –

invoke find using arguments / and -name flag (find / -name flag) to search the whole filesystem for files named flag. The list of addresses of all the files named flag is printed. Try to open those with no error displayed in the list. One of those files said permission denied when I tried to open it using absolute addressing. That rose suspicion because the find`s list didn`t show any error. So I went to that particular directory and opened the file `flag` using cat and got the flag.

### Linking files –

Given that the flag is actually in /flag. But /challenge/run access the flag from somewhere else. Now soft link the other address to the actual address to fool /challenge/run.  ln -s /flag ~/not-the-flag.  Then access /challenge/run to get the flag.

## Digesting Documentation

### Learning from documentation –

the program that contains the flag is given and the argument is also given use the argument while invoking the program to get the flag.

Flag: pwn.college{I6j3qedNjOlFYa_kOb10hWO1RMx.dRjM5QDL5QzM1czW}

### Learning Complex usage –

The documentation says that the argument --printfile prints the contents of a file on the terminal. So we need to invoke program /challenge/challenge with argument -- printfile and giving the /flag file as an argument for –printfile will read the contents of the /flag while.

Flag : pwn.college{wlgKjSL9lqioIKEAABA1cSeI7F0.dVjM5QDL5QzM1czW}

### Reading manuals –

using man command read the manual for challenge. The name is /challenge/challenge. The arguments for getting flag is --wxjcso 731.  Invoking /challenge/challenge –wxjcso 731 gives the flag.

Flag : pwn.college{UwJZxSjcXXQFLRs73LoY1Of9FYU.dRTM4QDL5QzM1czW}

### Searching Manuals –

open the manual for challenge. Use / to search for flag. Then use n for the next occurrence. The second occurrence gives the right argument for the flag. Use that to get the flag. /challenge/challenge --mj

Flag: pwn.college{ckhaT8mRjMfpEzReghRflZDhapq.dVTM4QDL5QzM1czW

### Searching for manuals –

open man man to see the manual of the man command. From there use man -k /challenge/challenge to get the man page name of /challenge/challenge. Use that as a command and put /challenge/challenge as argument to get the manual. In there the argument to be used with /challenge/challenge is given. Execute that and get the flag.

Flag : pwn.college{UIhqqAjUWO43KNnJtYdnTkosdtg.dZTM4QDL5QzM1czW}

### Helpful program –

use the –help argument for /challenge/challenge to get its manual. Then use argument -p with /challenge/challenge to get the secret value. Then use argument -g with the secret value to get the flag

Flag: pwn.college{kA9LA6eVg0S95xQ95GXal3ZAxmd.ddjM4QDL5QzM1czW}

### Help for builtins –

use help command with challenge as argument to get the manual. Now use the right argument -g with its secret value for challenge command to get the flag.

Flag : pwn.college{AQbufWouIB_ZmKjrUhk_9Sb1lnf.dRTM5QDL5QzM1czW}

## File GLobbing:

### Matching with * -

use cd command with argument as /ch* (only 4 chars max. allowed in argument) to enter /challenge directory. Now execute /challenge/run to get the flag.

Flag  : pwn.college{8weFs-cIISZMWf9tCHJUIAnfZtA.dFjM4QDL5QzM1czW}

### Matching with ? –

use cd with argument /?cha??enge to get to /challenge directory. From there eexecute /challenge/run to get the flag.

Flag: pwn.college{ku4cRaLRVnwuw75m7KBGfJYBeSG.dJjM4QDL5QzM1czW}

### Matching with [] –

use cd with /challenge/files as arguments to reach the directory. Now execute /challenge/run with file_[absh] as arguments to get the flag.

Flag: pwn.college{UCnBFD0dcnemQEjadSxfkBzUEiP.dNjM4QDL5QzM1czW}

### Matching paths with [] –

Execute /challenge/run with /challenge/files/file_[bash] as argument to get  the flag.

Flag: pwn.college{IEG3rCu8l92dYsvix8pD6kAolLs.dRjM4QDL5QzM1czW}

### Exclusionary Globbing –

use cd to go to /challenge/files. Execute /challenge/run with [!pwn]* to avoid files that start with any of these. This will yield the flag.

Flag : pwn.college{oEV0RhKwslx9h1NDbChbyarIpqg.dZjM4QDL5QzM1czW}

### Mixing Globs –

Use cd to go to /challenge/files. Execute /challenge/run with potential arguments related to `challenge, educational,pwning`. And the arguments should be less than 6 chars. When trying to use an argument and its wrong, it displayed other files that have same thing in common. Tried using `i` and `n` as common letters but it turned out to be the common ones for too many even in different combinations. Use ls to see all the files. Only challenge,educational and pwning started with letters c , e, and p respectively. So use argument [cpe]* to get the flag.

Flag: pwn.college{IeXU4Lp80HhN13Gf3JCzYXlZONL.dVjM4QDL5QzM1czW}

## Practising Piping :

### Redirecting output –

use `echo` command to print `PWN` and redirect its output to `COLLEGE` with `>` to get the flag.

Flag: pwn.college{ET8Akyhr8jT8ho3xv2kRLSIdAN1.dRjN1QDL5QzM1czW}

### Redirecting more output –

execute `/challenge/run` while redirecting the output to `myflag` using `>`. This will send the flag to `myflag` file. `cat` the myflag file to get the flag.

Flag : pwn.college{gNpbzOYAt1LsFneF2rljk1mTKXe.dVjN1QDL5QzM1czW}

### Appending output –

execute `/challenge/run` while redirecting the output in append mode (`>>`) to `/home/hacker/the-flag`. This will add the second part of the flag to the first part  of the flag that already existed in the `the-flag` file. `cat` the file to get the flag.

Flag: pwn.college{gYmOU1tYJAdWEhT37GvPACwGgIz.ddDM5QDL5QzM1czW}

### Redirecting errors –

execute `/challenge/run` and redirect the output (`>`) to `myflag` and redirect the error(`2>`) to `instructions`. Now `cat myflag` to get the flag.

Flag : pwn.college{kKCFuBP1R4niNCJ0pwRpyFZZiBY.ddjN1QDL5QzM1czW}

### Redirecting Input –

execute `echo` with `COLLEGE` as argument and redirect output (`>`) to `PWN` file. Now execute `/challenge/run` with input redirection (`<`) from `PWN`. This will yield the flag.

Flag : pwn.college{QLyxVc39s25rVBHoDsZLDYczWtw.dBzN1QDL5QzM1czW}

### Grepping Stored results –

execute `/challenge/run` while redirecting its output (`>`) to `/tmp/data.txt`. Now `grep` for `pwn.college` from `/tmp/data.txt`.

Flag : pwn.college{I3JoWU0WCRcPUFh1v-F8mj_h6g9.dhTM4QDL5QzM1czW}

### Grepping live output –

execute `/challenge/run` while piping (`|`) it to `grep` for `pwn.college{`.

Flag : pwn.college{YkbmZLW7TeaBsKsSniACeybOUe2.dlTM4QDL5QzM1czW}

### Grepping errors –

execute `/challenge/run` while redirecting error to output (`2>&1`) then pipe it (`|`) and `grep` for `pwn.college{` to get the flag.

Flag: pwn.college{cyf9yog8P2T8wqaxBHfwLjUyvsY.dVDM5QDL5QzM1czW}

### Duplicating piped data with tee –

execute `/challenge/pwn | tee hiii | /challenge/college` now the file `hiii` has the message regarding proper usage of `/challenge/pwn` with right argument.

Open the `hiii` file to get that data. Now execute `/challenge/pwn --secret szl6bQVw | tee hiii | /challenge/college` (based on the instructions). This yields the flag.

Flag: pwn.college{szl6bQVw5mabz22Zx9zjbYEGzJF.dFjM5QDL5QzM1czW}

### Writing to multiple programs –

execute `/challenge/hack | tee >(/challenge/the) >(/challenge/planet)`. This will give output of `/challenge/hack` to `/challenge/the` and to `/challenge/planet`.

Flag : pwn.college{UVdkj_B4HnRyNLLoNJW9DDDDcAX.dBDO0UDL5QzM1czW}

### Writing to multiple programs –

execute `/challenge/hack | 2>(/challenge/the) | >(/challenge/planet)` to send the stderr to `/challenge/the` and the stdout to `/challenge/planet`.

Flag : pwn.college{Mxg5Hyyj2HRvgYzIQpxPSoDHHdf.dFDNwYDL5QzM1czW}
Linux Luminarium:
Hello Hacker:
Intro to commands:
invoked the hello command to get the flag

Intro to arguments :
Invoked hello command with hackers as argument to get the flag

Pondering Paths:
The root :
invoke the program pwn with absolute address /pwn to get the flag

Program and Absolute path :
access run program using absolute addressing (/challenge/run) to get the flag.

Position Thy self –
Use cd to navigate to / and then access /challenge/run to get the flag

Position elsewhere –
Use cd to navigate to /sys/kernel and access /challenge/run to get the flag.

Position Yet elsewhere –
Use cd to navigate to /proc/67 and access /challenge/run to get the flag.

Implicit Relative path from / -
Use cd to navigate to / and then relative addressing (challenge/run) to get the flag.

Explicit Relative path from /-
Use cd to navigate to / and then access run by ./challenge/run to get the flag.

Implicit Relative path –
use cd to navigate to / and then use cd to go to challenge and then use ./run to get the flag.

Home sweet Home –
invoke /challenge/run with argument using absolute addressing in the home directory and make sure argument is only 3 chars long (/challenge/run ~/h) to get the flag

Comprehending Commands:
Cat : not the pet, the command –
Use cat to read the file flag to get the flag

Catting absolute paths –
use cat to read flag file using its absolute address /flag as an argument to the cat command to get the flag.

More catting practise –
use cat to read flag file which is in a different directory. Put its absolute address as an argument for cat.

Grepping for a needle in a haystack –
use grep to search for pwn.college(all the flags start like this) and use the absolute address as an argument.

Listing files –
use cd to navigate to /challenge and use ls to list out all the files in it. There we find the name of the renamed run. Accessing from there directly wouldn`t unlock the flag. So go back to home and /challenge/ , this will get the flag

Touching flags –
use cd to reach /tmp and touch a file pwn and another file college. Then go back to home and then execute /challenge/run to get the flag

Removing files –
use ls to see what is the to be deleted file and then use rm command with the file name as argument then execute /challenge/check to get the flag

Hidden files –
use cd to navigate to / and then use ls -a to see the . then use cat command to execute that file to get the flag.

An epic filesystem quest –
follow clues across different directories to find the flag. Sometimes straightforward due to use of cd. A few times its mandatory not to use cd. In those cases I used ls with relative addressing to reach the corresponding directory to see the name of the clue file. Then use cat /.

Making directories – use cd to navigate to / .
Then using mkdir create /tmp/pwn. cd into the newly created directory and invoke touch pwn to create an empty file pwn. Now execute /challenge/run to get the flag

Finding files –
invoke find using arguments / and -name flag (find / -name flag) to search the whole filesystem for files named flag. The list of addresses of all the files named flag is printed. Try to open those with no error displayed in the list. One of those files said permission denied when I tried to open it using absolute addressing. That rose suspicion because the finds list didnt show any error. So I went to that particular directory and opened the file flag using cat and got the flag.

Linking files –
Given that the flag is actually in /flag. But /challenge/run access the flag from somewhere else. Now soft link the other address to the actual address to fool /challenge/run. ln -s /flag ~/not-the-flag. Then access /challenge/run to get the flag.

Digesting Documentation
Learning from documentation –
the program that contains the flag is given and the argument is also given use the argument while invoking the program to get the flag.

Flag: pwn.college{I6j3qedNjOlFYa_kOb10hWO1RMx.dRjM5QDL5QzM1czW}

Learning Complex usage –
The documentation says that the argument --printfile prints the contents of a file on the terminal. So we need to invoke program /challenge/challenge with argument – printfile and giving the /flag file as an argument for –printfile will read the contents of the /flag while.

Flag : pwn.college{wlgKjSL9lqioIKEAABA1cSeI7F0.dVjM5QDL5QzM1czW}

Reading manuals –
using man command read the manual for challenge. The name is /challenge/challenge. The arguments for getting flag is --wxjcso 731. Invoking /challenge/challenge –wxjcso 731 gives the flag.

Flag : pwn.college{UwJZxSjcXXQFLRs73LoY1Of9FYU.dRTM4QDL5QzM1czW}

Searching Manuals –
open the manual for challenge. Use / to search for flag. Then use n for the next occurrence. The second occurrence gives the right argument for the flag. Use that to get the flag. /challenge/challenge --mj

Flag: pwn.college{ckhaT8mRjMfpEzReghRflZDhapq.dVTM4QDL5QzM1czW

Searching for manuals –
open man man to see the manual of the man command. From there use man -k /challenge/challenge to get the man page name of /challenge/challenge. Use that as a command and put /challenge/challenge as argument to get the manual. In there the argument to be used with /challenge/challenge is given. Execute that and get the flag.

Flag : pwn.college{UIhqqAjUWO43KNnJtYdnTkosdtg.dZTM4QDL5QzM1czW}

Helpful program –
use the –help argument for /challenge/challenge to get its manual. Then use argument -p with /challenge/challenge to get the secret value. Then use argument -g with the secret value to get the flag

Flag: pwn.college{kA9LA6eVg0S95xQ95GXal3ZAxmd.ddjM4QDL5QzM1czW}

Help for builtins –
use help command with challenge as argument to get the manual. Now use the right argument -g with its secret value for challenge command to get the flag.

Flag : pwn.college{AQbufWouIB_ZmKjrUhk_9Sb1lnf.dRTM5QDL5QzM1czW}

File GLobbing:
Matching with * -
use cd command with argument as /ch* (only 4 chars max. allowed in argument) to enter /challenge directory. Now execute /challenge/run to get the flag.

Flag : pwn.college{8weFs-cIISZMWf9tCHJUIAnfZtA.dFjM4QDL5QzM1czW}

Matching with ? –
use cd with argument /?cha??enge to get to /challenge directory. From there eexecute /challenge/run to get the flag.

Flag: pwn.college{ku4cRaLRVnwuw75m7KBGfJYBeSG.dJjM4QDL5QzM1czW}

Matching with [] –
use cd with /challenge/files as arguments to reach the directory. Now execute /challenge/run with file_[absh] as arguments to get the flag.

Flag: pwn.college{UCnBFD0dcnemQEjadSxfkBzUEiP.dNjM4QDL5QzM1czW}

Matching paths with [] –
Execute /challenge/run with /challenge/files/file_[bash] as argument to get the flag.

Flag: pwn.college{IEG3rCu8l92dYsvix8pD6kAolLs.dRjM4QDL5QzM1czW}

Exclusionary Globbing –
use cd to go to /challenge/files. Execute /challenge/run with [!pwn]* to avoid files that start with any of these. This will yield the flag.

Flag : pwn.college{oEV0RhKwslx9h1NDbChbyarIpqg.dZjM4QDL5QzM1czW}

Mixing Globs –
Use cd to go to /challenge/files. Execute /challenge/run with potential arguments related to challenge, educational,pwning. And the arguments should be less than 6 chars. When trying to use an argument and its wrong, it displayed other files that have same thing in common. Tried using i and n as common letters but it turned out to be the common ones for too many even in different combinations. Use ls to see all the files. Only challenge,educational and pwning started with letters c , e, and p respectively. So use argument [cpe]* to get the flag.

Flag: pwn.college{IeXU4Lp80HhN13Gf3JCzYXlZONL.dVjM4QDL5QzM1czW}

Practising Piping :
Redirecting output –
use echo command to print PWN and redirect its output to COLLEGE with > to get the flag.

Flag: pwn.college{ET8Akyhr8jT8ho3xv2kRLSIdAN1.dRjN1QDL5QzM1czW}

Redirecting more output –
execute /challenge/run while redirecting the output to myflag using >. This will send the flag to myflag file. cat the myflag file to get the flag.

Flag : pwn.college{gNpbzOYAt1LsFneF2rljk1mTKXe.dVjN1QDL5QzM1czW}

Appending output –
execute /challenge/run while redirecting the output in append mode (>>) to /home/hacker/the-flag. This will add the second part of the flag to the first part of the flag that already existed in the the-flag file. cat the file to get the flag.

Flag: pwn.college{gYmOU1tYJAdWEhT37GvPACwGgIz.ddDM5QDL5QzM1czW}

Redirecting errors –
execute /challenge/run and redirect the output (>) to myflag and redirect the error(2>) to instructions. Now cat myflag to get the flag.

Flag : pwn.college{kKCFuBP1R4niNCJ0pwRpyFZZiBY.ddjN1QDL5QzM1czW}

Redirecting Input –
execute echo with COLLEGE as argument and redirect output (>) to PWN file. Now execute /challenge/run with input redirection (<) from PWN. This will yield the flag.

Flag : pwn.college{QLyxVc39s25rVBHoDsZLDYczWtw.dBzN1QDL5QzM1czW}

Grepping Stored results –
execute /challenge/run while redirecting its output (>) to /tmp/data.txt. Now grep for pwn.college from /tmp/data.txt.

Flag : pwn.college{I3JoWU0WCRcPUFh1v-F8mj_h6g9.dhTM4QDL5QzM1czW}

Grepping live output –
execute /challenge/run while piping (|) it to grep for pwn.college{.

Flag : pwn.college{YkbmZLW7TeaBsKsSniACeybOUe2.dlTM4QDL5QzM1czW}

Grepping errors –
execute /challenge/run while redirecting error to output (2>&1) then pipe it (|) and grep for pwn.college{ to get the flag.

Flag: pwn.college{cyf9yog8P2T8wqaxBHfwLjUyvsY.dVDM5QDL5QzM1czW}

Duplicating piped data with tee –
execute /challenge/pwn | tee hiii | /challenge/college now the file hiii has the message regarding proper usage of /challenge/pwn with right argument.

Open the hiii file to get that data. Now execute /challenge/pwn --secret szl6bQVw | tee hiii | /challenge/college (based on the instructions). This yields the flag.

Flag: pwn.college{szl6bQVw5mabz22Zx9zjbYEGzJF.dFjM5QDL5QzM1czW}

Writing to multiple programs –
execute /challenge/hack | tee >(/challenge/the) >(/challenge/planet). This will give output of /challenge/hack to /challenge/the and to /challenge/planet.

Flag : pwn.college{UVdkj_B4HnRyNLLoNJW9DDDDcAX.dBDO0UDL5QzM1czW}

Writing to multiple programs –
execute /challenge/hack | 2>(/challenge/the) | >(/challenge/planet) to send the stderr to /challenge/the and the stdout to /challenge/planet.

Flag : pwn.college{Mxg5Hyyj2HRvgYzIQpxPSoDHHdf.dFDNwYDL5QzM1czW}

Markdown 10753 bytes 1606 words 253 lines Ln 1, Col 0HTML 8686 characters 1546 words 126 paragraphs