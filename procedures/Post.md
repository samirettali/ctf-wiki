* Port scan with netcat
```
nc -z -v localhost 1-65535 2>&1 | grep succeeded
```
