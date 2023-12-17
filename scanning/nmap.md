# Nmap

## Preferred scan
```
nmap -p 1-65535 -sV -sS -T4 <ip>
```

## Quick scan
```
nmap -T4 -F <ip>
```

## Intense scan
```
nmap -T4 -A -v <ip>
```

## Intense scan, all ports
```
nmap -p 1-65535 -T4 -A -v <ip>
```

## Slow comprehensive scan
```
nmap -sS -sU -T4 -A -v -PE -PP -PS80,443 -PA3389 -PU40125 -PY -g 53 \
    --script "default or (discovery and safe)" <ip>
```
