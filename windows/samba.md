# Samba

## Upload file with curl
```
curl --upload-file <file> -u 'DOMAIN\Username' smb://<host>/<share>/
```

## List shares
```
smbclient -L <host>
```

## Enumeration
```
nmblookup -A <host>
smbmap -H <host>
enum4linux <host>
```
