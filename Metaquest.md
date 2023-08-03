## Task :
Welcome to the Mobile MetaQuest CTF challenge, an exhilarating journey through the depths of mobile app mysteries. Dare to take on mind-boggling enigmas concealed within the app's realm. Navigate through obscure territories, uncover hidden fragments, and rise as the ultimate MetaQuest conqueror!

[MetaQuest](Resources%20provided/MetaQuest.apk)

## Points:100

## Solution:
Open the .apk file using any decompiler or use http://www.javadecompilers.com
![image](https://github.com/ikshvaku01/KPMG_CTF/assets/44796607/70c7d7af-064c-4d84-bd8a-1feafbbc8403)
Navigate to "MetaQuest.apk" > "resources" > "AndroidManifest.xml" 
Open the Androidmanifest.xml file, search for "<meta-data android:name="A" android:value="2LeSitU1UigOQWgLHLWinr"/>"
Copy the value and decrypt it using base62 format.
It will show you the encrypted flag. Using https://www.dcode.fr/base62-encoding
KPMG_CTF{M0B!L3_CH@LL3NG3}
