---
layout: single
type: docs
permalink: /docs/installation/providers/enterprise/basic-troubleshooting-script/
redirect_from:
  - /theme-setup/
last_modified_at: 2025-06-19
last_modified_by: Sivakumar
toc: true
---

# Faveo Basic Troubleshooting via Scripts <!-- omit in toc -->

<img alt="Troubleshoot" src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQ2rxwH6YebmlMEZtIJSwDUehm2GRIMcwJalQ&s" width="200"  />


## Troubleshooting Faveo Helpdesk via Bash Script for:
- Debian-based servers
- RHEL-based servers

## Introduction
The script is designed to ensure that all essential services and configurations on the Faveo-installed server are functioning correctly. It helps validate system components, identify configuration or connectivity issues, and maintain a stable and healthy Faveo Helpdesk environment. It includes the following diagnostic checks:

SSL Check  
→ Verifies SSL certificate validity for the domain.

System Info  
→ Displays OS, uptime, memory usage, CPU, and disk statistics.

Service Version and Status  
→ Shows version and status of services like Apache, MySQL, PHP, Php-fpm, Redis, etc.

Faveo Info  
→ Displays Faveo APP_URL, plan, and version.

Cron Jobs  
→ Lists all active cron jobs for www-data and root users.

Supervisor Jobs  
→ Checks status of Supervisor Jobs.

Logged-in Users  
→ Displays currently logged-in (SSH) system users.

Billing Connection  
→ Tests connection to the Faveo billing server.

Root-Owned Files in Faveo Directory  
→ Lists files/folders owned by root that may cause permission issues.

Check if Required Ports are Open  
→ Confirms if ports like 80, 443, 3306, 6379 are listening.

Firewall Check  
→ Checks status of firewall (e.g., UFW) and its rules.


## Prerequisites:
- "wget" tool installed.
- sudo or root user privilege

## Do this to run the script

* [Click here](/installation-scripts/FaveoInstallationScripts/basic-troubleshoot.sh) to download the "basic-troubleshoot.sh" or use wget to download using the below command. 

```sh
wget http://raw.githubusercontent.com/faveosuite/faveo-server-images/refs/heads/master/installation-scripts/FaveoInstallationScripts/basic-troubleshoot.sh
```

- Once the file is downlaoded to the faveo server provide executable permission to the script by running the below command inside the directory where the script is present.
```
chmod +x basic-troubleshoot.sh
```
- To execute the script run the below command from the directory where the script is present.
```
sudo ./basic-troubleshoot.sh
```

- Once the script is executed it will prompt for the faveo root directory which is a needed value for the script to work.
- It will prompt for the below
```
Enter Faveo root directory path (e.g., /var/www/faveo) /var/www/faveo is the default press enter to use the default value:
```

- When prompted above input the following details.

- If your Faveo root directory is the default as below Just press Enter:

```
/var/www/faveo
```
- Otherwise, enter the correct path manually.

Example:
```
/var/www/html/faveo
```

- Next, Select an Option from the Menu 

- You will be prompted to select one of the following:

```
Select an option to run:
1) Run all checks
2) SSL Check
3) System Info
4) Service Status
5) Faveo Info
6) Cron Jobs
7) Supervisor Jobs
8) Logged-in Users
9) Billing Connection
10) Root-Owned Files in Faveo Directory
11) Check if Required Ports are Open
12) Firewall check
0) Exit
Enter your choice [0-12]: 
```

