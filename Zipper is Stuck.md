## Task:
As an elite cyber investigator, you receive an anonymous tip about a suspicious network activity .  Unravel the encrypted messages, follow the digital trail, and work with your team to retrieve the confidential information. The message has a 3 digit lock.

[Capture Zipper](Resources%20provided/capture%20Zipper)

## Points : 200 (~100)

## Solution:
* __Open the capture packet using Wireshark__
* __Filter the http packets out. Here we are able to find a packet that carries an application which is compressed.__

![sort by http](https://github.com/ikshvaku01/KPMG_CTF/assets/60730655/b6991c91-5a8c-44b4-a5fd-3cd600fde723)
___


* __Investigating the packet further, we are able to see flag.txt written in the ASCII dump__

![hehehe](https://github.com/ikshvaku01/KPMG_CTF/assets/60730655/289177fb-cabd-4a9f-954d-ea353ad1b2c1)
___


* __Export the packet bytes under Media type__

![export as packet bytes](https://github.com/ikshvaku01/KPMG_CTF/assets/60730655/7f6f1b77-7e1b-485e-b43d-fc6a7c9ba5ed)
___


* __If we use file command on the exported file, we can see its a zip file__

![pog](https://github.com/ikshvaku01/KPMG_CTF/assets/60730655/8fe5d666-a9b1-47dc-a079-975ae0a0670e)
___


* __One way to crack the password is by using: https://www.lostmypass.com/file-types/zip/__

![kuduroooo](https://github.com/ikshvaku01/KPMG_CTF/assets/60730655/d79331e0-022c-454f-974b-8a7cfcf900cc)
___


* __It returns the password and then unlock the zip with the same__


![ida](https://github.com/ikshvaku01/KPMG_CTF/assets/60730655/5950b9bd-ead1-4a98-988f-69abeb8e75d4)
___

