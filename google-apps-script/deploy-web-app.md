---
description: Kms74 Sep 22, 2022
---

# นำเว็บแอปที่สร้างจาก Google Apps Script เสร็จแล้วไปใช้งาน

ในการนำเว็บแอปที่เราพัฒนาและทดสอบการทำงานของสคริปต์จนมั่นใจว่ามีความถูกต้องครบถ้วนแล้วออกไปใช้งานจริง เราจะต้องทำการเผยแพร่ให้ออกมาเป็นเว็บแอปอีกครั้ง เพื่อให้รายการที่เราพัฒนาเพิ่มเข้าไปใหม่ ได้ถูกเรียกใช้งานอย่างถูกต้อง ไม่ควรเอาลิงค์สำหรับ [ทดสอบเว็บแอป](https://kms74.gitbook.io/learn-to-be/google-apps-script/form-insert-data-to-google-sheet#undefined-2) ออกไปใช้งานจริง ๆ เพราะเมื่อไหร่ก็ตาม ที่เราเกิดอยากปรับปรุงฟังก์ชั่นภายในโปรเจค Apps Script มันจะส่งผลออกมาที่หน้าทดสอบทันที ซึ่งอาจมีความเสียหายกับเว็บแอปของเราได้ทุกเมื่อ ดังนั้นเราจึงต้องเผยแพร่เว็บแอปออกมาเป็นเวอร์ชั่นที่ _ต้องการกำหนด_ เพื่อจะนำไปใช้งาน

## ขั้นตอน

* จัดการการทำให้ใช้งานได้
* กำหนดค่า
* สร้างเป็นเวอร์ชั่นใหม่
* เผยแพร่เว็บแอป

### จัดการการทำให้ใช้งานได้

หากตอนนี้เรานำลิงค์ที่ได้มาจากบทบันทึกก่อนหน้า&#x20;

> [การพัฒนาเว็บแอปด้วย Google Apps Script ร่วมกับ Google Sheet](https://kms74.gitbook.io/learn-to-be/google-apps-script/google-apps-script-google-sheet)

หัวข้อ [นำเว็บแอปที่เผยแพร่แล้วไปใช้งาน](https://kms74.gitbook.io/learn-to-be/google-apps-script/google-apps-script-google-sheet#undefined-1) ไปวางในเบราเซอร์ตอนนี้ ก็จะยังคงเป็นหน้า `Hello, Google Apps Script` แบบนี้

![hello-google-apps-script](https://561421688-files.gitbook.io/\~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F4vIvqiiVlQnlK8nYzEh9%2Fuploads%2F1Q8iRJxKPXpwL9y1hPsQ%2Fgas-demo-homepage.png?alt=media\&token=9f0dec0a-08b6-4b59-8434-7c0ebca4128c)

คราวนี้หากแน่ใจแล้วว่าสคริปต์ของเราสมบูรณ์พร้อมจะเผยแพร่ให้องค์กรนำไปใช้งาน เราต้อง `จัดการการทำให้ใช้งานได้` เพื่อให้สคริปต์ที่เราปรับปรุงขึ้นใหม่ ถูกบรรจุเข้าในเว็บแอปที่เผยแพร่ไปแล้ว ให้สามารถแสดงผลส่วนที่เราได้เพิ่มเติมเข้าไป **`โดยใช้ลิงค์เดิม`** ดังนี้

* กดเมนู _การทำให้ใช้งานได้ > จัดการการทำให้ใช้งานได้_

![deploy-web-app-1](https://user-images.githubusercontent.com/52767363/191654734-fd7105e7-9737-43e2-b603-fa5a82331c46.png)

เสร็จแล้วจะปรากฏไดอะล็อกการกำหนดค่าให้เราดำเนินการขั้นต่อไป

### กำหนดค่า

* กดที่รูป _ดินสอ_ ตรงส่วนการกำหนดค่า

![deploy-web-app-2](https://user-images.githubusercontent.com/52767363/191654797-3736deec-4984-4b86-a080-84df4f975198.png)

จะเห็นว่าตรง `เวอร์ชั่น` และ `รายละเอียด` สามารถแก้ไขได้แล้ว

### สร้างเป็นเวอร์ชั่นใหม่

* กดตรงเมนู `เวอร์ชั่น`

![deploy-web-app-3](https://user-images.githubusercontent.com/52767363/191654889-753505e4-3c8a-41d0-bc8c-ef2e187022f1.png)

จะแสดงรายการเวอร์ชั่นที่เราเคยปรับปรุงไว้ ตรงนี้เลือกเป็น `เวอร์ชั่นใหม่` เพราะหากเลือกรายการเวอร์ชั่นที่มีอยู่แล้วจะเป็นการเรียกใช้งานเวอร์ชั่นที่เลือก กรณีที่เวอร์ชั่นใหม่เกิดข้อผิดพลาดจะสามารถเรียกคืนเวอร์ชั่นเดิมได้ด้วยวิธีเลือกเวอร์ชั่นเดิมตรงนี้

* ใส่รายละเอียดที่ต้องการเช่น `หมายเลข version หรือ release note` เพิ่อให้เป็นข้อสังเกตุได้ง่ายในอนาคต

![deploy-web-app-4](https://user-images.githubusercontent.com/52767363/191654968-96b490f2-2279-4135-8d9a-d2cc926a4dbe.png)

### เผยแพร่เว็บแอป

* กด `คัดลอก` ตรงเว็บแอป Url และกด `เสร็จสิ้น`

![deploy-web-app-5](https://user-images.githubusercontent.com/52767363/191655001-ad8c6272-bf0b-444f-9326-c9259827c973.png)

ตรงคัดลอกจะกดหรือไม่ก็ได้ หากยังมีลิงค์จากบทบันทึกก่อนหน้า\[^1] หัวข้อ [นำเว็บแอปที่เผยแพร่แล้วไปใช้งาน](https://kms74.gitbook.io/learn-to-be/google-apps-script/google-apps-script-google-sheet#undefined-1) อยู่แล้ว ผู้ศึกษาสามารถใช้ลิงค์เดิมไปใช้งานได้เลย เพราะวิธีนี้จะให้ลิงค์ url เว็ปแอปอันเดิมกับเราเสมอ จึงไม่ต้องไปคอยบอกให้ผู้ใช้งานต้องเปลี่ยนลิงค์ url เวลาที่เว็บแอปมีการอัพเดต ลิงค์ที่ได้จะมีโครงสร้าง url ลงท้ายด้วย `exec` แบบนี้

```
https://script.google.com/macros/s/<!--id-for-apps-script-web-application-->/exec
```

ถ้าผู้ศึกษาได้ทำตามบทบันทึกก่อนหน้า&#x20;

> [สร้างฟอร์มบันทึกข้อมูลจากเว็บแอปลงใน Google Sheet ด้วย Google Apps Script](https://kms74.gitbook.io/learn-to-be/google-apps-script/form-insert-data-to-google-sheet),&#x20;
>
> [อ่านข้อมูลจากกูลเกิ้ลชีตแล้วนำมาแสดงผลที่เว็บแอปด้วย Google Apps Script](https://kms74.gitbook.io/learn-to-be/google-apps-script/read-google-sheet-to-web-app),&#x20;
>
> [แก้ไขข้อมูลกูลเกิ้ลชีตด้วยเว็บแอปผ่าน Google Apps Script](https://kms74.gitbook.io/learn-to-be/google-apps-script/google-apps-script),&#x20;
>
> [ลบข้อมูลกูลเกิ้ลชีตด้วยเว็บแอปผ่าน Google Apps Script](https://kms74.gitbook.io/learn-to-be/google-apps-script/web-app-delete-row-from-sheet)

จนครบทั้งหมดแล้ว ผลลัพท์ที่ได้ก็จะเป็นแบบนี้

![deploy-web-app-6](https://user-images.githubusercontent.com/52767363/191660965-4ebe4690-ad1d-4889-92af-a8b0f93df3d0.PNG)

ถึงตรงนี้ผู้บันทึกหวังว่าผู้ศึกษาจะมีความเข้าใจในการพัฒนาเว็บแอปด้วย Google Apps Script จนสามารถนำไปพัฒนาต่อยอดให้ใช้งานภายในองค์กรของผู้ศึกษาในเบื้องต้นได้ บทบันทึกต่อ ๆ ไปจะแนะนำเพิ่มเติมเกร็ดเล็กเกร็ดน้อยเท่าที่ผู้บันทึกจะนึกได้ หรือมีผู้ศึกษาท่านใดแนะนำข้อสงสัยเข้ามาให้ผู้บันทึกได้นำมาบันทึกเป็นบทอธิบายตอบ :grin:

### แสดงความคิดเห็นได้ที่ :point\_right: [![github-gist-button](https://user-images.githubusercontent.com/52767363/191145099-9f4a51a2-35cc-495f-82e1-284d769a9052.png)](https://gist.github.com/Komsan74/898dc859c0b3a4b01b6859a9ba3ea7cb)