- To check all information at once, select option **1**. You will see full diagnostic output in sequence.
- If you want to run a single specific check instead of all, select the relevant option by passing optinon number from the menu when prompted.  [Click here for more detail](#single-specific-check)
- After selecting option 
- Below is the output of option ((1) Run all checks)

```
Welcome to User_Name
Date: Thursday 19 June 2025 10:57:40 AM IST
--------------------------------------------------
Faveo APP_URL from .env: faveo.helpdesk.com
Enter domain for SSL check (leave empty to use APP_URL):
```
The script will automatically read the APP_URL from the .env file inside faveo root directory.

After entering, it will display information like SSL validation, System Info, Service Status, Faveo Application Info, Cron Jobs (takes 5–10 sec), Csf, Supervisor Jobs, Logged-in Users, Billing Connection Check, Root-Owned Files/Folders in the Faveo directory, Port Availability Check (It will prompt for additional ports, if needed enter custome ports) If you need add n number of custome ports separated by comma; if not, just press Enter. After entering, it will display Port Availability and Firewall Check.

## Example Full Script Execution Summary
```
root@Faveo:/home/faveo/script# ./basic-troubleshoot.sh 
                                                                                                                         
                                        _______ _______ _     _ _______ _______                                          
                                       (_______|_______|_)   (_|_______|_______)                                         
                                        _____   _______ _     _ _____   _     _                                          
                                       |  ___) |  ___  | |   | |  ___) | |   | |                                         
                                       | |     | |   | |\ \ / /| |_____| |___| |                                         
                                       |_|     |_|   |_| \___/ |_______)\_____/                                          
                                                                                                                         
                              _     _ _______ _       ______ ______  _______  ______ _     _                            
                             (_)   (_|_______|_)     (_____ (______)(_______)/ _____|_)   | |                            
                              _______ _____   _       _____) )     _ _____  ( (____  _____| |                            
                             |  ___  |  ___) | |     |  ____/ |   | |  ___)  \____ \|  _   _)                            
                             | |   | | |_____| |_____| |    | |__/ /| |_____ _____) ) |  \ \                             
                             |_|   |_|_______)_______)_|    |_____/ |_______|______/|_|   \_)                            
                                                                                                                         
                                                                                                                         
Enter Faveo root directory path (e.g., /var/www/faveo) /var/www/faveo is the default press enter to use the default value: 
Select an option to run:
1) Run all checks
2) SSL Check
3) System Info
4) Service Status
5) Faveo Info
6) Cron Jobs
7) Supervisor Jobs
8) Logged-in Users
9) Billing Connection
10) Root-Owned Files in Faveo Directory
11) Check if Required Ports are Open
12) Firewall check
0) Exit
Enter your choice [0-12]: 1
Welcome to Faveo
Date: Thursday 19 June 2025 11:18:54 AM IST
--------------------------------------------------
Faveo APP_URL from .env: faveo.helpdesk.com
Enter domain for SSL check (leave empty to use APP_URL): 
No domain entered. Using APP_URL domain: faveo.helpdesk.com
SSL Check for: faveo.helpdesk.com
SSL is Valid

System Info:
Distro: Ubuntu 22.04.5 LTS
Kernel: 6.8.0-60-generic
Uptime: up 1 hour, 54 minutes
Load Avg: 1.22 0.92 0.97
vCPU Cores: 8
Memory: 8.0Gi used / 15Gi
Disk: 170G used / 320G (57%)

Service Status:
apache2: active (Since: Thu 2025-06-19 09:24:44 IST)
apache2 version: Server version: Apache/2.4.63 (Ubuntu)

httpd version: Server version: Apache/2.4.63 (Ubuntu)

mysql: active (Since: Thu 2025-06-19 09:24:50 IST)
mysql version: mysql  Ver 8.0.42 for Linux on x86_64 (MySQL Community Server - GPL)

mariadb version: mysql  Ver 8.0.42 for Linux on x86_64 (MySQL Community Server - GPL)

redis: active (Since: Thu 2025-06-19 09:24:43 IST)
redis version: Redis server v=6.0.16 sha=00000000:0 malloc=jemalloc-5.2.1 bits=64 build=a3fdef44459b3ad6

redis-server: active (Since: Thu 2025-06-19 09:24:43 IST)
redis-server version: Redis server v=6.0.16 sha=00000000:0 malloc=jemalloc-5.2.1 bits=64 build=a3fdef44459b3ad6

supervisord version: Not found or not applicable

supervisor: active (Since: Thu 2025-06-19 09:24:43 IST)
supervisor version: Not found or not applicable

php8.2-fpm: active (Since: Thu 2025-06-19 09:24:43 IST)
php8.2-fpm version: 

php-fpm version: 

cron: active (Since: Thu 2025-06-19 09:24:43 IST)
cron version: Not found or not applicable

crond version: Not found or not applicable

meilisearch: active (Since: Thu 2025-06-19 09:24:43 IST)
meilisearch version: meilisearch 1.14.0

nginx version: basic-troubleshoot.sh: line 162: nginx: command not found

node version: v22.16.0

npm version: 10.9.2

csf version: 

Faveo Application Info:
URL: https://faveo.helpdesk.com
Plan: Faveo Enterprise Pro
Version: v9.4.1

Cron Jobs:
Cron jobs for user: www-data
* * * * * /usr/bin/php /var/www/faveo/artisan schedule:run 2>&1
artisan commands found:
* * * * * /usr/bin/php /var/www/faveo/artisan schedule:run 2>&1
Estimating last run time from system logs:
Jun 19 11:14:01 Fvaeo CRON[80731]: (www-data) CMD (/usr/bin/php /var/www/faveo/artisan schedule:run 2>&1)
Jun 19 11:15:01 Fvaeo CRON[81560]: (www-data) CMD (/usr/bin/php /var/www/faveo/artisan schedule:run 2>&1)
Jun 19 11:16:01 Fvaeo CRON[82303]: (www-data) CMD (/usr/bin/php /var/www/faveo/artisan schedule:run 2>&1)
Jun 19 11:17:01 Fvaeo CRON[83040]: (www-data) CMD (/usr/bin/php /var/www/faveo/artisan schedule:run 2>&1)
Jun 19 11:18:01 Fvaeo CRON[83801]: (www-data) CMD (/usr/bin/php /var/www/faveo/artisan schedule:run 2>&1)
Jun 19 11:19:01 Fvaeo CRON[84840]: (www-data) CMD (/usr/bin/php /var/www/faveo/artisan schedule:run 2>&1)

Cron jobs for user: root
None

Supervisor Jobs:
faveo-Horizon                    RUNNING   pid 4060, uptime 1:54:24

Logged-in Users:
2

Billing Connection Check:
Billing connection is working.

Root-Owned Files/Folders in Faveo Directory:
No files/folders owned by root found.

Port Availability Check:
Enter any additional ports to check (comma-separated, or press Enter to skip): 

Checking Port 80 (HTTP)
Port 80 is open internally (listening).

Checking Port 6379 (Redis)
Port 6379 is open internally (listening).

Checking Port 443 (HTTPS)
Port 443 is open internally (listening).

Checking Port 3306 (MySQL)
Port 3306 is open internally (listening).

Firewall Check:
UFW is installed.
Status: inactive


--------------------------------------------------
Script by Faveo Helpdesk | support@faveohelpdesk.com
Execution complete.
```

## Single Specific Check

To run a single specific check instead of all, select the relevant option number from the menu when prompted

Selecting a Single Specific Check

You will be prompted to select one of the following:
```
Select an option to run:
1) Run all checks
2) SSL Check
3) System Info
4) Service Status
5) Faveo Info
6) Cron Jobs
7) Supervisor Jobs
8) Logged-in Users
9) Billing Connection
10) Root-Owned Files in Faveo Directory
11) Check if Required Ports are Open
12) Firewall check
0) Exit
Enter your choice [0-12]: 
```

To run a specific check individually, enter the number of the option you want to execute.

- Enter **2** to check SSL Validity

Output After Running the Script

```
Welcome to Faveo
Date: Thursday 19 June 2025 01:03:37 PM IST
--------------------------------------------------
Faveo APP_URL from .env: faveo.helpdesk.com
Enter domain for SSL check (leave empty to use APP_URL): 
```

If your root directory is the default (/var/www/faveo), just press Enter. The script will automatically read the APP_URL from the .env file inside the faveo root directory.

Example Output

```
Enter your choice [0-12]: 2
Welcome to Faveo
Date: Thursday 19 June 2025 1:18:54 PM IST
--------------------------------------------------
Faveo APP_URL from .env: faveo.helpdesk.com
Enter domain for SSL check (leave empty to use APP_URL): 
No domain entered. Using APP_URL domain: faveo.helpdesk.com
SSL Check for: faveo.helpdesk.com
SSL is Valid
--------------------------------------------------
Script by Faveo Helpdesk | support@faveohelpdesk.com
Execution complete.
```

- Enter **3** to check System Info

It displays System OS, uptime, memory usage, CPU, disk statistics, etc..

Example Output

```
Enter your choice [0-12]: 3
Welcome to Faveo
Date: Thursday 19 June 2025 1:00:54 PM IST
--------------------------------------------------
System Info:
Distro: Ubuntu 22.04.5 LTS
Kernel: 6.8.0-60-generic
Uptime: up 3 hours, 45 minutes
Load Avg: 0.92 0.72 0.86
vCPU Cores: 8
Memory: 9.2Gi used / 15Gi
Disk: 170G used / 320G (57%)
--------------------------------------------------
Script by Faveo Helpdesk | support@faveohelpdesk.com
Execution complete.
```

- Enter **4** to check Service Status and Service Version

Shows version and status of services like Apache, MySQL, PHP, Php-fpm, Redis, etc.

Example Output

```
Enter your choice [0-12]: 4
Welcome to Faveo
Date: Thursday 19 June 2025 1:10:54 PM IST
--------------------------------------------------
Service Status:
apache2: active (Since: Thu 2025-06-19 09:24:44 IST)
apache2 version: Server version: Apache/2.4.63 (Ubuntu)

httpd version: Server version: Apache/2.4.63 (Ubuntu)

mysql: active (Since: Thu 2025-06-19 09:24:50 IST)
mysql version: mysql  Ver 8.0.42 for Linux on x86_64 (MySQL Community Server - GPL)

mariadb version: mysql  Ver 8.0.42 for Linux on x86_64 (MySQL Community Server - GPL)

redis: active (Since: Thu 2025-06-19 09:24:43 IST)
redis version: Redis server v=6.0.16 sha=00000000:0 malloc=jemalloc-5.2.1 bits=64 build=a3fdef44459b3ad6

redis-server: active (Since: Thu 2025-06-19 09:24:43 IST)
redis-server version: Redis server v=6.0.16 sha=00000000:0 malloc=jemalloc-5.2.1 bits=64 build=a3fdef44459b3ad6

supervisord version: Not found or not applicable

supervisor: active (Since: Thu 2025-06-19 09:24:43 IST)
supervisor version: Not found or not applicable

php8.2-fpm: active (Since: Thu 2025-06-19 09:24:43 IST)
php8.2-fpm version: 

php-fpm version: 

cron: active (Since: Thu 2025-06-19 09:24:43 IST)
cron version: Not found or not applicable

crond version: Not found or not applicable

meilisearch: active (Since: Thu 2025-06-19 09:24:43 IST)
meilisearch version: meilisearch 1.14.0

nginx version: basic-troubleshoot.sh: line 162: nginx: command not found

node version: v22.16.0

npm version: 10.9.2

csf version: 

--------------------------------------------------
Script by Faveo Helpdesk | support@faveohelpdesk.com
Execution complete.
```

- Enter **5** to check Faveo Info

Displays Faveo APP_URL, plan, and version

Example Output
```
Enter your choice [0-12]: 5
Welcome to Faveo
Date: Thursday 19 June 2025 1:15:04 PM IST
--------------------------------------------------
Faveo Application Info:
URL: https://siva.localhost
Plan: Faveo Enterprise Pro
Version: v9.4.1
--------------------------------------------------
Script by Faveo Helpdesk | support@faveohelpdesk.com
Execution complete.
```

- Enter **6** to check Cron Jobs with last few run time logs (takes 5–10 sec)

Example Output

```
Enter your choice [0-12]: 6
Welcome to Faveo
Date: Thursday 19 June 2025 1:14:30 PM IST
--------------------------------------------------
Cron Jobs:
Cron jobs for user: www-data
* * * * * /usr/bin/php /var/www/faveo/artisan schedule:run 2>&1
artisan commands found:
* * * * * /usr/bin/php /var/www/faveo/artisan schedule:run 2>&1
Estimating last run time from system logs:
Jun 19 13:44:02 Faveo CRON[179717]: (www-data) CMD (/usr/bin/php /var/www/faveo/artisan schedule:run 2>&1)
Jun 19 13:45:01 Faveo CRON[180511]: (www-data) CMD (/usr/bin/php /var/www/faveo/artisan schedule:run 2>&1)
Jun 19 13:46:01 Faveo CRON[181271]: (www-data) CMD (/usr/bin/php /var/www/faveo/artisan schedule:run 2>&1)
Jun 19 13:47:01 Faveo CRON[181997]: (www-data) CMD (/usr/bin/php /var/www/faveo/artisan schedule:run 2>&1)
Jun 19 13:48:01 Faveo CRON[182718]: (www-data) CMD (/usr/bin/php /var/www/faveo/artisan schedule:run 2>&1)
Jun 19 13:49:01 Faveo CRON[183467]: (www-data) CMD (/usr/bin/php /var/www/faveo/artisan schedule:run 2>&1)

Cron jobs for user: root
None

--------------------------------------------------
Script by Faveo Helpdesk | support@faveohelpdesk.com
Execution complete.
```

- Enter **7** to check Supervisor jobs running status

```
Enter your choice [0-12]: 7
Welcome to Faveo
Date: Thursday 19 June 2025 1:20:04 PM IST
--------------------------------------------------
--------------------------------------------------
Supervisor Jobs:
faveo-Horizon                    RUNNING   pid 4060, uptime 4:28:25

--------------------------------------------------
Script by Faveo Helpdesk | support@faveohelpdesk.com
Execution complete.
```

- Enter **8** to check SSH Logged-in Users

Example Output
```
Enter your choice [0-12]: 8
Welcome to Faveo
Date: Thursday 19 June 2025 1:22:04 PM IST
--------------------------------------------------
Logged-in Users:
2

--------------------------------------------------
Script by Faveo Helpdesk | support@faveohelpdesk.com
Execution complete.
```

- Enter **9** to check Faveo Billing Connection

Example Output

```
Enter your choice [0-12]: 9
Welcome to Faveo
Date: Thursday 19 June 2025 1:25:08 PM IST
--------------------------------------------------
Billing Connection Check:
Billing connection is working.


--------------------------------------------------
Script by Faveo Helpdesk | support@faveohelpdesk.com
Execution complete.
```

- Enter **10** to check Root-Owned Files in Faveo Directory

Example Output (No files/folders owned by root found)

```
Enter your choice [0-12]: 10
Welcome to Faveo
Date: Thursday 19 June 2025 1:30:04 PM IST
--------------------------------------------------
Root-Owned Files/Folders in Faveo Directory:
No files/folders owned by root found.


--------------------------------------------------
Script by Faveo Helpdesk | support@faveohelpdesk.com
Execution complete.
```

Example Output  (Root-Owned Files in Faveo Directory (Issue))

```
Enter your choice [0-12]: 10
Welcome to Faveo
Date: Thursday 19 June 2025 1:31:02 PM IST
--------------------------------------------------
Root-Owned Files/Folders in Faveo Directory:
The following items are owned by root:
/var/www/faveo/bootstrap
/var/www/faveo/bootstrap/cache
/var/www/faveo/bootstrap/cache/.gitignore
/var/www/faveo/bootstrap/cache/packages.php
/var/www/faveo/bootstrap/cache/services.php
/var/www/faveo/bootstrap/app.php
/var/www/faveo/bootstrap/autoload.php
/var/www/faveo/storage
/var/www/faveo/storage/debugbar
/var/www/faveo/storage/debugbar/.gitignore
/var/www/faveo/storage/logs
/var/www/faveo/storage/logs/.gitignore
/var/www/faveo/storage/framework
/var/www/faveo/storage/framework/cache
/var/www/faveo/storage/framework/cache/ec
/var/www/faveo/storage/framework/cache/ec/ff
/var/www/faveo/storage/framework/cache/ec/ff/ecffb309874da7e47b1214d6d10704f86a011afd
/var/www/faveo/storage/framework/cache/3a
/var/www/faveo/storage/framework/cache/3a/d1
/var/www/faveo/storage/framework/cache/3a/d1/3ad1fe5763fe6b9bec0a3b5d65d7bc21a47fb6fa
/var/www/faveo/storage/framework/cache/3b
/var/www/faveo/storage/framework/cache/3b/0f
/var/www/faveo/storage/framework/cache/3b/0f/3b0f92f916e4c88725b9dec8b8660187d9db458c
/var/www/faveo/storage/framework/cache/.gitignore
/var/www/faveo/storage/framework/cache/c4
/var/www/faveo/storage/framework/cache/c4/ca
/var/www/faveo/storage/framework/cache/c4/ca/c4ca0a81abf6e7054b095951a267d4644e82f773
/var/www/faveo/storage/framework/cache/6c
/var/www/faveo/storage/framework/cache/6c/c4
/var/www/faveo/storage/framework/cache/6c/c4/6cc4c5c421b9926ff0e1d615b50acd0354cda171
/var/www/faveo/storage/framework/cache/e1
/var/www/faveo/storage/framework/cache/e1/15
/var/www/faveo/storage/framework/cache/e1/15/e11523c5ff23fc1600aca2d8ee5adb542c5ce4b3
/var/www/faveo/storage/framework/views
/var/www/faveo/storage/framework/views/1577e048ef1518d750e5ce1a8465ab0a.php
/var/www/faveo/storage/framework/views/cbc69d7628b7d63f2c7f45f383a8a2ec.php
/var/www/faveo/storage/framework/views/9ee12cbe9019ffa581bbee531368b6cb.php
--------------------------------------------------
Script by Faveo Helpdesk | support@faveohelpdesk.com
Execution complete.
```

This indicates that files in the bootstrap/ and storage/ directories are incorrectly owned by root.
These folders must be owned by the web server user (usually www-data) to allow the application to write logs, cache, and perform scheduled tasks.


To Fix This, Follow the Steps

Run the following command to correct file ownership:

```
chown -R www-data:www-data /var/www/faveo/ Enter the file/folder which are not owned by www-data 
```

- Enter **11** to check Check if Required Ports are Open

The script will automatically check commonly required Faveo ports: 80 (HTTP), 443 (HTTPS), 3306 (MySQL), and 6379 (Redis)

To check additional ports, enter them as comma-separated values when prompted

```
Enter any additional ports to check (comma-separated, or press Enter to skip): 25,587,9000
```
This is useful when you want to verify if services like SMTP, Horizon, Meilisearch, etc., are reachable.

Example Output

```
Enter your choice [0-12]: 11
Welcome to Siva-LWS
Date: Thursday 19 June 2025 02:07:19 PM IST
--------------------------------------------------
Port Availability Check:
Enter any additional ports to check (comma-separated, or press Enter to skip): 

Checking Port 80 (HTTP)
Port 80 is open internally (listening).

Checking Port 6379 (Redis)
Port 6379 is open internally (listening).

Checking Port 443 (HTTPS)
Port 443 is open internally (listening).

Checking Port 3306 (MySQL)
Port 3306 is open internally (listening).
--------------------------------------------------
Script by Faveo Helpdesk | support@faveohelpdesk.com
Execution complete.
```

- Enter **12** to check Firewall

Example Output
```
Enter your choice [0-12]: 12
Welcome to Faveo
Date: Thursday 19 June 2025 02:36:24 PM IST
--------------------------------------------------
Firewall Check:
UFW is installed.
Status: active

     To                         Action      From
     --                         ------      ----
[ 1] 6568/tcp                   ALLOW IN    Anywhere                  
[ 2] 7070/udp                   ALLOW IN    Anywhere                  
[ 3] 102.106.35.21 1194/tcp     ALLOW OUT   Anywhere                   (out)
[ 4] 8080/tcp                   ALLOW IN    Anywhere                  
[ 5] 443                        ALLOW IN    102.106.35.21           
[ 6] 443                        ALLOW IN    Anywhere                  
[ 7] 22/tcp                     ALLOW IN    Anywhere                  
[ 8] 32156/tcp                  ALLOW IN    Anywhere                  
[ 9] 6568/tcp (v6)              ALLOW IN    Anywhere (v6)             
[10] 7070/udp (v6)              ALLOW IN    Anywhere (v6)             
[11] 8080/tcp (v6)              ALLOW IN    Anywhere (v6)             
[12] 443 (v6)                   ALLOW IN    Anywhere (v6)             
[13] 22/tcp (v6)                ALLOW IN    Anywhere (v6)             
[14] 32156/tcp (v6)             ALLOW IN    Anywhere (v6)             

--------------------------------------------------
Script by Faveo Helpdesk | support@faveohelpdesk.com
Execution complete.
```
