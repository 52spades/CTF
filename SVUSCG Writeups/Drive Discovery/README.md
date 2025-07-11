# Drive Discovery

## Description
![Challenge Description](Screenshots/DriveDiscDescription.png)
## File

[drivediscovery.zip](drivediscovery.zip)  
MD5 Hash: 2fe5817bdb806bbb2bd4fbc36d10a63f
<br>

## Writeup

We first want to check our zip file's MD5 hash with `md5sum drivediscovery.zip` to ensure integrity.

![Checking MD5 hash in command line](Screenshots/DDiscMD5.png)

Looks good!
<br>
<br>

Unzip the file with `unzip drivediscovery.zip`

![.zip Unzipped Contents](Screenshots/unzip1.png)
<br>
<br>

The DriveDiscoveryDescriptionPUBLIC.txt suggests that the flag has likely been deleted.

![DriveDiscoveryDescriptionPUBLIC.txt](Screenshots/DriveDiscREADME.png)
<br>
<br>

The .001 file likely packed the hidden thumb drive, so we unzip it with 7zip using  `7zip x nothinginterestinghere.001`.

![.001 Unzipped Contents](Screenshots/DriveDiscUNZIP.png)
<br>
<br>

The directory "Secrets" contains a hint for us: the flag is likely encoded in Base64.

![Secrets](Screenshots/Secrets.png)
<br>
<br>

Since the flag has been deleted, it is likely not in the recycle bin, but instead in the '[SYSTEM]' directory. 

![SYSTEM directory](Screenshots/SYSTEM.png)
<br>
<br>

The $MFT, or Master File Table, file maintains records of all files, so if the flag has been deleted, it can still be found here and will be encoded in base64.  

Using `strings $MFT`, we find a line of base64 encoded text. This is the flag.

![Encoded flag](Screenshots/flag.png)

Decode  with `cat $MFT | grep U1ZC | base64 -d`.  

The flag is: `SVBRG{d3l373d_n07_f0r60773n_283029382}`!






