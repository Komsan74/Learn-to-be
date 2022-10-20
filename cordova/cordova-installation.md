---
title: พัฒนาโมบายแอปด้วย Cordova
description: Kms74 Sep 24, 2022
tags: [cordova, android, java, javascript, html, css]
---

การจะพัฒนาเว็ปแอปให้การเป็นโมบายแอปพลิเคชั่นด้วย Cordova นั้น จำเป็นอย่างยิ่งที่จะต้องมีเครื่องมือช่วยเหลือที่นอกเหนือจาก Text/Code Editor แล้ว หากผู้ศึกษาใช้ระบบปฏิบัติการวินโดวส์ ก็สามารถดำเนินการติดตั้งเครื่องมือที่จำเป็นตามบทบันทึกนี้ได้ แต่หากว่าผู้ศึกษาใช้งานระบบปฏิบัติการอื่น ก็อาจเทียบเคียงการติดตั้งเครื่องไม้เครื่องมือเหล่านี้จากระบบปฏิบัติการของผู้ศึกษาได้โดยตรง

## สิ่งที่ต้องมี

- Node.js
- Java-JDK8
- Android-SDK
- Gradle
- Cordova
- Android Emulator

เครื่องมือทั้งหมดที่ว่ามา ผู้บันทึกจะแนะนำการติดตั้งผ่านทาง Command Line เพราะสะดวกดี ไม่ต้องไปเปิดเว็บค้นหาสิ่งโน้นทีสิ่งนี้ที ให้เสียเวลามากมายนัก หากผู้ศึกษาไม่ถนัดการใช้งาน Command Line ก็สามารถกดลิงค์ไปศึกษาและดาวน์โหลดเครื่องมือแต่ละอย่างจากเว็บทางการได้โดยตรงเช่นกัน แต่ผู้บันทึกจะไม่ขอกล่าวถึงขั้นตอนเหล่านั้นในบทบันทึกนี้ สิ่งแรกที่ต้องมีคือต้องติดตั้ง Chocolatey เอาไว้ในเครื่องด้วย หากยังไม่เคยติดตั้งให้กลับไปอ่าน [Chocolatey Package Manager สำหรับวินโดวส์][choco-install] หากติดตั้งพร้อมแล้วก็เริ่มขั้นต่อไปกันเลย :rocket:

[choco-install]: ../others/chocolatey-package-manager-for-windows.md

## Node.js
- ดาวน์โหลดและติดตั้งผ่าน [เว็บไซต์ทางการ Node.js][nodejs]

[nodejs]: https://nodejs.org/en/

- ติดตั้งผ่าน Command Line เปิด cmd.exe เลือกโหมด Administrator พิมพ์คำสั่ง

```sh
choco install nodejs -y
```

## Java-JDK8
- ดาวน์โหลดและติดตั้งผ่าน [เว็บไซต์ทางการ Java-JDK8][jdk8]

[jdk8]: https://www.oracle.com/java/technologies/javase/javase8u211-later-archive-downloads.html

- ติดตั้งผ่าน Command Line เปิด cmd.exe เลือกโหมด Administrator พิมพ์คำสั่ง

```sh
choco install jdk8 -y
```

## Android-SDK
- ดาวน์โหลดและติดตั้งผ่าน [เว็บไซต์ทางการ Android SDK][sdk]

[sdk]: https://developer.android.com/studio#command-tools

- ติดตั้งผ่าน Command Line เปิด cmd.exe เลือกโหมด Administrator พิมพ์คำสั่ง

```sh
choco install android-sdk -y
```

- ติดตั้ง SDK build tools, SDK platform, SDK platform tools เปิด cmd.exe เลือกโหมด Administrator พิมพ์คำสั่ง
```sh
sdkmanager "platforms;android-28" "platform-tools" "build-tools;28.0.3"
```

## Gradle Build Tool เครื่องมือจัดการโครงสร้างโปรเจคอัตโนมัติสำหรับ Java และอื่น ๆ
- ดาวน์โหลดและติดตั้งผ่าน [เว็บไซต์ทางการ Gradle Build Tool][gradle]

[gradle]: https://gradle.org/

- ติดตั้งผ่าน Command Line เปิด cmd.exe เลือกโหมด Administrator พิมพ์คำสั่ง
```sh
choco install gradle -y
```

- หรือติดตั้งผ่านคำสั่ง `npm` ของ Node.js ที่ได้ติดตั้งไว้ก่อนแล้ว

```sh
npm install -g gradle
```

## Cordova
- ดาวน์โหลดและติดตั้งผ่าน [เว็บไซต์ทางการ Cordova][cordova]

[cordova]: https://cordova.apache.org/

- ติดตั้งผ่าน Command Line เปิด cmd.exe เลือกโหมด Administrator พิมพ์คำสั่ง

```sh
npm install -g cordova
```

## Android Emulator

ตรงส่วนนี้ผู้บันทึกขอให้เป็นไปตามความชอบของแต่ละบุคคลก็แล้วกันไม่ว่าจะใช้ Android Virtual Device (AVD) จาก Android SDK โดยตรง หรือจะใช้พวกโปรแกรมจำลองอย่าง [LDplayer][ld], [Noxplayer][nox] หรือ [Genymotion][geny] ก็ได้หมด แต่ที่ผู้บันทึกใช้อยู่จะเป็น [Noxplayer Emulator][nox] ดังนั้นจะไม่แนะนำวิธีติดตั้งไว้ในบทบันทึกนี้

[ld]: https://th.ldplayer.net/
[nox]: https://th.bignox.com/
[geny]: https://www.genymotion.com/

## ความคิดเห็น

[![github-gist-button](https://user-images.githubusercontent.com/52767363/191145099-9f4a51a2-35cc-495f-82e1-284d769a9052.png)][comment]

[comment]: https://gist.github.com/Komsan74/4f4754c2e53db6e7601afb8b7b731de2
