---
title: พัฒนาโมบายแอปด้วย Cordova
description: สร้างและพัฒนาเว็บแอปให้เป็นโมบายแอปด้วย Cordova
date: 2022-09-25
tags: [cordova, android, java, javascript, html, css]
---

Cordova เป็นเฟรมเวิร์คสำหรับพัฒนาเว็บแอปให้เป็นโมบายแอปด้วย Javascript, HTML และ CSS โดยเขียนโค้ดชุดเดียวก็สามารถทำให้ใช้งานได้ทุกแพลตฟอร์ม ไม่ว่าจะเป็น Android, iOs, Windows, Electron แต่ในบทบันทึกจะมีแนะนำเพียงระบบ Android กับ Electron เพราะระบบอื่น ๆ ผู้บันทึกไม่ได้ทดสอบ เนื่องจากไม่มีอุปกรณ์สำหรับทดสอบนั่นเอง :grin:

## ขั้นตอน

- [ติดตั้งสิ่งจำเป็นในการพัฒนา Cordova][installation]  
  - [java-jdk8][java-jdk]  
  - [android-sdk][android-sdk]
  - [gradle][gradle]
  - [cordova][cordova]
- [สร้างโปรเจคใหม่][getstart]
- [Emulator Test][nox-test]
- [Build APK Package][run-build]

[installation]: cordova-installation.md
[cordova]: cordova-installation.md#cordova
[android-sdk]: cordova-installation.md#android-sdk
[java-jdk]: cordova-installation.md#java-jdk8
[gradle]: cordova-installation.md#gradle-build-tool-เครื่องมือจัดการโครงสร้างโปรเจคอัตโนมัติสำหรับ-java-และอื่น-ๆ
[getstart]: README.md
[nox-test]: README.md
[run-build]: README.md
