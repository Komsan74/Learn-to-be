---
title: การสร้าง React Starter Project ขึ้นใหม่
description: create-react-app เพื่อสร้างโปรเจคใหม่
date: 2022-10-05
tags: [create, react, app, create-react-app, npm, npx, javascript, jsx]
---

## บทเล่า

ก่อนอื่นผู้บันทึกขอชี้แจงคร่าว ๆ ก่อนว่า [React][react] นั้นไม่ใช่ภาษาโปรแกรม แต่เป็น ui-framework ที่พัฒนาขึ้นมาโดยทีมงาน [Facebook][facebook] และเป็นที่นิยมในกลุ่มผู้พัฒนาเว็บแอปเป็นอย่างมาก ซึ่งผู้บันทึกเองจะไม่ขอลงรายละเอียดลึกซึ้ง (เพราะผู้บันทึกก็ไม่ได้มีความรู้ลึกซึ้งในเรื่องนี้) :grin: เชื่อว่าผู้เข้ามาศึกษาน่าจะรู้จัก และมีพื้นฐานเกี่ยวกับ [React][react] มาพอสมควรบ้างแล้ว

## เตรียมพ้อม

ในการเริ่มต้นสร้าง [React Project][react] ในบทบันทึกนี้ จะใช้ตัวช่วยติดตั้งแพ็กเกจ [Node Packgage Manager][node] หรือ [npm][node] ลองตรวจสอบดูว่าเครื่องของเรามีการติดตั้งไว้เรียบร้อยหรือยัง ด้วยการเปิดหน้าต่าง `cmd.exe` (สำหรับวินโดวส์) พิมพ์คำสั่งดังนี้แล้วกด `Enter `

```sh
node -v
```

