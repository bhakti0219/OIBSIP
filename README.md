
# OIBSIP

## TASK 1 - Basic Network Scanning with Nmap

### 1. Basic Scan

Command : nmap <target_ip>

<img width="571" height="508" alt="image" src="https://github.com/user-attachments/assets/a83c9ad8-5439-41fd-8cf2-df29ed72bec9" />

Shows the basic Nmap scan used to identify reachable/open TCP ports on the authorized lab target.

### 2. Service version scan

Command : nmap -sV <target_ip>

<img width="672" height="506" alt="image" src="https://github.com/user-attachments/assets/3f6e6e2d-5e6a-4e3f-a582-9e1b15000f0e" />
<img width="1019" height="76" alt="image" src="https://github.com/user-attachments/assets/c5cd870b-aef4-4e16-923b-6cc11c60324a" />

Shows Nmap service and version detection using the -sV option.

### 3. OS detection scan

Command: sudo nmap -O <target_ip>

<img width="926" height="553" alt="image" src="https://github.com/user-attachments/assets/b9e55288-b835-4628-9c0c-24d354be1138" />
<img width="816" height="328" alt="image" src="https://github.com/user-attachments/assets/70d51f8f-da6d-4a2b-8a62-213905642c1c" />





| Port         | Service / Version                             | What the service does                                                              | Security risk                                                                                                                             |
| ------------ | --------------------------------------------- | ---------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------- |
| **21/tcp**   | FTP – vsftpd 2.3.4                            | Transfers files between computers.                                                 | 🔴 **High** – FTP is unencrypted, so credentials/data can be exposed. The detected version is also very old.                              |
| **22/tcp**   | SSH – OpenSSH 4.7p1                           | Provides secure remote login and administration.                                   | 🟠 **Medium** – SSH is designed to be secure, but this is an old version and an exposed SSH service should be properly secured.           |
| **23/tcp**   | Telnet – Linux telnetd                        | Provides remote command-line access.                                               | 🔴 **High** – Telnet does not provide encrypted communication, making credentials and data vulnerable to interception.                    |
| **25/tcp**   | SMTP – Postfix                                | Sends and receives email between mail servers.                                     | 🟠 **Medium** – An exposed mail service can be abused if improperly configured.                                                           |
| **53/tcp**   | DNS – ISC BIND 9.4.2                          | Resolves domain names into IP addresses and provides DNS information.              | 🔴 **High** – An old/exposed DNS service can create security risks if vulnerable or misconfigured.                                        |
| **80/tcp**   | HTTP – Apache httpd 2.2.8                     | Hosts and serves websites over HTTP.                                               | 🔴 **High** – HTTP traffic is unencrypted, and the detected Apache version is very old.                                                   |
| **111/tcp**  | RPCBind – RPC #100000                         | Maps RPC services to their network ports.                                          | 🟠 **Medium** – Exposing RPC services can reveal information about available network services.                                            |
| **139/tcp**  | NetBIOS-SSN – Samba 3.x–4.x                   | Provides NetBIOS session services, commonly used for network file/printer sharing. | 🔴 **High** – Network sharing exposure can allow unauthorized access if poorly secured.                                                   |
| **445/tcp**  | Microsoft-DS – Samba 3.x–4.x                  | Provides SMB file and printer sharing.                                             | 🔴 **High** – SMB exposure can allow unauthorized file sharing/access when improperly configured.                                         |
| **512/tcp**  | exec – netkit-rsh rexecd                      | Provides remote command execution.                                                 | 🔴 **High** – Remote command execution services are dangerous when exposed because they can permit unauthorized system access.            |
| **513/tcp**  | login – rlogin                                | Provides remote login to a Unix/Linux system.                                      | 🔴 **High** – rlogin is an insecure legacy remote-login protocol.                                                                         |
| **514/tcp**  | shell – rshd                                  | Provides remote shell/command execution.                                           | 🔴 **High** – Legacy remote shell services provide insecure remote access.                                                                |
| **1099/tcp** | Java RMI Registry – GNU Classpath rmiregistry | Registers and locates Java RMI remote objects.                                     | 🔴 **High** – An exposed RMI service can increase the risk of unauthorized remote interaction with applications.                          |
| **1524/tcp** | bindshell – Metasploitable root shell         | Provides a network-accessible command shell.                                       | 🔴 **Critical** – A shell exposed over the network can provide direct unauthorized command execution.                                     |
| **2049/tcp** | NFS – 2–4 / RPC #100003                       | Provides network file-system sharing.                                              | 🔴 **High** – Improperly secured NFS can expose files and directories to unauthorized users.                                              |
| **2121/tcp** | FTP – ProFTPD 1.3.1                           | Provides file-transfer services.                                                   | 🔴 **High** – FTP is unencrypted and the detected software version is old.                                                                |
| **3306/tcp** | MySQL – 5.0.51a                               | Database server used to store and retrieve application data.                       | 🔴 **High** – Directly exposed database services increase the risk of unauthorized database access.                                       |
| **5432/tcp** | PostgreSQL – 8.3.0–8.3.7                      | Database server used to store and manage structured data.                          | 🔴 **High** – Direct network exposure of a database should be restricted and properly authenticated.                                      |
| **5900/tcp** | VNC – protocol 3.3                            | Provides graphical remote-desktop access.                                          | 🔴 **High** – Exposed remote-desktop services can allow unauthorized access if authentication/security is weak.                           |
| **6000/tcp** | X11                                           | Provides remote X Window System graphical-display access.                          | 🔴 **High** – Exposed X11 can allow unauthorized access to graphical sessions if not properly secured.                                    |
| **6667/tcp** | IRC – UnrealIRCd                              | Provides Internet Relay Chat communication.                                        | 🟠 **Medium** – An exposed IRC service can be abused if outdated or poorly configured.                                                    |
| **8009/tcp** | AJP13 – Apache JServ                          | Connects Apache web servers with Java application servers such as Tomcat.          | 🔴 **High** – An exposed AJP connector can create security risks if improperly configured.                                                |
| **8180/tcp** | HTTP – Apache Tomcat/Coyote JSP engine 1.1    | Provides web/application-server functionality.                                     | 🔴 **High** – An exposed application server can provide an attack surface, particularly when running an old configuration/software stack. |


