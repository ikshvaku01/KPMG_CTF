## Task :

```
Your mission is to navigate the intricacies of AWS (Amazon Web Services) and obtain the confidential information within.

https://kpmg-ctf.s3.ap-south-1.amazonaws.com/index.html
```

## Points : 150

## Solution:

Change the website url :
https://kpmg-ctf.s3.ap-south-1.amazonaws.com/flag-me-if-you-can.txt

Convert it to get the Flag :
```
KPMG_CTF{5247146a414c3ea2f7bec2c0f9b0664d}
```

<hr>

**A more correct approach is cited [here](https://github.com/shashankk90/Writeups/blob/master/KPMG/Secure%20Storage%20Showdown.md) is mentioned below**

We are given the link to a aws s3 bucket. The `aws-cli` allows us to list all the files available in the bucket. 

```bash
$ aws s3 ls s3://kpmg-ctf --recursive

2023-04-88 22:13:46         42 flag-me-if-you-can.txt
2023-04-08 22:05:00  110824955 hacker.gif
2023-04-88 22:09:82         81 index.html
```
The bucket has a flag file which contains the flag.
```bash
$ aws s3 cp s3://kpmg-ctf/flag-me-if-you-can.txt flag.txt
download: s3://kpmg-ctf/flag-me-if-you-can.txt to ./flag.txt

$ cat flag.txt
KPMG_CTF{5247146a414c3ea2f7bec2c0f9b0664d}
```