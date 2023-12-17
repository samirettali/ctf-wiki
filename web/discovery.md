# Discovery

## Fuzz
```
ffuf -c -r -recursion -recursion-depth 3 -t 80 -w <wordlist> -o links.csv -of csv -u https://example.com/FUZZ
```

## Find GET parameter
```
ffuf -c -r -recursion -recursion-depth 3 -t 80 -w <wordlist> -o links.csv -of csv -u https://example.com/index.php?FUZZ=test
```

## Tools for finding
* [gau](https://github.com/lc/gau): Find urls in various online archives
* [subjs](https://github.com/lc/subjs): Find js files
* [assetfinder](http://github.com/tomnomnom/assetfinder): Find domains and
    subdomains
* [linkfinder](https://github.com/GerbenJavado/LinkFinder): Find links in js
    files
