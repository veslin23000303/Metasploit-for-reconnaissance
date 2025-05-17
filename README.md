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


#### OUTPUT:
![ip-of-attacker](https://github.com/Manoj162004/Metasploit-for-reconnaissance/assets/120365042/3124bd5e-f8c7-49c8-843f-f798d3c2a6fc)

Invoke msfconsole:

![msfconsole](https://github.com/Manoj162004/Metasploit-for-reconnaissance/assets/120365042/ab8fc40d-0e55-40fb-aa28-a2567dffd231)

Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

![msf-info](https://github.com/Manoj162004/Metasploit-for-reconnaissance/assets/120365042/9418b63d-9976-49f0-b2f1-23f505936edf)

#### Port Scanning:
Following command is executed for scanning the systems on our local area network with a TCP scan (-sT) looking for open ports between 1 and 1000 (-p1-1000).
msf >  nmap -sT 192.168.1810/24 -p1-1000
#### OUTPUT:
![msf-nmap](https://github.com/Manoj162004/Metasploit-for-reconnaissance/assets/120365042/3e461f4c-1e49-4477-9455-e695fb8b050f)
step4:
use the db-nmap command to scan and save the results into Metasploit's postgresql attached database. In that way, you can use those results in the exploitation stage later.

scan the targets with the command db_nmap as follows.
msf > db_nmap 192.168.181.0/24
#### OUTPUT:

![db_nmap](https://github.com/Manoj162004/Metasploit-for-reconnaissance/assets/120365042/78cf8911-1cfc-4b2e-96a1-319c70156555)

Metasploit has a multitude of scanning modules built in. If we open another terminal, we can navigate to Metasploit's auxiliary modules and list all the scanner modules.
cd /usr/share /metasploit-framework/modules/auxiliary
kali > ls -l
#### OUTPUT:

![auxiliary-ls-l](https://github.com/Manoj162004/Metasploit-for-reconnaissance/assets/120365042/87dd0e6a-ba3a-4066-af83-fdb2daa0aae9)

Search is a powerful command in Metasploit that you can use to find what you want to locate. 
msf >search name:Microsoft type:exploit

The info command provides information regarding a module or platform,
#### OUTPUT
![msfsearch](https://github.com/Manoj162004/Metasploit-for-reconnaissance/assets/120365042/dc038257-ee12-4ee7-8477-c2a7192cab98)

Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows:
systemctl start postgresql
msfdb init
#### MYSQL ENUMERATION
Find the IP address of the Metasploitable machine first. Then, use the db_nmap command in msfconsole with Nmap flags to scan the MySQL database at 3306 port.
db_nmap -sV -sC -p 3306 <metasploitable_ip_address>

![db_nmap](https://github.com/Manoj162004/Metasploit-for-reconnaissance/assets/120365042/78cf8911-1cfc-4b2e-96a1-319c70156555)

Use the search option to look for an auxiliary module to scan and enumerate the MySQL database.
search type:auxiliary mysql

![searchtypeauxiliarymysql](https://github.com/Manoj162004/Metasploit-for-reconnaissance/assets/120365042/420e94f9-8eeb-44e9-9f06-925cb627eb66)

use the auxiliary/scanner/mysql/mysql_version module by typing the module name or associated number to scan MySQL version details.
use 11 Or: use auxiliary/scanner/mysql/mysql_version

![use11](https://github.com/Manoj162004/Metasploit-for-reconnaissance/assets/120365042/521e3966-f0f2-4e28-b4a4-19133ddb8220)


Use the set rhosts command to set the parameter and run the module, as follows:

![setrhost](https://github.com/Manoj162004/Metasploit-for-reconnaissance/assets/120365042/d129eec5-a1d3-4372-a95d-883e8add8c8e)


After scanning, you can also brute force MySQL root account via Metasploit's auxiliary(scanner/mysql/mysql_login) module.

![mysql_login](https://github.com/Manoj162004/Metasploit-for-reconnaissance/assets/120365042/27c829a5-e0e3-4488-a0a9-87156cff2ea7)

set the PASS_FILE parameter to the wordlist path available inside /usr/share/wordlists:
set PASS_FILE /usr/share/wordlistss/rockyou.txt
Then, specify the IP address of the target machine with the RHOSTS command.
set RHOSTS <metasploitable-ip-address>
Set BLANK_PASSWORDS to true in case there is no password set for the root account.
set BLANK_PASSWORDS true

![pass_file_parameter](https://github.com/Manoj162004/Metasploit-for-reconnaissance/assets/120365042/fa4a5ed2-12c3-409b-9af3-ae5b8c543615)

#### RESULT:
The Metasploit framework for reconnaissance is  examined successfully.











## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
