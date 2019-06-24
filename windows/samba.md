# Samba

## Upload file with curl
```
curl --upload-file <file> -u 'DOMAIN\Username' smb://<host>/<share>/
```

## List shares
```
smbclient -L <host>
```
