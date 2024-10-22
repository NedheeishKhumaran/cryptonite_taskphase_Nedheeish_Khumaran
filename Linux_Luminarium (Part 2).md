# Linux Luminarium (Part 2)
## Shell Variables:
### Printing Variables – use `echo` with `$FLAG` as argument (FLAG is a variable name here). This will print the contents of `FLAG`. 
Flag : pwn.college{wXCeIeD0mylkOfaLPl4f4t9h5cq.ddTN1QDL5QzM1czW}

### Setting Variable – assign `COLLEGE` to variable `PWN`.  `PWN=COLLGE`.
Flag : pwn.college{05jO981e2gWyLlCsaf4Tca2OgVs.dlTN1QDL5QzM1czW}

### Multiword variables – assign,  `PWN=COLLEGE YEAH` to get the flag.
Flag: pwn.college{gAKleU1SicSiK23Ayf6SYD-1jAh.dBjN1QDL5QzM1czW}

### Exporting Variables – assign and export `PWN=COLLEGE` and then just assign ‘COLLEGE=PWN’. Now invoke /challenge/run to get the flag.
Flag: pwn.college{sUjz-QJmmFvhtwgF2HjWCFzEUHg.dJjN1QDL5QzM1czW}

### Printing exported variables – invoke command env to print out all the exported variables. Search for `FLAG` variable to get the flag.
Flag: pwn.college{YgDN3oFJd-Yh_OmegWBa-Oemrki.dhTN1QDL5QzM1czW}

### Storing command output – assign the output of `/challenge/run` to the variable ‘PWN’. `PWN=$(/challenge/run)`. Now ‘echo $PWN’ to print its contents. There is the flag.
Flag: pwn.college{kqPmSYv8-w_emEjurm9EtMwPFfY.dVzN0UDL5QzM1czW}

### Reading input – read input for `PWN` variable. The input should be `COLLEGE`. ‘read -p “input PWN =  ” PWN’. `input PWN = COLLEGE`.  This gives the flag.
Flag: pwn.college{U70a167Ptlp4fASmRyHWwUhrE_W.dhzN1QDL5QzM1czW}

### Reading files – read into PWN variable, the file `/challenge/read_me`. `read PWN < /challenge/read_me` to get the flag.
Flag: pwn.college{M2ChGWK-alwLbeNgWQj2SmHNSTW.dBjM4QDL5QzM1czW}


## Processes and Jobs
### Listing Processes – invoke the command `ps -ef` to get the renamed version of `/challenge/run` from the list of processes. Now access the renamed file to get the flag.
Flag: pwn.college{QHFwpQu5kjeOHm3O4p9Chb1Fb5R.dhzM4QDL5QzM1czW}

### Killing processes – To find the PID of the process `/challenge/dont_run`, invoke `ps -ef | grep challenge/dont_run`. From this find the PID of it and invoke `kill <PID>`. This will kill the process. Now execute `/challenge/run` to get the flag.
Flag: pwn.college{wOvkvk0OSJFTgGmIcXwN4VVvp1n.dJDN4QDL5QzM1czW}
### Interrupting processes – invoke `/challenge/run`. Then interrupt it using `ctrl+c`. This will yield the flag.
Flag: pwn.college{IHqHnnC9cb3EjZc41ua2pSWyWRP.dNDN4QDL5QzM1czW}

### Suspending processes – invoke `/challenge/run`. Now press `ctrl+z` to suspend the process and then invoke `/challenge/run ` to get the flag.
Flag: pwn.college{UgdZZWNm5F_BMT4tWMN8a-KkUKh.dVDN4QDL5QzM1czW}

### Resuming processes – invoke `/challenge/run`.  Now press `ctrl+z` to suspend the process and then use `fg` to resume the process. This will yield the flag.
Flag: pwn.college{gGTez21iUSWFsD3ZuII8FzKO0_N.dZDN4QDL5QzM1czW}

