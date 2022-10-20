---
title: การใช้ NoxPlayer เป็น Emulator สำหรับทดสอบแอนดรอยด์แอป
description: Kms74 Oct 20, 2022
website:
    gitbook: https://kms74.gitbook.io/learn-to-be/cordova/cordova-use-nox-player
    github: https://github.com/Komsan74/Learn-to-be/blob/main/cordova/cordova-use-nox-player.md
    gist: https://gist.github.com/Komsan74/0f71da46a330da6cbe6d8b803c49da54
---

## บทเล่า

หลายคนประสบปัญหาในการใช้งาน Andriod Virtual Device (AVD) ที่สร้างจาก Android SDK Manager ทำงานช้าบ้าง เปิดไม่ขึ้นบ้าง หรือแม้แต่อาการติด ๆ ดับ ๆ ที่มาจากผู้ใช้อาจตั้งค่าไม่ถูกต้อง หรือทรัพยากรณ์ที่ใช้งานอยู่รองรับได้ไม่ดีก็ตาม แต่เวลาใช้ Android Emulator สำหรับเล่นเกมในพีซี ที่ผลิตกันออกมาหลายค่าย อาทิ MumuPlayer, LDPlayer, NoxPlayer และอีกหลายตัวที่มีผู้นิยมใช้งานอย่างแพร่หลาย กลับพบว่าเครื่องที่ใช้งาน AVD ได้ไม่ค่อยดี เมื่อใช้ Android Emulator Player เหล่านั้นกลับลื่นไหล ดังนั้นบทบันทึกนี้ จะแนะนำการเอา NoxPlayer มาใช้งานเป็น Android Emulator สำหรับทดสอบแอปที่พัฒนาขึ้นด้วย Cordova 

## เตรียมการ

ในบทบันทึกนี้เกี่ยวข้องกับเครื่องมือเครื่องใช้ที่จำเป็นต้องมี ดังนี้

* Node Package Manager (npm)
* Code Editor ที่ถนัด เช่น VS Code
* Java-JDK
* Android-SDK
* Gradle
* Cordova
* NoxPlayer

