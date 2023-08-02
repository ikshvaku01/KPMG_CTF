## Task:
There are no blatant injection points or vulnerable forms to exploit. Instead, the key to progress lies in understanding the intricacies of the web application's inner workings.

## Points: 150 

## Solution:
Firstly, we see that there is a /login.php file
The comments suggest that there is a "secret" GET Parameter, And also a file at "/config/iamsecure.txt"

We have to use a simple local file technique.
we could do https://kicyber-c32073fa97a7-hackme-1.chals.io/login.php?secret=../../config/iamsecure.txt
which gives us the credentials encoded in base64 (which could be decoded with https://gchq.github.io/CyberChef/#recipe=From_Base64('A-Za-z0-9%2B/%3D',true,false)), We get 11 chars as password, so we have to bruteforce the last character (using tools like wfuzz and seclists/Fuzzing/alphanum-case-extra.txt)

Login with correct credentials and get the flag.