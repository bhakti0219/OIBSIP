
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


OS Detection Result: Nmap attempted OS detection using -O, but no exact operating-system match was identified.

### 4. Save result

Command : nmap  -sV -O <target_ip> | tee nmap_scan_result.txt
          cat nmap_scan_result.txt

<img width="958" height="583" alt="image" src="https://github.com/user-attachments/assets/e2208300-0d86-4a0e-b0c3-bb42d8d74e3b" />
<img width="996" height="332" alt="image" src="https://github.com/user-attachments/assets/8415b41a-688e-424a-80b8-8520a1d383cc" />

Shows the saved Nmap scan results containing discovered ports, services, versions, MAC address information, and OS-detection output.





