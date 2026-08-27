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
<img width="1600" height="869" alt="1st" src="https://github.com/user-attachments/assets/47b632e4-a335-4346-8275-ca166266cfff" />


Invoke msfconsole:
## OUTPUT:
<img width="1600" height="869" alt="WhatsApp Image 2026-08-20 at 11 49 15 AM" src="https://github.com/user-attachments/assets/5089f280-b60a-445d-bd3c-f79854c9e1f8" />


Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.




Port Scanning:
Following command is executed for scanning the systems on our local area network with a TCP scan (-sT) looking for open ports between 1 and 1000 (-p1-1000).
msf >  nmap -sT 192.168.1810/24 -p1-1000  (Replace with appropriate IP Address)
## OUTPUT:
<img width="1600" height="869" alt="WhatsApp Image 2026-08-20 at 11 49 16 AM" src="https://github.com/user-attachments/assets/6281355a-03da-4e7e-9043-464d5d165572" />

step4:
use the db-nmap command to scan and save the results into Metasploit's postgresql attached database. In that way, you can use those results in the exploitation stage later.

scan the targets with the command db_nmap as follows.
msf > db_nmap 192.168.181.0/24
## OUTPUT:
<img width="946" height="446" alt="Screenshot 2026-08-20 194321" src="https://github.com/user-attachments/assets/6fe7c88d-809d-41a4-858a-af786bccda34" />

<img width="417" height="77" alt="Screenshot 2026-08-20 194502" src="https://github.com/user-attachments/assets/76cd57ef-3273-4974-a990-6d4fd327f85d" />

Metasploit has a multitude of scanning modules built in. If we open another terminal, we can navigate to Metasploit's auxiliary modules and list all the scanner modules.
cd /usr/share /metasploit-framework/modules/auxiliary
kali > ls -l
## OUTPUT:
<img width="647" height="198" alt="Screenshot 2026-08-20 200122" src="https://github.com/user-attachments/assets/05832c3b-d337-454a-9c2c-2f1820a1a815" />





Search is a powerful command in Metasploit that you can use to find what you want to locate. 
msf >search name:Microsoft type:exploit
## OUTPUT:

<img width="1600" height="869" alt="WhatsApp Image 2026-08-20 at 11 49 16 AM (2)" src="https://github.com/user-attachments/assets/e99e4901-b0f7-49ae-9003-6d317879f5d0" />


The info command provides information regarding a module or platform,

Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows:
systemctl start postgresql
msfdb init
## OUTPUT:
<img width="626" height="343" alt="image" src="https://github.com/user-attachments/assets/2f4c7ed3-7e97-4adc-964c-1d4c0f810a3f" />







## MYSQL ENUMERATION
Find the IP address of the Metasploitable machine first. Then, use the db_nmap command in msfconsole with Nmap flags to scan the MySQL database at 3306 port.
db_nmap -sV -sC -p 3306 <metasploitable_ip_address>

## OUTPUT:
<img width="644" height="136" alt="image" src="https://github.com/user-attachments/assets/fc863ffb-609e-482f-8918-6bacaf68950d" />



Use the search option to look for an auxiliary module to scan and enumerate the MySQL database.
search type:auxiliary mysql
## OUTPUT:
<img width="1600" height="869" alt="WhatsApp Image 2026-08-20 at 11 49 16 AM (3)" src="https://github.com/user-attachments/assets/4fd64ea1-e533-4f41-bc23-da3b5c6d54ec" />




use the auxiliary/scanner/mysql/mysql_version module by typing the module name or associated number to scan MySQL version details.
use 11
Or:
use auxiliary/scanner/mysql/mysql_version
## OUTPUT:
<img width="833" height="618" alt="image" src="https://github.com/user-attachments/assets/f11392b5-2be7-45d3-b05d-c79ee40ff4dc" />





Use the set rhosts command to set the parameter and run the module, as follows:
## OUTPUT:
<img width="627" height="118" alt="image" src="https://github.com/user-attachments/assets/0a0dedc6-61de-4ecc-ab24-f41e759bc138" />











set the PASS_FILE parameter to the wordlist path available inside /usr/share/wordlists:
set PASS_FILE /usr/share/wordlistss/rockyou.txt
Then, specify the IP address of the target machine with the RHOSTS command.
set RHOSTS <metasploitable-ip-address>
Set BLANK_PASSWORDS to true in case there is no password set for the root account.
set BLANK_PASSWORDS true
## OUTPUT:
<img width="644" height="183" alt="image" src="https://github.com/user-attachments/assets/c17f2885-80fd-4c18-ace4-ced45fc240fa" />





## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
