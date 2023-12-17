## Decompile apk

```
# apktool d -rf my-app.apk
```

## Generate a signing key

```
$ keytool -genkey -v -keystore my-release-key.keystore -alias alias_name -keyalg RSA -keysize 2048 -validity 10000
```

## Recompile the apk
```
$ rm app.apk
$ rm signed-app.apk
$ apktool b -f -d com.myapp
$ jarsigner -verbose -sigalg SHA1withRSA -digestalg SHA1 -keystore my-release-key.keystore com.myapp/dist/com.myapp.apk alias_name
$ zipalign -v 4 com.myapp/dist/com.myapp.apk signed-app.apk
```
