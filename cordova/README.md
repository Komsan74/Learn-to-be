---
title: Cordova
description: สร้างและพัฒนาเว็บแอปให้เป็นโมบายแอปด้วย Cordova
date: 2022-09-24
tags: cordova, android, java, javascript, html
---

# สร้างและพัฒนาโมบายแอปด้วย Cordova

## ขั้นตอน

- [ติดตั้งสิ่งจำเป็นในการพัฒนา Cordova][installation]
  - [cordova][cordova]
  - [android-sdk][android-sdk]
  - [java-jdk][java-jdk]
  - [gradle][gradle]
- [สร้างโปรเจคใหม่][getstart]
- [Emulator Test][nox-test]
- [Build APK Package][run-build]

[installation]: http://link
[cordova]: http://link
[android-sdk]: http://link
[java-jdk]: http://link
[gradle]: http://link
[getstart]: http://link
[nox-test]: http://link
[run-build]: http://link


## สร้างโปรเจคใหม่
```sh
cordova create project_name com.your.app_id app_name
```

## Build APK Package
หลังจากที่สั่ง 
```
cordova build android --release
```
เรียบร้อยแล้ว เราจะได้ไฟล์
```
app-release-unsigned.apk
```
ซึ่งยังใช้งานไม่ได้ เราต้องนำแอพที่ได้ไปสร้างลายเซ็นต์เสียก่อน โดยมีขั้นตอนดังนี้

### สร้าง keystore 
```sh
keytool -genkey -v -keystore my-release-key.jks -keyalg RSA -keysize 2048 -validity 10000 -alias my-alias 
```
### Sign / ใส่ลายเซ็นต์
```sh
jarsigner -verbose -sigalg SHA1withRSA -digestalg SHA1 -keystore my-release-key.jks app-release-unsigned.apk my-alias
```

### zip / บีบอัดแพ็กเกจ
```sh
zipalign -v 4 app-release-unsigned.apk <custom_filename>.apk
```
### verify / ยืนยันความถูกต้องของแพ็กเกจ
```sh
apksigner verify <custom_filename>.apk
```

### Finish
เสร็จแล้วสามารถนำไฟล์ `<custom_filename>.apk` ไปใช้งานหรือเผยแพร่ได้ตามความต้องการ

## Emulator Test
ในที่นี้จะใช้ Nox Emulator เป็นเครื่องจำลองในการทดสอบ ต้องทำการเชื่อมต่อก่อนด้วยคำสั่ง
```adb connect 127.0.0.1:62001```

การหาพอร์ตเชื่อมต่อ Nox Emulator
- พิมพ์คำสั่ง
```tasklist```

- เช็คค่า PID ของ NoxVMHandle.exe จากนั้นพิมพ์คำสั่ง
```netstat -aon | findstr PID```

- หา address 127.0.0.1 ที่เชื่อมพอร์ตที่ขึ้นต้นด้วย 62 จากนั้นพิมพ์คำสั่งเชื่อมต่อ
```adb connect 127.0.0.1:62xxx```

## รองรับแอนดรอยด์ Kitkat
```cordova platform add android@8```

## เปลี่ยนไอคอนแอป
- รูปไอคอนนามสกุล .png ใส่ไว้ที่ /www/img/
- แก้ไขไฟล์ `config.xml`
```xml
<platform name="android">
   <icon src="www/img/icon_name.png" />
</platform>
```

## Toast
> `cordova plugin add cordova-plugin-x-toast`
> usage : `window.plugins.toast.showWithOpitons({...})`

## Gradle
ติดตั้งโดย chocolatey

```choco install gradle```

ทดสอบ footnote[^1]

[^1]: นี่แหละ footnote