### Backgrounding Processes  – invoke `/challenge/run`. Now press `ctrl+z` to suspend the process and invoke `bg` to background it. Then again invole `/challenge/run` to get the flag.
Flag: pwn.college{cwH3gubpFeggghkwhaNWOxCWyIq.ddDN4QDL5QzM1czW}

### Foregrounding Processes – invole `/challenge/run`. Now press `ctrl+z` to suspend it. Then send it to background by using  `bg` and then again enter `fg` to bring it to foreground. Press `Enter` to get the flag.
Flag: pwn.college{44TElLqdVMP6pDwbOJ1mWyikZGD.dhDN4QDL5QzM1czW}

### Starting backgrounded processes – invole `/challenge/run &` to run this directly in the background. This will yield the flag.
Flag: pwn.college{062SSZM-iTCBDkyt8fSHPW-23xd.dlDN4QDL5QzM1czW}

### Process exit codes – invoke `/challenge/get-code’ and then get its error code by invoking `echo $?`. Invoke `/challenge/submit-code <the error code>` this will yield the flag.
Flag: pwn.college{gXqVshoEJDd0gSkF2sRyQ42wy3s.dljN4UDL5QzM1czW}

## Perceiving Permissions
### Changing file ownership – invoke `chown hacker /flag` to change the ownership to hacker user. Then `cat /flag` to read its contents. 
Flag: pwn.college{wDnbc6-z7QnHIjtZZEv0lFqdOqG.dFTM2QDL5QzM1czW}

### Groups and Files – invoke `ls – l /flag` to know its permissions. It is owned by root user and root group. Now invoke `chgrp hacker /flag`. This changes the group that has access to the file to `hacker`.  Now `cat /flag` to get the flag.
Flag: pwn.college{0PYmIj49Ycg3u5reGW5J_fbQt59.dFzNyUDL5QzM1czW}

### Fun with Group names – invoke `id` to find the group that your user is in. Then invoke `chgrp <your_group> /flag` to change group to your group. Now `cat /flag` to read its contents.
Flag: pwn.college{kMGlr9eULEkgwwdvyPYwTBWfrpx.dJzNyUDL5QzM1czW}

### Changing permissions – invoke `ls -l /flag` to know the file permissions of /flag file. Then invoke `chmod o+r /flag` to change “ others’ ” permission to read the file. `cat /flag` to get the flag.
Flag: pwn.college{4JUQUgoJxldurqYs6cc-AZTSOaQ.dNzNyUDL5QzM1czW}

### Executable files – invoke ‘ls -l /challenge/run’ to check its permissions. Hacker user is the owner. Therefore, invoke `chmod u+x /challenge/run` to give execution permission to the hacker user who is the owner here. Now invoke `/challenge/run` to get the flag.
Flag: pwn.college{EdV2f6AAbzhS7wHt36MFMaxe52h.dJTM2QDL5QzM1czW}

### Permission tweaking practice – invoke `/challenge/run` to start the rounds of permission changing. Multiple permissions can be changed in a single command by using comma(`,`) between them, like `chmod u+x,o-w /challenge/pwn`. After 8 successful rounds of tweaking, /flag file’s ownership is given to `hacker` user. Using chmod change its permission to read for hacker user by `chmod u+r /flag`. Now `cat /flag` to read its contents.
Flag: pwn.college{Iw-VPh1b0c0Os72BX7hrxouNPxR.dBTM2QDL5QzM1czW}


### Permission setting practice - invoke `/challenge/run` to start the rounds of permission setting. Multiple permissions can be set in a single command by using comma(`,`) between them, like `chmod u=wx,g=rx,o=- /challenge/pwn`. Similar to last challenge, but here set the permissions instead of altering the existing ones.
Flag: pwn.college{sh6ysL-Zr2t1P1B5P4Thtlw9QLp.dNTM5QDL5QzM1czW}

### SUID bit – invoke `chmod u+s /challenge/getroot` to give super user executable permission to the file. Now run `/challenge/getroot` to get the flag.
 Flag: pwn.college{IWomqAdLpDp0-Ey3eD3n6g4mes2.dNTM2QDL5QzM1czW}


