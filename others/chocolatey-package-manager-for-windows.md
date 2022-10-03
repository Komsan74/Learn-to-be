---
title: Chocolatey Package Manager สำหรับวินโดวส์
description: Package Manager For Windows และรายการโปรแกรมที่จำเป็นเมื่อลงวินโดวส์ใหม่
data: 2022-09
tags: [chocolatey, windows, package, manager, choco]
---

สำหรับบทบันทึกนี้จะแนะนำตัวจัดการแพ็กเกจสำหรับวินโดวส์ หรือตัวช่วยลงโปรแกรมผ่านบรรทัดคำสั่ง (Command Line) เพื่อช่วยลดเวลาในการค้นหาไฟล์ติดตั้งโปรแกรมต่าง ๆ ไม่ต้องเปิดเบราเซอร์เข้าเว็บโน้นสลับกับเว็บนี้ กว่าจะได้ไฟล์ติดตั้งสักตัวมาใช้งาน Chocolatey ถือเป็นตัวเลือกที่ดีที่จะนำมาแนะนำ

## Installation
- ศึกษาข้อมูลและวิธีการติดตั้งผ่าน [เว็บไซต์ทางการ Chocolatey][choco-site]

[choco-site]: https://chocolatey.org/

- ติดตั้งผ่าน Power Shell ในโหมด Administrator :man_pilot: พิมพ์คำสั่งนี้ลงไป (หรือคัดลอกไปวาง)

```powershell
Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
```
รอให้ระบบทำการติดตั้งจนเสร็จเรียบร้อย (อาจใช้เวลาสักครู่)

- ตรวจสอบการติดตั้ง พิมพ์คำสั่งนี้ลงไปในหน้าต่าง Power Shell

```powershell
choco
```

Chocolatey จะแสดงหมายเลขเวอร์ชั่นที่ติดตั้งในเครื่องออกมาแบบนี้

![choco-check-install](https://user-images.githubusercontent.com/52767363/192127427-7909ac38-0e28-4374-8d87-fda2d55746b1.png)

เป็นอันเสร็จเรียบร้อย ปิดหน้าต่าง Power Shell หรือพิมพ์คำสั่ง `exit` แล้วกด `Enter` หลังจากนี้ก็สามารถใช้งาน Chocolatey ผ่าน Power Shell หรือ CMD ได้แล้ว

## โปรแกรมที่ควรลงหลังติดตั้งวินโดวส์ใหม่ (สำหรับผู้ศึกษาการพัฒนาซอฟต์แวร์)
จะใช้วิธีการติดตั้งด้วยวิธีเดียวกันทั้งหมดคือ เปิดหน้าต่าง `cmd.exe` ในโหมด Administrator แล้วพิมพ์คำสั่งที่แนะนำลงไป

- ### 7zip 
  เครื่องมือแตกและบีบอัดไฟล์
  - ศึกษาและดาวน์โหลดไฟล์ติดตั้งจาก [เว็บไซต์ทางการ 7zip][7zip-site]
  
  [7zip-site]: https://www.7-zip.org/
  
  - ติดตั้งผ่าน Command Line
  
```sh
choco install 7zip -y
```

- ### Brave Browser 
  เครื่องมือท่องเว็บที่รวดเร็วและปลอดภัยสามารถบล็อคโฆษณาได้หมดจด
  - ศึกษาและดาวน์โหลดไฟล์ติดตั้งจาก [เว็บไซต์ทางการ Brave Browser][brave-site]
  
  [brave-site]: https://brave.com/
  
  - ติดตั้งผ่าน Command Line
  
```sh
choco install brave -y
```

- ### Git 
  เวอร์ชั่นคอนโทรลที่ใช้ในการพัฒนาซอฟต์แวร์
  - ศึกษาและดาวน์โหลดไฟล์ติดตั้งจาก [เว็บไซต์ทางการ Git SCM][git-site]
  
  [git-site]: https://git-scm.com/
  
  - ติดตั้งผ่าน Command Line
```sh
choco install git -y
```

- ### Visual Studio Code 
  โค้ดเอดิเตอร์ที่เหมาะสำหรับพัฒนาแอปพลิเคชั่นทั่วไป
  - ศึกษาและดาวน์โหลดไฟล์ติดตั้งจาก [เว็บไซต์ทางการ VS Code][vscode-site]
  
  [vscode-site]: https://code.visualstudio.com/
  
  - ติดตั้งผ่าน Command Line

```sh
choco install vscode -y
```  
- ### Node JS
  Node Package Manager
  - ศึกษาและดาวน์โหลดไฟล์ติดตั้งจาก [เว็บไซต์ทางการ Node JS](https://nodejs.org/en/)

  - ติดตั้งผ่าย Command Line

```sh
choco install nodejs -y
```

- ### ค้นหาแพ็กเกจเพิ่มเติม
  - ในกรณีที่ต้องการค้นหารายชื่อแพ็กเกจต่าง ๆ ว่ามีอยู่ใน `Repository` ของ `Chocolatey` หรือไม่ สามารถทำได้โดยเรียกใช้คำสั่ง

```sh
choco search <ชื่อแพ็กเกจ>
```
Chocolatey ก็จะแสดงรายการแพ็กเกจเกี่ยวกับ `<ชื่อแพ็กเกจ>` ที่เราค้นหาออกมาเท่าที่จะมีรายการนั้นปรากฏอยู่ใน `Repository` ของ `Chocolatey` นั่นเอง และเราสามารถเลือกที่จะ `install` แพ็กเกจเหล่านั้นได้ตามอัธยาศัย

ที่บันทึกมาทั้งหมดนี้ยังไม่ใช่ทั้งหมดที่อยากแนะนำ หากจะมีกล่าวถึงอีกเรื่อย ๆ ในบทบันทึกอื่น ๆ หวังว่าจะมีประโยชน์สำหรับผู้ศึกษาที่เข้ามาอ่านบทบันทึกนี้

## ความคิดเห็น

[![github-gist-button](https://user-images.githubusercontent.com/52767363/191145099-9f4a51a2-35cc-495f-82e1-284d769a9052.png)][comment]

[comment]: https://gist.github.com/Komsan74/67fd6644c3aacdb882947bef2b813144
