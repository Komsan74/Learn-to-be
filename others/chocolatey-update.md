---
title: วิธีอัพเดทโปรแกรมที่ติดตั้งด้วย Chocolatey
description: KMS74 Dec 5, 2022 | ปรับปรุงโปรแกรมที่ติดตั้งผ่าน Chocolatey ให้เป็นเวอร์ชั่นใหม่
website:
  gist: https://gist.github.com/Komsan74/3ff3cb29985f16e27df26abf06a0fe29
  github: https://github.com/Komsan74/Learn-to-be/blob/main/others/chocolatey-update.md
  gitbook: https://kms74.gitbook.io/learn-to-be/others/chocolatey-update
---

## บทเล่า<a name="intro"></a>

เมื่อใช้งานโปรแกรมไประยะหนึ่ง แล้วพบว่าโปรแกรมที่กำลังใช้งานอยู่เป็นเวอร์ชั่นเก่าไม่ทันสมัย หรืออาจจะไม่รองรับกับอัพเดทใหม่ ๆ ของวินโดวส์ หรือแม้แต่กับส่วนขยายใหม่ ๆ ของโปรแกรมนั้น ๆ ที่ออกมาภายหลังจากตอนที่เราได้ติดตั้ง ทำให้เราใช้งานโปรแกรมนั้น ๆ ได้ไม่เต็มประสิทธิภาพ เราจึงควรอัพเดทโปรแกรมเหล่านั้นให้ทันสมัยอยู่เสมอ

## วิธิการ<a name="method"></a>

* ดาวน์โหลดไฟล์ติดตั้งเวอร์ชั่นใหม่จากเว็บไซต์ทางการของโปรแกรมนั้น ๆ (ไม่ได้แนะนำในบทบันทึกนี้)
* อัพเดทผ่าน Chocolatey Package Manager ผ่านบรรทัดคำสั่ง `CMD.exe` ในโหมด `Administrator` พิมพ์คำสั่งดังนี้

```sh
choco update <package_name> -y
```

เช่น หากเราต้องการอัพเดทโปรแกรม Visual Studio Code เราก็ใช้คำสั่งดังนี้

```sh
choco update vscode -y
```

หรือ หากต้องการอัพเดทโปรแกรมที่ติดดั้งด้วย Chocolatey ทั้งหมด ทุกโปรแกรมที่มีการอัพเดทเวอร์ชั่นใหม่แล้ว ก็ใช้คำสั่งดังนี้

```sh
choco update all -y
```

## บทสรุป 

จะเห็นว่าหากเราได้ติดตั้งโปรแกรมใช้งานบนวินโดวส์ด้วย Chocolatey Package Manager แล้วล่ะก็ การจะกระทำการอัพเดทโปรแกรมต่าง ๆ ให้เป็นเวอร์ชั่นใหม่ ก็สามารถกระทำได้ด้วยความสะดวก ไม่ต้องยุ่งยากไปขวนขวานหาเว็บไซต์ทางการเพื่อดาวน์โหลด อย่างไรก็ดี ในการอัพเดทด้วยวิธีนี้ก็ยังจำกัดเฉพาะโปรแกรมที่มีรายชื่อแพกเกจอยู่ใน Repository ของ Chocolatey เท่านั้น (ซึ่งก็มากพอสำหรับการใช้งานทั่วไปบนวินโดวส์)

## บันทึกที่เกี่ยวข้อง

* [แนะนำ Chocolatey Package Manager สำหรับวินโดวส์](chocolatey-package-manager-for-windows.md)

## ความคิดเห็น

[![github-gist-button](https://user-images.githubusercontent.com/52767363/191145099-9f4a51a2-35cc-495f-82e1-284d769a9052.png)][comment]

[comment]: https://gist.github.com/Komsan74/3ff3cb29985f16e27df26abf06a0fe29