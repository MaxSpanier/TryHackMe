# user flag
found a webserver with sweet rice  
found this vulnerability `https://www.exploit-db.com/exploits/40718`  
downloaded the sql backup  
found `username - manager` and a password hash `42f749ade7f9e195bf475f37a44cafcb`  
cracked the hash with hashcat `hashcat -m password.hash /usr/share/wordlists/rockyou.txt`  
`42f749ade7f9e195bf475f37a44cafcb:Password123`  
found out that the login page for sweet rice applications is `/content/as`  
logged in with `manager - Password123`  
used this script to upload a php reverse shell to the server `https://www.exploit-db.com/exploits/40716`  
found the user flag in `/home/itguy/user.txt`

<details>
<summary>user.txt</summary>
THM{63e5bce9271952aad1113b6f1ac28a07}
</details> 

# root flag
found out that www-data is allowed to run `/home/itguy/backup.pl` with root privelegeas    
that script runs another script called `/etc/copy.sh`  
that script is just a reverse shell where you just need to insert your own ip and port  
find out that there is no vim or vi or nano or any other text editor installed -_-  
copy the content of the file into the file with the changed ip and port `echo the file with the new ip and port to the same file`   
setup a netcat listener and run the file with `sudo /usr/bin/perl /home/itguy/backup.pl`  
get an instant root shell  
found root.txt in `/root/root.txt`

<details>
<summary>root</summary>
THM{6637f41d0177b6f37cb20d775124699f}
</details>  