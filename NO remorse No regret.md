## Task :
Agent X intercepts a high-stakes call between gangsters "Shadow" and "Viper." Critical intel lies within, but excessive background noise corrupts the message. Your mission should you choose to accept it is to decode the audio using the tools at your disposal.

[Secret_Message](Resources%20provided/Secret_Message.mp3)

## Points: 200

## Solution:

We are given a `.mp3` file for this challenge. It contains some beeps with other noises over it. On opening the file with audacity, we can see it has two channels. One channel has a morse code and the other has noise.

![mp3 file](https://github.com/shashankk90/Writeups/blob/master/KPMG/files/images/No%20remorse,%20No%20regret.png)

I extracted the file only channel and put it into an [online morse decoder](https://morsecode.world/international/decoder/audio-decoder-adaptive.html). It decoded to `RB.GY/3TPVV`
This is the link to a zip file on the internet. On extracting the zip file, we get an image. The image contains the flag.

```sh
[ssk@arch kic]$ unzip flag.zip 
Archive:  flag.zip
  inflating: flag.jpg                
[ssk@arch kic]$ strings flag.jpg | grep KPMG
"KPMG_CTF{3ND_I$_H3R3}" 
```