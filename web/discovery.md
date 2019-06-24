# Discovery
*
## Find pages and directories with dirsearch
```
dirsearch -t 8 -f -e php,html,asp,js,css,txt,sql -u <url> -w <wordlist>
```

## Find pages and directories with gobuster
```
gobuster -w <wordlist> -u <url>
```

## Find GET parameter
```
wfuzz -c -w <wordlist> "http://site/page?FUZZ='"
```