### Security Analysis

The scan identified 23 open TCP ports on the authorized lab target. The services include FTP, SSH, Telnet, HTTP, SMB, NFS, MySQL, PostgreSQL, VNC, X11, IRC, Java RMI, and other remote-access services.

Several exposed services present significant security risks because they use insecure legacy protocols, provide remote administration or command execution, expose databases, or are running old software versions. Telnet, rlogin, rsh, FTP, exposed databases, remote desktop services, and the network-accessible bind shell are particularly important findings.

This assessment demonstrates why network scanning is important: it helps identify exposed services that may require patching, access restrictions, encryption, stronger authentication, or removal when they are not required.


OS Detection Result: Nmap attempted OS detection using -O, but no exact operating-system match was identified.

### 4. Save result

Command : nmap  -sV -O <target_ip> | tee nmap_scan_result.txt
          cat nmap_scan_result.txt

<img width="958" height="583" alt="image" src="https://github.com/user-attachments/assets/e2208300-0d86-4a0e-b0c3-bb42d8d74e3b" />
<img width="996" height="332" alt="image" src="https://github.com/user-attachments/assets/8415b41a-688e-424a-80b8-8520a1d383cc" />

Shows the saved Nmap scan results containing discovered ports, services, versions, MAC address information, and OS-detection output.


## TASK 2 · Basic Firewall Configuration with UFW

### Step 1 - Install

Command : sudo apt update
          sudo apt install ufw -y

<img width="864" height="234" alt="image" src="https://github.com/user-attachments/assets/1c854b03-f0e0-4efc-b24a-b8744c3cc64d" />

<img width="964" height="500" alt="image" src="https://github.com/user-attachments/assets/2ec31e74-4a75-42ac-9549-2aa254d6530d" />


### Step 2 - Allow SSH

Command : sudo ufw allow ssh

<img width="503" height="84" alt="image" src="https://github.com/user-attachments/assets/b79be318-7b7d-4033-8646-40653278e10e" />


### Step 3 - Deny HTTP

Command : sudo ufw deny http

<img width="483" height="87" alt="image" src="https://github.com/user-attachments/assets/7f8fdc81-c72e-4016-91b7-a27062447946" />


### Step 4 - Allow HTTPS

Command : sudo ufw allow https

<img width="412" height="84" alt="image" src="https://github.com/user-attachments/assets/d92cda79-3090-4c12-a1bb-4b7b33c1fd00" />


### Step 5 - Deny FTP

Command : sudo ufw demy ftp

<img width="445" height="82" alt="image" src="https://github.com/user-attachments/assets/98a6f3b9-84dc-452c-9b6d-5b8209add8fe" />


### Step 6 - Enable

Command : sudo ufw enable

<img width="547" height="67" alt="image" src="https://github.com/user-attachments/assets/64214b91-0fb3-4135-bae9-675b6b2cf92a" />


### Step 7 - Verify

Command : sudo ufw status verbose

<img width="587" height="362" alt="image" src="https://github.com/user-attachments/assets/07c9846e-b1ee-437a-bea9-731092409226" />

### Step 8 - Create Script

Command : nano ufw_configuration.sh

this puted in nano:

!/bin/bash

sudo ufw allow ssh
sudo ufw deny http
sudo ufw allow https
sudo ufw deny ftp

sudo ufw enable
sudo ufw status verbose


Saved :

