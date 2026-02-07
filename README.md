# Metasploit-for-reconnaissance
# Metasploit
Metasploit for reconnaissance in pentesting

# AIM:

To get introduced to Metasploit Framework and to  perform reconnaissance  in pentesting .

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode

### Step 2:

Investigate on the various categories of tools as follows:

### Step 3:

Open terminal and try execute some kali linux commands

## EXECUTION STEPS AND ITS OUTPUT:

Find out the ip address of the attackers system
## OUTPUT:
<img width="1183" height="847" alt="image" src="https://github.com/user-attachments/assets/eafff71b-20fe-4b54-9e93-e1017a1a440d" />


Invoke msfconsole:
## OUTPUT:
<img width="1422" height="603" alt="image" src="https://github.com/user-attachments/assets/4563cff2-067f-47a5-8617-d9c54f2421a8" />


Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

<img width="1467" height="864" alt="image" src="https://github.com/user-attachments/assets/245e3b36-5b21-462e-b7fe-7d28088d60bd" />



Port Scanning:
Following command is executed for scanning the systems on our local area network with a TCP scan (-sT) looking for open ports between 1 and 1000 (-p1-1000).
msf >  nmap -sT 192.168.1810/24 -p1-1000  (Replace with appropriate IP Address)
## OUTPUT:
<img width="1280" height="735" alt="image" src="https://github.com/user-attachments/assets/229bb644-29e0-4e47-8595-94d849460baa" />

step4:
use the db-nmap command to scan and save the results into Metasploit's postgresql attached database. In that way, you can use those results in the exploitation stage later.

scan the targets with the command db_nmap as follows.
msf > db_nmap 192.168.181.0/24
## OUTPUT:

<img width="1466" height="609" alt="image" src="https://github.com/user-attachments/assets/1196be17-2531-4e52-8096-f960a5d621b7" />


Metasploit has a multitude of scanning modules built in. If we open another terminal, we can navigate to Metasploit's auxiliary modules and list all the scanner modules.
cd /usr/share /metasploit-framework/modules/auxiliary
kali > ls -l
## OUTPUT:

<img width="1322" height="787" alt="image" src="https://github.com/user-attachments/assets/8e83d420-bd68-4e73-846f-61e1262ad344" />


Search is a powerful command in Metasploit that you can use to find what you want to locate. 
msf >search name:Microsoft type:exploit
## OUTPUT:
<img width="1633" height="760" alt="image" src="https://github.com/user-attachments/assets/d33b5024-0c1e-472c-9c7e-c2833c45f31c" />



The info command provides information regarding a module or platform,

Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows:
systemctl start postgresql
msfdb init
## OUTPUT:

<img width="1638" height="755" alt="image" src="https://github.com/user-attachments/assets/52c5a7d7-7a55-4bdf-8eb7-86b3fc48385f" />



## MYSQL ENUMERATION
Find the IP address of the Metasploitable machine first. Then, use the db_nmap command in msfconsole with Nmap flags to scan the MySQL database at 3306 port.
db_nmap -sV -sC -p 3306 <metasploitable_ip_address>

## OUTPUT:
<img width="1657" height="699" alt="image" src="https://github.com/user-attachments/assets/21599564-0b9f-40ec-9f57-1f86dead3932" />

Use the search option to look for an auxiliary module to scan and enumerate the MySQL database.
search type:auxiliary mysql
## OUTPUT:

<img width="1466" height="442" alt="image" src="https://github.com/user-attachments/assets/bbf802b1-0015-429d-b0f5-b71594f3b51e" />

use the auxiliary/scanner/mysql/mysql_version module by typing the module name or associated number to scan MySQL version details.
use 11
Or:
use auxiliary/scanner/mysql/mysql_version
## OUTPUT:

<img width="1507" height="315" alt="image" src="https://github.com/user-attachments/assets/625be7ba-67b6-445d-a16b-ff0fd00d6e18" />



Use the set rhosts command to set the parameter and run the module, as follows:
## OUTPUT:

<img width="1515" height="218" alt="image" src="https://github.com/user-attachments/assets/c3e7bfbd-9a0f-4552-b853-0aa3231151fc" />


After scanning, you can also brute force MySQL root account via Metasploit's auxiliary(scanner/mysql/mysql_login) module.
## OUTPUT:

<img width="1562" height="622" alt="image" src="https://github.com/user-attachments/assets/858bde1e-2741-4611-a686-734387f1375c" />



set the PASS_FILE parameter to the wordlist path available inside /usr/share/wordlists:
set PASS_FILE /usr/share/wordlistss/rockyou.txt
Then, specify the IP address of the target machine with the RHOSTS command.
set RHOSTS <metasploitable-ip-address>
Set BLANK_PASSWORDS to true in case there is no password set for the root account.
set BLANK_PASSWORDS true
## OUTPUT:
<img width="1580" height="451" alt="image" src="https://github.com/user-attachments/assets/dd1a50a1-2ca9-4ff4-bf8e-418854d4ea1e" />






## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
