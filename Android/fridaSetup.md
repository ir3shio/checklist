Start Frida Server
```sh
adb shell
su
./data/local/tmp/frida-server
```

List app ID 
```sh
frida-ps -Uai
```

```sh
frida -U -l E:\universalUnpinssl.js -f <APP_ID>
```

To get apk apth
```sh
adb shell pm path <PACKAGE_ID>
```

List package name
```sh
adb shell pm list packages 
```