chmod +x ufw_configuration.sh

<img width="507" height="106" alt="image" src="https://github.com/user-attachments/assets/66afde99-96ea-4ad9-9224-2b709669279f" />

<img width="802" height="134" alt="image" src="https://github.com/user-attachments/assets/28f22f28-833d-49e1-b4f7-92e5ab163250" />

Run it :
./ufw_configuration.sh

<img width="525" height="441" alt="image" src="https://github.com/user-attachments/assets/9d0468ff-de46-499b-992e-c0f46671b8ea" />

### Step 9 - Test

Command : sudo ufw status numbered

<img width="540" height="252" alt="image" src="https://github.com/user-attachments/assets/779745d0-6f78-4e30-b2d5-9569ce1b6cff" />



## Task 3 - SQL Injection on DVWA (Low Security)


### Step 1 - Install required packages

Command : sudo apt update
sudo apt install apache 2
mariadb-server php php-mysqli git -y


<img width="1012" height="477" alt="image" src="https://github.com/user-attachments/assets/2ec55957-f645-436d-89e3-13dfed77ac1f" />

<img width="984" height="503" alt="image" src="https://github.com/user-attachments/assets/aaad0424-e9ec-43d3-bacf-5bdfd83b2c20" />

<img width="738" height="511" alt="image" src="https://github.com/user-attachments/assets/cc1a5b6c-28fc-48fa-a44e-610135b9929b" />

Command :
Start services :  

sudo systemctl start apache2
sudo systemctl start mariadb

Enable them :

sudo systemctl enable apache2
sudo systemctl enable mariadb

<img width="995" height="224" alt="image" src="https://github.com/user-attachments/assets/ef4acda3-d47d-4569-8439-024332168b96" />


### Step 2 - Download DVWA

cd /var/www/html
sudo git clone https://github.com/digininja/DVWA.git dvwa

<img width="640" height="223" alt="image" src="https://github.com/user-attachments/assets/2d34c7e6-7faf-43fb-a581-c94ecb6467b7" />

Set permissions:

sudo chown -R www-data:www-data /var/www/html/dvwa

<img width="466" height="193" alt="image" src="https://github.com/user-attachments/assets/3a6c5677-6616-4c4a-a014-2d0b8c84fb7e" />

### Step 3 - Configure DVWA

cd /var/www/html/dvwa/config
sudo cp config.inc.php.dist config.inc.php

<img width="402" height="192" alt="image" src="https://github.com/user-attachments/assets/8af09810-7f36-47e2-9de2-1ccd9ae244a7" />

<img width="1308" height="519" alt="db" src="https://github.com/user-attachments/assets/06355e0e-c660-4b02-813c-e1e1cce43dd4" />

### Step 5 - Set security to Low





## Task 4 - Network Security Threats

Created :
network_security_threats_report.md


<img width="702" height="396" alt="image" src="https://github.com/user-attachments/assets/07ea5b18-a4b4-48fe-8e52-dc62f99f744a" />


<img width="1359" height="484" alt="image" src="https://github.com/user-attachments/assets/d7b61e2e-ffd3-4f6e-b1bc-c63663688df9" />

<img width="1355" height="495" alt="image" src="https://github.com/user-attachments/assets/af9decbf-b654-4653-ae8d-54fce74bdfe2" />

<img width="1348" height="507" alt="image" src="https://github.com/user-attachments/assets/3e212e96-f653-4dff-a747-f2758b05bd54" />

<img width="1363" height="516" alt="image" src="https://github.com/user-attachments/assets/aa280873-f839-4b68-909a-ffbfbeb80e92" />

<img width="1345" height="504" alt="image" src="https://github.com/user-attachments/assets/c13845c8-be17-4f63-98ca-0ac33ec10e66" />

<img width="1349" height="503" alt="image" src="https://github.com/user-attachments/assets/bfb6ddaa-bb5f-4408-a289-50036a847d21" />

<img width="1353" height="450" alt="image" src="https://github.com/user-attachments/assets/814db2db-882f-4d46-b6c9-800d05276036" />

<img width="1280" height="517" alt="image" src="https://github.com/user-attachments/assets/bb558b3e-ab02-4f75-8160-5ac9217ba1a1" />

<img width="1356" height="479" alt="image" src="https://github.com/user-attachments/assets/0b21f41f-11ce-45d2-ad57-da3b669084f3" />

<img width="1347" height="510" alt="image" src="https://github.com/user-attachments/assets/cf225855-ceb6-4bba-a7ac-dfad60d667f9" />

<img width="1353" height="516" alt="image" src="https://github.com/user-attachments/assets/2fad9c9e-21a9-46e3-ba0e-d3e8904f783f" />

<img width="1359" height="514" alt="image" src="https://github.com/user-attachments/assets/0a33d4bf-0c9e-471a-9639-aca9a397f07f" />
