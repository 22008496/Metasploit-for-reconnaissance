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
![Screenshot 2024-04-27 132501](https://github.com/22008496/Metasploit-for-reconnaissance/assets/119476113/bf1abe5f-d384-44ae-bc36-acd2faae3cd4)

##Invoke msfconsole:
![Screenshot 2024-04-27 132720](https://github.com/22008496/Metasploit-for-reconnaissance/assets/119476113/0b1529e4-3ed7-4bfb-b468-d3881f1fda13)

##Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.
![Screenshot 2024-04-27 133041](https://github.com/22008496/Metasploit-for-reconnaissance/assets/119476113/7048e68b-3fa5-4775-8105-34a9b60c89ca)

Port Scanning:

Following command is executed for scanning the systems on our local area network with a TCP scan (-sT) looking for open ports between 1 and 1000 (-p1-1000).

msf > nmap -sT 192.168.1810/24 -p1-1000



## OUTPUT:
![Screenshot 2024-04-27 133202](https://github.com/22008496/Metasploit-for-reconnaissance/assets/119476113/d4ff9eed-2f52-4253-b1f6-6624428cbfe6)

use the db-nmap command to scan and save the results into Metasploit's postgresql attached database. In that way, you can use those results in the exploitation stage later.

scan the targets with the command db_nmap as follows.

msf > db_nmap 192.168.181.0/24

OUTPUT:
![Screenshot 2024-04-27 133445](https://github.com/22008496/Metasploit-for-reconnaissance/assets/119476113/c90581d0-0a93-4003-83fc-7b6046230873)

Metasploit has a multitude of scanning modules built in. If we open another terminal, we can navigate to Metasploit's auxiliary modules and list all the scanner modules.

cd /usr/share /metasploit-framework/modules/auxiliary

kali > ls -l

OUTPUT:
![Screenshot 2024-04-27 133707](https://github.com/22008496/Metasploit-for-reconnaissance/assets/119476113/ca751a5e-9c2d-47bf-a2c4-549a20da9387)

Search is a powerful command in Metasploit that you can use to find what you want to locate.

msf >search name:Microsoft type:exploit
![Screenshot 2024-04-27 133812](https://github.com/22008496/Metasploit-for-reconnaissance/assets/119476113/d7963e37-5a8c-47e7-8b7c-496781d8fddf)

The info command provides information regarding a module or platform

OUTPUT:
![Screenshot 2024-04-27 134231](https://github.com/22008496/Metasploit-for-reconnaissance/assets/119476113/356f8520-8021-4fbe-b91d-46eec17dfe6c)

Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows:

systemctl start postgresql

msfdb init

MYSQL ENUMERATION

Find the IP address of the Metasploitable machine first. Then, use the db_nmap command in msfconsole with Nmap flags to scan the MySQL database at 3306 port.

db_nmap -sV -sC -p 3306 <metasploitable_ip_address>

![Screenshot 2024-04-27 134432](https://github.com/22008496/Metasploit-for-reconnaissance/assets/119476113/a7898301-32df-4db9-ae3e-b88f6e2425ae)

Use the search option to look for an auxiliary module to scan and enumerate the MySQL database. search type:auxiliary mysql

![Screenshot 2024-04-27 134614](https://github.com/22008496/Metasploit-for-reconnaissance/assets/119476113/1e987272-c646-40a5-86bd-68b4fb9db674)

use the auxiliary/scanner/mysql/mysql_version module by typing the module name or associated number to scan MySQL version details.

use 11 Or: use auxiliary/scanner/mysql/mysql_version

![Screenshot 2024-04-27 134723](https://github.com/22008496/Metasploit-for-reconnaissance/assets/119476113/97a6f1b0-06db-40d7-8ca0-730fd055216e)

Use the set rhosts command to set the parameter and run the module, as follows:

![Screenshot 2024-04-27 134825](https://github.com/22008496/Metasploit-for-reconnaissance/assets/119476113/8307374e-9680-44d8-928c-81c9a7a8a2d3)

After scanning, you can also brute force MySQL root account via Metasploit's auxiliary(scanner/mysql/mysql_login) module.

![Screenshot 2024-04-27 134919](https://github.com/22008496/Metasploit-for-reconnaissance/assets/119476113/08ce5340-5c0a-4cff-afe6-02c2d77f71e8)

set the PASS_FILE parameter to the wordlist path available inside /usr/share/wordlists:

set PASS_FILE /usr/share/wordlistss/rockyou.txt

Then, specify the IP address of the target machine with the RHOSTS command.

set RHOSTS

Set BLANK_PASSWORDS to true in case there is no password set for the root account.

set BLANK_PASSWORDS true

![Screenshot 2024-04-27 135034](https://github.com/22008496/Metasploit-for-reconnaissance/assets/119476113/302d2101-acd2-4dc6-9d49-a89eb566d5b7)



## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