## Untangling users 
### Becoming root using su - invoke `su cat /flag` to read contents of /flag with super user privileges. Password for su was provided.
Flag: pwn.college{sg-c-qUsejqpHFTvag5wT13BPtd.dVTN0UDL5QzM1czW}

###Other users with su – invoke `su zardus` to switch to zardus user. Password is provided. Invoke `/challenge/run` to get the flag.
Flag: pwn.college{EIpPwdhcXIZdHiw3FWMGmyYCYOA.dZTN0UDL5QzM1czW}

### Cracking Passwords – invoke `john /challenge/shadow-leak` to find the dehashed password for `zardus`. `su zardus` and use that password. Now run `/challenge/run` to get the flag.
Flag: pwn.college{0AnjwcVIG0cWPM17V_RpLRQ78KI.ddTN0UDL5QzM1czW}

### Using sudo – invoke `sudo cat /flag` to read the contents of flag file as superuser.
Flag: pwn.college{0GcY0BT_Iua-8Q1rOIb2H5MN0Ef.dhTN0UDL5QzM1czW}


## Chaining commands
### Chaining with semicolons – invoke ` /challenge/pwn ; /challenge/college` in a chained manner to get the flag.
Flag: pwn.college{Qcey6CWn2YqIb-_ZLrDKaUTgqF2.dVTN4QDL5QzM1czW}

### Your first shell script – invoke `nano x.sh` to create the file and enter it. Now type `/challenge/pwn; /challenge/college`. Press `ctrl+o` to write out. Then `ctrl+x` to exit. Now invoke `bash x.sh` to get the flag.
Flag: pwn.college{M-B6-AfZl2WEUTZKcWt6i4C_vWY.dFzN4QDL5QzM1czW}

### Redirecting Script output – invoke `bash x.sh | /challenge/solve`. x.sh already has the desired program from last challenge. Now piping them will push its output to /challenge/solve.
Flag: pwn.college{YlKITcmW2SgHBeMwqftQG3sllev.dhTM5QDL5QzM1czW}

### Executable shell scripts – create a nano file ‘y.sh’. Enter commands as in `x.sh`. Now invoke `chmod a+x ./y.sh`. this will give executable permission to y.sh and now execute `./y.sh` to get the flag.   Flag: pwn.college{01RV53d03ghlbSCgSn4wBTSfBHd.dRzNyUDL5QzM1czW} 
## Pondering Paths
### The PATH variable – invoke `PATH=””` to ensure that `/challenge/run` cant find `rm` command. Now, run `/challenge/run` to get the flag.
Flag: pwn.college{sOpo8MCG7dkE29-r5zX1HVNWH-S.dZzNwUDL5QzM1czW}
### Setting path – invoke `PATH=”/challenge/more_commands/”` to set path to the path of `win` command. Now execute `/challenge/run`. This will yield the flag.
Flag: pwn.college{cRMcUsj7PN7x7JNJU5ECXqRi4C-.dVzNyUDL5QzM1czW}

### Adding Commands – invoke `nano win` and enter `cat /flag` in it. Now invoke `chmod a+x ./win` to give executable permission. Add win’s path to existing path. `export PATH=$PATH:/home/hacker/` Now run `/challenge/run` to get the flag.
Flag: pwn.college{8BZpgVfc1dzyIR6MEDXzQjRRhW6.dZzNyUDL5QzM1czW}
### Hijacking Commands – invoke `PATH=””` and then invoke `/challenge/run`. Even then the rm deletes the flag. To hijack this one. We need to pretend something else is rm. So, `nano rm` and then enter `cat /flag` in it. Now give `chmod o+x /home/hacker/rm`. Then `echo $PATH` to find its contents. Now add our new `rm`’s address to the front. `PATH=”/home/hacker/:<all the other ones>”`. Now execute `/challenge/run` to get the flag.
Flag: pwn.college{8dnHnKN_dSVXFCLNXgnlRkQ4gG6.ddzNyUDL5QzM1czW}

 

