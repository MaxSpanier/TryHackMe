# Who wrote the task list? 
nmap showed `ssh` and `ftp` ports are open and `ftp` supports anonymous login  
connect to the server via ftp `ftp IP` - `anonymous`  
get both files  

<details>
<summary>user</summary>
lin
</details>  
  
# Service and password 
use hydra to bruteforce the ssh password `hydra -l lin -P locks.txt ssh://IP`

<details>
<summary>password</summary>
RedDr4gonSynd1cat3
</details>  

# user.txt
<details>
<summary>user.txt</summary>
THM{CR1M3_SyNd1C4T3}
</details>  

# root.txt
checked wich programs lin can run as root with `sudo -l`  
`tar` can be run as root  
got the exploit from `https://gtfobins.github.io/gtfobins/tar/#sudo`

<details>
<summary>root.txt</summary>
THM{80UN7Y_h4cK3r}
</details>  