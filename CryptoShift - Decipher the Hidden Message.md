## Task:
Decrypt the ciphertext encrypted using an unknown cipher. Your mission is to apply various cryptanalysis techniques and pattern recognition to crack the cipher and reveal the hidden Flag.

[Cipher](Resources%20provided/Cipher.txt)

```txt
PKNT vmgrgrvh rm Rmwrz ziv vhgzyorhsvw fmwvi gsv ozdh lu Rmwrz zmw ziv ldmvw zmw nzmztvw (zh gsv xzhv nzb yv) yb vhgzyorhsvw Rmwrzm kiluvhhrlmzoh. Vhgzyorhsvw rm Zftfhg 1993, gsv PKNT vmgrgrvh szev izkrwob yfrog z hrtmrurxzmg xlnkvgrgrev kivhvmxv rm gsv xlfmgib. Glwzb dv lkvizgv uiln luurxvh zxilhh 14 xrgrvh rmxofwrmt rm Zsnvwzyzw, Yvmtzofif, Xszmwrtzis, Xsvmmzr, Tfiftizn, Sbwvizyzw, Qzrkfi, Plxsr, Plopzgz, Nfnyzr, Mlrwz, Kfmv, Ezwlwziz zmw Erqzbzdzwz. Lfi tolyzo zkkilzxs gl hvierxv wvorevib svokh kilerwv ezofv-zwwvw hvierxvh gl xorvmgh.
Lfi wruuvivmgrzgrlm rh wvirevw uiln z izkrw kviulinzmxv-yzhvw, rmwfhgib-gzrolivw zmw gvxsmloltb-vmzyovw yfhrmvhh zwerhlib hvierxvh wvorevivw yb hlnv lu gsv ovzwrmt gzovmgvw kiluvhhrlmzoh rm gsv xlfmgib. Uozt rh PKNT_XGU zmw rm yizxpvg blf szev gl dirgv gsv ulooldrmt gvcg drgslfg hkzxvh zmw hznv xzhv - PKNT RMWRZ XBYVI GVZN. PKNT kiluvhhrlmzoh ziv tilfkvw yb rmwfhgib ulxfh zmw lfi xorvmgh ziv zyov gl wvzo drgs rmwfhgib kiluvhhrlmzoh dsl hkvzp gsvri ozmtfztv. Lfi rmgvimzo rmulinzgrlm gvxsmloltb zmw pmldovwtv nzmztvnvmg hbhgvnh vmzyov gsv wvorevib lu rmulinvw zmw grnvob yfhrmvhh zwerxv gl xorvmgh.PKNT kilerwvh irhp, urmzmxrzo & yfhrmvhh zwerhlib, gzc zmw ivtfozglib hvierxvh, rmgvimzo zfwrg, zmw xliklizgv tlevimzmxv hvierxvh. Yvmtzofif luurxv olxzgrlm rh zg Vnyzhhb Tlou Ormph Yfhrmvhh Kzip Kvyyov Yvzxs Y Yolxp 1hg 2mw Uolli Luu Rmgvinvwrzgv Irmt Ilzw,
```

## Points : 100

## Solution:

Apply Alphabetical substitution which translated too:
```
KPMG entities in India are established under the laws of India and are owned and managed (as the case may be) by established Indian professionals. Established in August 1993, the KPMG entities have rapidly built a significant competitive presence in the country. Today we operate from offices across 14 cities including in Ahmedabad, Bengaluru, Chandigarh, Chennai, Gurugram, Hyderabad, Jaipur, Kochi, Kolkata, Mumbai, Noida, Pune, Vadodara and Vijayawada. Our global approach to service delivery helps provide value-added services to clients.
Our differentiation is derived from a rapid performance-based, industry-tailored and technology-enabled business advisory services delivered by some of the leading talented professionals in the country. Flag is KPMG_CTF and in bracket you have to write the following text without spaces and same case - KPMG INDIA CYBER TEAM. KPMG professionals are grouped by industry focus and our clients are able to deal with industry professionals who speak their language. Our internal information technology and knowledge management systems enable the delivery of informed and timely business advice to clients.KPMG provides risk, financial & business advisory, tax and regulatory services, internal audit, and corporate governance services. Bengaluru office location is at Embassy Golf Links Business Park Pebble Beach B Block 1st 2nd Floor Off Intermediate Ring Road,
```

Solution:
```txt
KPMG_CTF{KPMGINDIACYBERTEAM}
```