การติดตั้ง npm, code editor, java-jdk, android-sdk, gradle และ cordova บทบันทึกนี้จะไม่พูดถึง สำหรับผู้ศึกษาที่ยังไม่ได้ทำการติดตั้งรายการใด ก็สามารถทำตามวิธีการติดตั้งจากบทบันทึก [ติดตั้งสิ่งจำเป็นในการพัฒนาแอปด้วย Cordova](https://kms74.gitbook.io/learn-to-be/cordova/cordova-installation)

## ติดตั้ง NoxPlayer

ผู้ศึกษาสามารถดาวน์โหลดไฟลติดตั้งได้จากเว็บไซต์ทางการ [https://th.bignox.com/](https://th.bignox.com/) โดยเลือกเวอร์ชั่น Android ที่ต้องการทดสอบได้ด้วยตัวเอง ปัจจุบันเป็น NoxPlayer เวอร์ชั่น 7.0.3.7 (ตุลาคม 2565) มีถึง `Android 9`  เมื่อดาวน์โหลดเสร็จแล้วก็ดับเบิ้ลคลิกติดตั้งเหมือนโปรแกรมที่ติดตั้งในวินโดวส์พีซีทั่วไป

## ค้นหา Emulator

ในโฟลเดอร์หลักของโปรเจคแอนดรอยด์ที่ทำงานอยู่ ให้เปิดหน้าต่าง cmd.exe หรือหน้าต่าง terminal ใน code editor แล้วพิมพ์คำสั่ง

```sh
cordova run android --list
```

![use-nox-emu-01](https://user-images.githubusercontent.com/52767363/196839699-e843cf8f-bc99-401e-b6b0-367434e65737.png)

> ### Available android devices:
> จะแสดงรายชื่ออุปกรณ์ Android ภายนอก (มือถือ, แท็บเลท) รวมถือ Android Player ต่าง ๆ ที่เชื่อมต่อกับ `adb` แล้ว

> ### Available android virtual devices:
> จะแสดงรายชื่อ AVD ที่สร้างไว้ใน android-sdk-manager ถึงจะไม่ได้เปิดอยู่ก็จะแสดงรายชื่อไว้ตรงนี้

จะเห็นว่ายังไม่มีอุปกรณ์ใด ๆ เชื่อต่ออยู่เลย และคอมพิวเตอร์เครื่องนี้ผู้บันทึกไม่ได้สร้าง AVD ไว้ใช้งานแม้แต่เครื่องเดียว

## เชื่อมต่อ NoxPlayer

เปิดโปรแกรม NoxPlayer ให้รันขึ้นมาก่อน

![use-nox-emu-02](https://user-images.githubusercontent.com/52767363/196844796-f0b3dbe9-957c-4b18-8179-cf0d4526773a.PNG)

จากนั้นในโฟลเดอร์หลักของโปรเจคแอนดรอยด์ เปิดหน้าต่าง cmd.exe หรือหน้าต่าง terminal ใน code editor ก็ได้ พิมพ์คำสั่ง

```sh
tasklist | findstr Nox*
```
จะได้ผลลัพท์ตามนี้

![use-nox-emu-03](https://user-images.githubusercontent.com/52767363/196847133-3da9f7ee-835f-4c8b-b052-b8e5b2090c58.png)

ให้จด PID ของโปรเซส NoxVMHandle.exe ไว้ใช้กับคำสั่งถัดไป

```sh
netstat -aon | findstr [PID]
```

ในภาพข้างต้น PID ก็คือ 10312 พิมพ์ลงในคำสั่งแล้วจะได้ผลลัพท์ดังภาพ ให้มองหาการเชื่อมต่อกับพอร์ตที่ขึ้นต้นด้วย **`62`** ในภาพคือพอร์ต **`62028`** 

![use-nox-emu-04](https://user-images.githubusercontent.com/52767363/196849986-43d2c088-e23e-428f-997d-77bcb2e82b88.png)

ทำการเชื่อมต่อกับ adb (Android Debug Bridge) ด้วยคำสั่ง

```sh
adb connect 127.0.0.1:[port]
```

ถ้า NoxPlayer ยังเปิดอยู่ จะได้ผลลัพท์การเชื่อมต่อแบบนี้

![use-nox-emu-05](https://user-images.githubusercontent.com/52767363/196851781-99ff38d8-e086-43fe-b6ab-b22ab14b5d66.png)

ทำการ [ค้นหา Emulator](#ค้นหา-emulator) อีกที ก็จะได้ผลลัพท์

![use-nox-emu-06](https://user-images.githubusercontent.com/52767363/196852554-31abf951-f64a-4f28-bd67-ca8b86ac1138.png)

## ทดลองรัน Cordova App บน NoxPlayer

ในโฟลเดอร์หลักของโปรเจคแอนดรอยด์ เปิดหน้าต่าง cmd.exe หรือใช้หน้าต่าง terminal ของ code editor ก็ได้ พิมพ์คำสั่ง

```sh
cordova run android --target=[emulator.ip.address:port]
```

ดังนี้

![use-nox-emu-07](https://user-images.githubusercontent.com/52767363/196854793-a700c244-e464-48df-bc26-e80d70d5b806.png)

รอให้ Cordova ทำการคอมไพล์โปรเจค และติดตั้งไฟล์ `.apk` ลงใน NoxPlayer จนเสร็จเรียบร้อยก็จะปรากฏข้อความ `INSTALL SUCCESS` เป็นอันเสร็จ

> :bulb: **Tip:** 
> ถ้ามี Platform Android เพียงแค่ Platform เดียวใน Cordova Project 
> สามารถตัดคำว่า `android` ออกจากบรรทัดคำสั่งได้ 
> ```sh
>   cordova run --target=127.0.0.1:62028
> ```

มาแล้ว

![use-nox-emu-08](https://user-images.githubusercontent.com/52767363/196855278-e1cf8e55-b6d4-400f-9c91-cf2d207d7d8e.PNG)

แอนดรอยด์แอปที่สร้างจาก Cordova จะถูกติตตั้งใน NoxPlayer ให้สามารถเรียกใช้ภายหลังได้แม้จะหยุดเชื่อมต่อ หรือปิด code editor ไปแล้วก็ตาม

![use-nox-emu-09](https://user-images.githubusercontent.com/52767363/196856233-5b9714a4-d3f0-4da7-be31-0b6f5313c8fd.png)

## บทสรุป

บทบันทึกนี้แสดงให้เห็นว่า เราสามารถนำเอา Android Player อย่าง NoxPlayer มาใช้เป็น Android Emulator สำหรับทดสอบแอปแอนดรอยด์ที่พัฒนาขึ้นด้วย Cordova แทนการใช้งาน AVD เพื่อลดข้อจำกัดบางอย่าง แต่ก็ต้องแลกมาด้วยขั้นตอนที่เพิ่มขึ้นอีกเล็กน้อย 

* ข้อดีคือ

> ไม่จำเป็นต้องติดตั้ง Android Studio เพื่อสร้างและรัน AVD

* แต่ก็มีข้อเสียเล็ก ๆ เช่นกันคือ

> เมื่อปิด NoxPlayer ไปแล้ว หากต้องการเปิดขึ้นมาทดสอบอีกครั้ง จะต้องทำการเชื่อมต่อตาม[ขั้นตอน](#เชื่อมต่อ-noxplayer)ที่ว่ามาทั้งหมดใหม่ทุกครั้ง


## บทบันทึกที่เกี่ยวข้อง

* > [ติดตั้งสิ่งจำเป็นในการพัฒนาแอปด้วย Cordova](https://kms74.gitbook.io/learn-to-be/cordova/cordova-installation)

## ความคิดเห็น

[![github-gist-button](https://user-images.githubusercontent.com/52767363/191145099-9f4a51a2-35cc-495f-82e1-284d769a9052.png)][comment]

[comment]: https://gist.github.com/Komsan74/0f71da46a330da6cbe6d8b803c49da54