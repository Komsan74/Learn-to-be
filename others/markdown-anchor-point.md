---
title: แก้ปัญหา Heading IDs ภาษาไทยใน GitBook
description: Kms74 Oct 21, 2022
website:
    gitbook: https://kms74.gitbook.io/learn-to-be/others/markdown-anchor-point
    github: https://github.com/Komsan74/Learn-to-be/blob/main/others/markdown-anchor-point.md
    gist: https://gist.github.com/Komsan74/9bb18dc4803bd492e88f395371ac275c
---

## บทนำ<a name="introduction">

ผู้บันทึกมีปัญหาเกี่ยวกับ Heading IDs ในเอกสาร Markdown เวลาที่สร้าง Header เป็นภาษาไทย ผลปรากฏว่าเมื่อนำไปแสดงผลในที่ต่าง ๆ จะใช้เป็น Anchor Point ได้บ้างไม่ได้บ้าง โดยเฉพาะใน GitBook นั้น จะมีข้อผิดพลาดในการใช้งานเกิดขึ้น เช่นว่า

* Heading IDs ที่ควรเป็น `#ภาษาไทย` จะเปลี่ยนเป็น `#undefined` แทน

```
## หัวข้อเรื่อง
...

กลับไปที่ [หัวข้อเรื่อง](#undefined)
```

* แต่ถ้ามี Header เป็นภาษาไทยหลาย ๆ ที่ ก็จะเป็น `#undefined-เลขลำดับ` แทน 

```
## หัวข้อเรื่อง
..
## รายละเอียด
..
## สรุปว่า
..
จะไปที่ [หัวข้อเรื่อง](#undefined)
จะไปที่ [รายละเอียด](#undefined-1)
จะไปที่ [สรุปว่า](#undefined-2)
```

* และ Header ที่เป็นภาษาไทยปนอังกฤษ ระบบของ GitBook จะตัดคำไทยออกทั้งหมดให้เหลือแต่ภาษาอังกฤษ

```
## การเพิ่ม Anchor Point ในเอกสาร Markdown
..
จะไปที่ [การเพิ่ม Anchor Point ในเอกสาร Markdown](#anchor-point-markdown)
```

ซึ่งดูแล้วก็ไม่น่าจะยุ่งยากอะไร ถ้าเราทำเอกสารเพื่อให้แสดงผลกับ GitBook ที่เดียวก็แล้วไป แต่ถ้าเราต้องการนำเอกสารชุดเดียวกัน ไปแสดงผลในหลาย ๆ ที่ การจะมานั่งแก้ Heading IDs ให้ตรงตามความต้องการของแต่ละที่นั้นก็ใช่ว่าจะสะดวกนัก

## แทรก HTML Anchor Point<a name="insert-html-anchor-point"></a>

ปัญหาดังกล่าวสามารถแก้ไขได้ ด้วยการแทรก HTML Anchor Point เข้าไปที่ Header ที่เราคาดว่าจะสร้างปัญหา (เจาะจง Header ที่เป็นภาษาไทย) โดยมีรูปแบบดังนี้

```
## Header name<a name="header-name"></a>
```

เช่นว่า

```
## แทรก HTML Anchor Point<a name="insert-html-anchor-point"></a>
..
จะไปที่ [## แทรก HTML Anchor Point](#insert-html-anchor-point)
```

แบบนี้จะทำให้เราใช้ HTML Anchor Point เป็น Heading IDs ในเอกสาร Markdown ของเราได้โดยไม่เกิดปัญหา เมื่อนำไปแสดงผลในที่ต่าง ๆ ที่ระบบอาจไม่รองรับ Heading IDs ที่เป็นภาษาไทย

> :bulb: **Tip:** เราสามารถตั้งชื่อ Anchor Point ให้กระชับแค่ไหนก็ได้ ไม่จำเป็นต้องให้เหมือนกับ Header (ถ้าไม่กลัวจะสับสน) เช่น
> ```
> ## ตั้งชื่อให้ Anchor Point<a name="a-point-1"></a>
> ..
> จะไปที่ [ตั้งชื่อให้ Anchor Point](#a-point-1)
> ```

## บทสรุป

สำหรับบทบันทึกนี้เป็นการแสดงให้เห็นว่า เราสามารถแก้ปัญหาการสร้าง Header เป็นภาษาไทยหรือภาษาอังกฤษปนไทย จนเกิดปัญหาใช้งาน Heading IDs ไม่ได้กับบางเว็บเพจ ด้วยการแทรก HTML Anchor Point เข้าไปแทนได้ หวังว่าจะพอมีประโยชน์ สำหรับผู้ที่ประสบปัญหาแบบเดียวกัน

## ความคิดเห็น

[![github-gist-button](https://user-images.githubusercontent.com/52767363/191145099-9f4a51a2-35cc-495f-82e1-284d769a9052.png)][comment]

[comment]: https://gist.github.com/Komsan74/9bb18dc4803bd492e88f395371ac275c