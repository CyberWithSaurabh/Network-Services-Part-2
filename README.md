Room Overview

The Network Services 2 room on TryHackMe focuses on enumerating and interacting with common network services that run on enterprise systems. These services provide functionality such as file sharing, email communication, and database management.

However, when these services are misconfigured, they can expose sensitive data and become potential attack vectors.

In this room, we explore how attackers and security professionals interact with these services to identify vulnerabilities.

🎯 Learning Objectives

After completing this room, you will be able to:

Identify common network services running on a target machine
Enumerate services using penetration-testing tools
Interact with exposed services
Extract useful information from misconfigured services
Understand common security risks associated with network services
🛠 Tools Used
Tool	Purpose
Nmap	Network scanning and service detection
Telnet	Manual interaction with network services
MySQL Client	Connecting to database services
showmount	Enumerating NFS shares
mount	Mounting remote file systems
📡 Task 1 — Service Enumeration

Service enumeration is the process of discovering services running on a target system.

The first step in any penetration test is to scan the target machine for open ports and running services.

Example Scan
nmap -sC -sV <target-ip>

This scan performs:

Default script scanning
Service version detection
Open port discovery
Identification of running services
📂 Task 2 — NFS (Network File System)
What is NFS?

NFS allows systems to share directories and files across a network. It is commonly used in Linux environments for remote file access.

If NFS shares are improperly configured, attackers may mount remote directories and access sensitive files.

Enumerating NFS Shares
showmount -e <target-ip>

Example output:

/home *
/var *
Mounting the Share

Create a local directory:

mkdir /tmp/mount

Mount the share:

mount <target-ip>:/home /tmp/mount

View files:

ls /tmp/mount
📧 Task 3 — SMTP Enumeration
What is SMTP?

SMTP (Simple Mail Transfer Protocol) is used to send email messages between servers.

SMTP typically runs on port 25.

Attackers often use SMTP enumeration to discover valid usernames.

Connecting to SMTP Server
telnet <target-ip> 25

Example banner:

220 mail.example.com SMTP Service Ready
SMTP Commands
Command	Description
HELO	Identify client
VRFY	Verify user
EXPN	Expand mailing list
MAIL FROM	Specify sender
RCPT TO	Specify recipient

Example:

VRFY admin
🗄 Task 4 — MySQL Enumeration
What is MySQL?

MySQL is a widely used relational database management system used by web applications.

It typically runs on port 3306.

Connecting to MySQL
mysql -h <target-ip> -u root
Database Enumeration

List databases:

show databases;

Select database:

use database_name;

List tables:

show tables;

View data:

select * from table_name;
⚠ Security Risks

Misconfigured services may expose sensitive information such as:

Database credentials
Usernames
Configuration files
Internal system data

Understanding how these services work helps security professionals detect vulnerabilities.

🛡 Skills Learned
Network service enumeration
Interaction with exposed services
NFS share discovery
SMTP user enumeration
MySQL database exploration
📚 Platform

Room: TryHackMe — Network Services 2
Difficulty: Beginner / Intermediate

👨‍💻 Author      Saurabh 
Cybersecurity & Networking Enthusiast