ถ้ามี [Node Packgage Manager][node]  ติดตั้งไว้อยู่แล้ว ระบบจะแสดงหมายเลขเวอร์ชั่นออกมา แต่หากยังไม่ได้ติดตั้ง ก็กลับไปดูวิธีการติดตั้งได้จากบทบันทึก [Chocolatey Package Manager สำหรับวินโดวส์](../../others/chocolatey-package-manager-for-windows.md#node-js) ทำการติดตั้งให้เรียบร้อยแล้วดำเนินการขั้นต่อไป

## Get Started

### create-react-app

ทีมงาน `Facebook` ได้จัดเตรียมแม่แบบโครงสร้าง [React Starter Project][react] เอาไว้ให้แล้วใน [Node Package][create-react-app] ชื่อว่า [creat-react-app][create-react-app] เราสามารถเริ่มสร้างโปรเจคด้วยแม่แบบโครงสร้างนั้นผ่าน Command Line ด้วยคำสั่งดังนี้

```sh
npx create-react-app myapp
```

โดยแทนที่ `myapp` ด้วยชื่อแอปโปรเจคที่เราต้องการสร้าง รอสักครู่ [Node Package Manager][node] จะทำการติดตั้ง [React Starter Templet][react] ลงในโฟลเดอร์ `/myapp` หรือโฟลเดอร์ที่เป็นชื่อแอปโปรเจคที่เรากำหนดไว้ในคำสั่งข้างต้นนั่นเอง

![creat-react-app-0](https://user-images.githubusercontent.com/52767363/193970691-a911d5b9-7b95-40a9-be13-8d222bda9d5e.png)

รอต่อไปจนกระทั่งปรากฏข้อความ `Happy hacking!` 

![creat-react-app-1](https://user-images.githubusercontent.com/52767363/193970698-05543c79-1b22-42ec-8245-47eff2a8eb9c.png)

### ทดสอบผลการติดตั้ง

ทำการย้ายพาธคำสั่งไปที่โฟลเดอร์แอปโปรเจคที่เพิ่งสร้างขึ้นมา

```sh
cd myapp
```

ทดลองสั่ง `run`

```sh
npm start
```

[Node Package Manager][node] จะทำการจำลองเซิร์ฟเวอร์ขึ้นมาแบบนี้ (สังเกตจะแสดงที่อยู่เว็บแอปและพอร์ตมาให้)

![creat-react-app-2](https://user-images.githubusercontent.com/52767363/193973076-46fcd765-ec12-426f-ac03-6ae0ebe12137.png)

และถ้าไม่มีขั้นตอนอะไรผิดพลาด เมื่อพิมพ์ที่อยู่ตามที่ [Node Package Manager][node] กำหนดมาให้ลงในเว็บเบราเซอร์ ในตัวอย่างคือ `http://localhost:3000`  ก็จะแสดงโลโก้ [React][react] ขึ้นมาแบบนี้ เป็นอันเสร็จเรียบร้อย

![creat-react-app-3](https://user-images.githubusercontent.com/52767363/193973081-418e7e92-11b0-4c96-912e-45fb2ae0d836.png)
  
### ติดตั้ง React App ด้วยวิธีอื่น

นอกจากคำสั่ง `npx` ข้างต้น เรายังสามารถทำการติดตั้ง [React Starter Project] ด้วยคำสั่งอื่น ๆ ได้อีก เป็นต้นว่า

  - ใช้คำสั่ง [npm][node] พิมพ์คำสั่ง

```sh
npm init react-app myapp
```

  - ใช้คำสั่ง [yarn][yarn] พิมพ์คำสั่ง

```sh
yarn create react-app myapp
```

หรือจะสร้างโฟลเดอร์ขึ้นมาเองดื้อ ๆ เลยก็ยังได้ โดยอ้างอิงโครงสร้าง React App ที่กำลังจะกล่าวถึง

### โครงสร้าง React App

ทำการเปิดแอปโปรเจคด้วยโค้ดเอดิเตอร์ที่ถนัด (สำหรับบทบันทึกตัวอย่างนี้จะใช้ [VS CODE][vscode] เป็นโค้ดเอดิเตอร์) ถ้ายังอยู่ในหน้าต่าง `cmd.exe` ผู้ศึกษาสามารถเปิด [VS CODE][vscode] ได้ด้วยคำสั่ง

```sh
code .
```

หรือจะเปิดจากสตาร์ทเมนูของวินโดวส์ตามปกติก็ได้เช่นกัน สำหรับผู้ศึกษาที่ต้องการใช้งาน [VS CODE][vscode] แต่ยังไม่ได้ทำการติดตั้ง สามารถศึกษาวิธีติดตั้งได้จากบทบันทึก [Chocolatey Package Manager สำหรับวินโดวส์](../../others/chocolatey-package-manager-for-windows.md#visual-studio-code) ได้เลย

เมื่อเปิดเข้ามาแล้วจะเห็นโครงสร้าง React App ของเราโดยหลัก ๆ จะเป็นดังนี้

```text
myapp/  
  node_modules/  
  public/
    index.html
    favicon.ico
  src/
    App.css
    App.js
    App.test.js
    index.css
    index.js
    logo.svg
  package.json
  README.md
```

ดูใน [VS CODE][vscode] ก็จะเห็นโครงสร้างประมาณแบบนี้

![creat-react-app-4](https://user-images.githubusercontent.com/52767363/193976478-906da3d2-4f44-431f-bed6-75a61ff572a4.png)

หลังจากนี้เราสามารถเพิ่มหรือแก้ไข `component` ต่าง ๆ ในโฟลเดอร์ `src` เพื่อแสดงผลเว็บแอปให้เป็นไปตามความต้องการของเราได้ โดยจะนำมาแนะนำในบทบันทึกต่อ ๆ ไป

## บทบันทึกที่เกี่ยวข้อง

  - [Chocolatey Package Manager สำหรับวินโดวส์](chocolatey-package-manager-for-windows.md#vs-code)

## ความคิดเห็น

[![github-gist-button](https://user-images.githubusercontent.com/52767363/191145099-9f4a51a2-35cc-495f-82e1-284d769a9052.png)][comment]

[comment]: https://gist.githubusercontent.com/Komsan74/72a6e6330a19d5622e8f873a67d5f094

[react]: https://reactjs.org/
[facebook]: https://developers.facebook.com/
[node]: https://nodejs.org/
[create-react-app]: https://www.npmjs.com/package/create-react-app
[vscode]: https://code.visualstudio.com/
[yarn]: https://yarnpkg.com/