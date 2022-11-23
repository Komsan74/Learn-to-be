---
title: เปิด Google Sheet ให้เคอร์เซอร์เลื่อนไปอยู่แถวล่างสุดด้วย Apps Script
description: Kms74 Nov 23, 2022 
website:
    gist: https://gist.github.com/Komsan74/766dd0fe097461d76a4de4d4a0481b85
    github: https://github.com/Komsan74/Learn-to-be/blob/main/google-sheet/sheet-open-to-last-row.md
    gitbook: https://kms74.gitbook.io/learn-to-be/google-sheet/sheet-open-to-last-row
---

## บทเล่า

เวลาที่เราเปิด Google Sheet ทุกครั้ง เคอร์เซอร์จะมาเริ่มต้นอยู่ที่เซล `A1` เสมอ ถ้าข้อมูลไม่เยอะมาก ก็ถือว่าไม่ยุ่งยากอะไรหากผู้ใช้ต้องการจะเพิ่มแถวข้อมูลเข้าไปใหม่ ก็เพียงแค่เลื่อนเม้าส์ไปยังเซลที่ต้องการ แต่ถ้าหากว่าในสเปรดชีตนั้นมีแถวข้อมูลจำนวนมาก อาจจะหลายร้อยหลายพันบรรทัด การจะเลื่อนเม้าส์ลงไปก็ดูจะไม่ค่อยสะดวก ดังนั้นบทบันทึกนี้จะแนะนำการแก้ปัญหาดังกล่าว

## วิธีการ
* **วิธีที่ 1** การใช้ **Shortcut Key**
  * เมื่อเปิดไฟล์กูลเกิ้ลชีตขึ้นมาเคอร์เซอร์จะอยู่ที่เซล `A1` ให้เรากดปุ่ม `[Ctrl]` + `[↓]` (Arrow Down) พร้อมกัน เมื่อปล่อยมือเคอร์เซอร์จะเลื่อนไปที่เซล `A` แถวล่างสุดทันที
 
* **วิธีที่ 2** การใช้ **Apps Script**
  * เมื่อเปิดไฟล์กูลเกิ้ลชีตขึ้นมา ให้กดเมนู `ส่วนขยาย > Apps Script`
  * เพิ่มสคริปต์นี้ลงไปใน `code.gs`
  ```js
  function onOpen() {
    goToLastRow();
  }

  function goToLastRow() {
    var sheet = SpreadsheetApp.getActiveSpreadsheet().getActiveSheet();  
    var lastRow = sheet.getRange("A:A").getValues().filter(String).length;  
    var lastCell = sheet.getRange(lastRow, 1);

    sheet.setCurrentCell(lastCell).activate();
  }
  ```
  * กดบันทึก ปิดและเปิดไฟล์กูลเกิ้ลชีตขึ้นใหม่ จะเห็นว่าเคอร์เซอร์จะอยู่ที่เซล `A` ในแถวล่างสุด โดยที่เราไม่ต้องเลื่อนเมาส์หา

## บทสรุป

ในบทบันทึกนี้เป็นเพียงเทคนิคหนึ่ง ที่จะช่วยให้ผู้ศึกษาใช้ลดความยุ่งยากในการเลื่อนหาแถวล่าสุดของข้อมูล ช่วยให้ลดเวลาในการทำงานให้สั้นลง ด้วยการใช้ประโยชน์จาก Shortcut Key ในกูลเกิ้ลชีต และการเลือกใช้งาน Apps Script อย่างมีประสิทธิภาพ

## บทบันทึกที่เกี่ยวข้อง

* [Google Sheet](README.md)

## ความคิดเห็น

[![github-gist-button](https://user-images.githubusercontent.com/52767363/191145099-9f4a51a2-35cc-495f-82e1-284d769a9052.png)][comment]

[comment]: https://gist.github.com/Komsan74/766dd0fe097461d76a4de4d4a0481b85