# user.txt

found an apache server that runs a vulnerable version (CVE-2020–1938)  
used this github tool `https://github.com/00theway/Ghostcat-CNVD-2020-10487` to read the config file --> `skyfuck:8730281lkjlkjdqlksalks`  
ssh into the machine and found the user.txt in `/home/merlin/user.txt`  

<details>
<summary>user.txt</summary>
</details>

# root.txt

in skyfuck there is a credentials gpg file and a tryhackme.asc file  
download both and use john to crack the password for the file `gpg2john --wordlist=/usr/share/wordlists/rockyou.txt` --> `alexandru`  
on the machine decrypt the file `gpg --decrypt credentials.gpg`  
found the credentials for merlin `merlin:asuyusdoiuqoilkda312j31k2j123j1g23g12k3g12kj3gk12jg3k12j3kj123j`  
`sudo -l` showed that zip can be run a sudo

<details>
<summary>root.txt</summary>
THM{Z1P_1S_FAKE}
</details>