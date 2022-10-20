---
title: ปรับปรุงฟังก์ชั่น Google Apps Script ให้ยืดหยุ่นต่อการใช้งาน
description: Kms74 Oct, 2022
date: 2022-09
tags: [GAS, Google Apps Script, apps script, google-sheet, google sheet, sheet]
---

## เล่านำ

"พี่ ๆ ร้านพี่มีสินค้าตัวนี้ไหม" 

คำถามลอย ๆ จากลูกค้า ทำให้เราต้องเปิดเว็บแอปที่เคยสร้างไว้ขึ้นมาดู ก็พบว่าตอนนี้เว็บแอปของเรามีเพียงแค่ [`ตารางฐานข้อมูลลูกค้า`](deploy-web-app.md) เท่านั้น ยังไม่สามารถทำการค้าใด ๆ กับรายชื่อลูกค้าที่เราได้บันทึกเอาไว้เลย ดังนั้นสิ่งที่ต้องทำต่อไป ก็คือการสร้าง `ตารางฐานข้อมูลสินค้า` เพื่อจะได้มีรายการสินค้าไว้ทำการค้ากับลูกค้าได้นั่นเอง

## สิ่งที่ต้องทำ

- ### [ส่วน Google Sheet](#google-sheet)
    
    - ชีตข้อมูลสำหรับบันทึกตารางสินค้า ให้ชื่อว่า `[tbl]Product`

- ### [ส่วน Apps Script](#google-apps-script)
    
    -แก้ไขฟังก์ชั่นใน `code.gs` ให้สามารถรองรับการ `CRUD` ข้อมูลได้หลายชีต

- ### [ส่วน HTML](#html)
    
    - ปรับปรุงการแสดงผลในหน้า `index.html`

- ### [ส่วน Javascript](#javascript)
    
    - ปรับฟังก์ชั่นควบคุมการสื่อสารระหว่าง `backend ` กับ `frontend`

## Google Sheet

จัดเตรียมชีตข้อมูลในไฟล์ `GAS Database Demo Sheets` ที่เราได้สร้างไว้ตั้งแต่บทบันทึก [การพัฒนาเว็บแอปด้วย Google Apps Script ร่วมกับ Google Sheet](google-apps-script-google-sheet.md) ทำการเพิ่มชีตใหม่ ตั้งชื่อชีตว่า `[tbl]Product` โดยให้มีฟิลด์ข้อมูลดังนี้

- ProductID เก็บข้อมูล รหัสสินค้า

- ProductName เก็บข้อมูล รายชื่อสินค้า

- UnitPrice เก็บข้อมูล ราคาสินค้าต่อหน่วย

- Discount เก็บข้อมูล ส่วนลดสินค้า

![apps-script-edit-code-0](https://user-images.githubusercontent.com/52767363/192676983-03a21a49-eee6-472f-b0ec-cad3527752b6.png)

## Google Apps Script

ทำการแก้ไขสคริปต์ใน `code.gs` ที่เคยทำไว้ ให้สามารถเรียกใช้งานได้หลายสเปรดชีต
    
    - CREATE 
    
    เพิ่มตัวระบุชื่อตารางข้อมูลในฟังก์ชั่น ``
    - READ
    - UPDATE
    - DELETE

## HTML

## Javascript

## บทบันทึกที่เกี่ยวข้อง
> - [การพัฒนาเว็บแอปด้วย Google Apps Script ร่วมกับ Google Sheet](google-apps-script-google-sheet.md) 
> - [นำเว็บแอปที่สร้างจาก Google Apps Script เสร็จแล้วไปใช้งาน](deploy-web-app.md)

### แสดงความคิดเห็นได้ที่ :point_right: [![github-gist-button](https://user-images.githubusercontent.com/52767363/191145099-9f4a51a2-35cc-495f-82e1-284d769a9052.png)](https://gist.github.com/Komsan74/c92f0d19f98aaba9982a3c2a4bcce265)
