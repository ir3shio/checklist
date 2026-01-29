# Android‌ ‌App‌ ‌Traffic‌ ‌Decryption‌ ‌&‌ ‌Defeat‌ ‌Certificate‌ ‌Pinning‌ 
‌
‌
## Prerequisites:‌ ‌
- Android Emulator
  - For Windows: Nox‌ ‌Player (Make Sure to Enable Root Access)
  - For Linux: Genymotion
- OpenSSL
- Burp Suite

----
## Burp Setup:
1. **Proxy** ->  **Options** -> **Import / export CA certificate** -> Select **Certificate in DER format** in Export & Save it as **burp.der**
2. Add Proxy Listner -> Add port 8081 -> select **All interfaces**
----
## OpenSSL‌ ‌(Hash‌ ‌Certificate):‌ ‌
Android‌ ‌apparently‌ ‌refers‌ ‌to‌ ‌certs‌ ‌by‌ ‌a‌ ‌hashed‌ ‌file‌ ‌name.‌ ‌We‌ ‌need‌ ‌to‌ ‌generate‌ ‌this.‌‌ ‌
‌1. Open Terminal(Linux/MacOS)/Command Prompt(Windows) 
1. Type‌ ‌the‌ ‌following:‌ ‌`openssl‌ ‌x509‌ ‌-inform‌ ‌DER‌ ‌-subject_hash_old‌ ‌-in‌ ‌burp.der` ‌‌
![Screenshot from 2023-01-15 21-16-16](https://user-images.githubusercontent.com/91581651/212551110-e6ac9f4c-0626-40b0-887b-8538283e93e3.png)
1. Now,‌ ‌take‌ ‌the‌ ‌number/hash‌ ‌that‌ ‌the‌ ‌command‌ ‌spit‌ ‌out,‌ ‌such‌ ‌as‌ ‌“9a5ba575”‌ ‌and‌ ‌rename‌‌ your‌ ‌burp.der‌ ‌file‌ ‌by‌ ‌running‌ ‌the‌ ‌command:‌ ‌`mv‌ ‌burp.der‌ ‌9a5ba575.0` ‌Make‌ ‌sure‌ ‌you‌ ‌append‌ ‌the‌ ‌.0‌ ‌(dot‌ ‌zero)‌ ‌file‌ ‌extension‌ ‌to‌ ‌your‌ ‌hash‌ ‌when‌ ‌renaming‌ ‌the‌‌
file.‌ ‌
----
## Emulator 
1. Open your Android’s Settings.
1. Tap Wi-Fi.
1. Tap and hold the Wi-Fi Network Name.
1. Select Modify Network.
1. Click Advanced Options.
1. Tap Manual. Change your proxy’s settings.
1. At the place of hostname enter Host Machine IP 
    - In Linux, type ifconfig in terminal.
    - In Windows, type ipconfig in Command Prompt 
1. In Port enter `8081`.
1. Tap Save.‌
----
## ADB‌ ‌(Install‌ ‌Certificate):‌ ‌
_This‌ ‌step‌ ‌is‌ ‌to‌ ‌push‌ ‌the‌ ‌new‌ ‌certificate‌ ‌into‌ ‌the‌ ‌system‌ ‌trusted‌ ‌CA‌ ‌store.‌_
1. In Terminal,Type Following Commands:‌ ‌
```
su
mount -o rw,remount /
```
3. Now‌ ‌open‌ ‌a‌ ‌new‌ ‌Tab ‌leaving‌ ‌the‌ ‌ADB‌ ‌bridge‌ ‌window‌ ‌open.‌ ‌ ‌
4. Navigate‌ ‌to‌ ‌folder‌ ‌which‌ ‌contains‌ ‌the‌ ‌new‌ ‌cert‌ ‌with‌ ‌hashed‌ ‌name.‌ ‌
5. In Terminal,Type Following Command:‌
```
adb push 9a5ba575.0 /system/etc/security/cacerts
```
8. If‌ ‌all‌ ‌went‌ ‌well,‌ ‌you are good to go.Close‌ ‌down‌ ‌all the terminal.‌ ‌
‌
#‌# Permission Setup
```
su
setenforce 0
setprop persist.sys.tango_zygote32.start 0
setprop persist.device_config.runtime_native.usap_pool_enabled false
```
