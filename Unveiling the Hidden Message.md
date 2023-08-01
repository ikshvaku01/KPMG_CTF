## Task:
The objective of this challenge is to reverse engineer a given binary executable file and extract flag embedded within the program.
Payload binary executable:

![](payload)

## Points : 100

## Solution:
converted the binary to my system runnable linux environment:

```bash
chmod +x payload
```

Run the binary executable:
```bash
./payload
```
Output:
```bash
Good Luck finding the flag :)
```

output the strings in the binary file:
```bash
strings ./payload > ./payload-data.txt
```

```shell
grep CTF ./payload-data.txt
KPMG_CTF
```
Open text editor to see through `./payload-data.txt` no need to reverse engineer it further .

Flag:
```
KPMG_CTF{e59ff97941044f85df5297e1c302d260}
```