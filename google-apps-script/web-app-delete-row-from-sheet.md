---
description: >-
  DELETE Operation
  บทบันทึกนี้จะนำเสนอวิธีลบแถวข้อมูลจากกูลเกิ้ลชีตกรณีที่ไม่ต้องการข้อมูลนั้นแล้ว
---

# ลบข้อมูลกูลเกิ้ลชีตด้วยเว็บแอปผ่าน Google Apps Script

![delete-sheet-0](https://user-images.githubusercontent.com/52767363/191158355-7d5c620b-7c42-4a1a-8b37-0f8ba74a9660.png)

## ขั้นตอน

### ส่วน Apps Script

* เพิ่มฟังก์ชั่น `deleteData(id)` รับหมายเลขไอดีจากไคลเอ็นต์มาค้นหาในชีตแล้วทำการลบข้อมูล

### ส่วน HTML

* ไม่มีรายการเพิ่มเติม

### ส่วน CSS

* ไม่มีรายการเพิ่มเติม

### ส่วน Javascript

* แก้ไขฟังก์ชั่น `getData()` เพิ่มปุ่ม `ลบ` ข้อมูล
* เพิ่มฟังก์ชั่น `accessDelete(index)` เพื่อส่งคำสั่ง `ลบ` ไปให้เซิร์ฟเวอร์

## ส่วน Apps Script

### เพิ่มฟังก์ชั่น `deleteData(id)`

เปิดไฟล์ `code.gs` เพิ่มสคริปต์นี้ลงไป

```javascript
/***************  Delete  ***************/
function deleteData(id) {    
  let last_row = worksheet.getLastRow();
  let status = 0, result;

  // กำหนดช่วงแถวข้อมูลเพื่อค้นหาแถวที่ต้องการลบ
  for(let i = 2; i <= last_row; i++) {  
    // หาแถวที่ต้องการลบจาก id ซึ่งอยู่ในคอมลัมน์ที่ 1
    if(worksheet.getRange(i,1).getValue() == id) {
      // ลบแถวที่มีค่าคอลัมน์ตรงกับค่า id ที่ต้องการลบ
      worksheet.deleteRow(i);
      status = 1;
    }
  }

  // เงื้อนไขการตอบกลับผลลัพท์ส่งให้ไคลเอ็นต์
  if (status == 1) {
    result = "ลบช้อมูล " + id + " เรียบร้อย";
  } else result = "ไม่พบ ID." + id + " ในฐานข้อมูล";
  
  return result;
}
```

ฟังก์ชั่นนี้ถ้าสังเกตจะคล้ายกันกับฟังก์ชั่น `updateData(data)` ในบทบันทึกก่อนหน้า ผู้บันทึกพยายามเขียนฟังก์ชั่นที่ช่วยให้ผู้ศึกษาทำความเข้าใจได้ง่าย และนำไปพัฒนาต่อยอดใช้งานได้จริง ดังนั้นสคริปต์ที่ใช้จึงไม่มีความซับซ้อนมากนัก ถ้าผู้ศึกษาจะงง ก็น่าจะงงคำอธิบายของผู้บันทึกเสียมากกว่า (ฮา) :grin:

ตรง เงื่อนไขการตอบกลับผลสัพท์ส่งให้ไคลเอ็นต์ `if...else` จริง ๆ แล้วไม่ต้องมีก็ได้ ประกาศ `result="ลบเรียบร้อย" ไปเลยก็จบเรื่อง เพราะผู้ใช้ต้องคลิก` ลบ\` ข้อมูลจากตาราง ไม่ได้มานั่งพิมพ์ไอดีเอาเอง จึงไม่มีทางที่จะหาไอดีไม่พบ แต่ผู้บันทึกตั้งใจให้ทำเผื่อไว้ให้คุ้นเคย บทบันทึกต่อ ๆ ไปน่าจะต้องได้ใช้แน่นอน :grin:

## ส่วน Javascript

### แก้ไขฟังก์ชั่น `getData()` เพิ่มปุ่ม `ลบ` ข้อมูล

เปิดไฟล์ `javascript.html` มองหาฟังก์ชั่น `getData(values)` อยู่ในส่วน `*** READ ***` แก้ไขสคริปต์ให้เป็นดังนี้

```javascript
function getData(values) {      
  let json = JSON.parse(values);
  // <table>
  var table = document.createElement("table");
  table.setAttribute("class", "table table-striped table-bordered");
  table.setAttribute("id", "table");  
  // <thead>
  let header = table.createTHead();  
  header.setAttribute("class", "text-center");
  // <tr>
  let row = header.insertRow(0);    
  // <th>
  let headerCell = json.sheets[0]; 
  for (let th in headerCell){      
    row.insertCell().innerHTML = `<b> ${headerCell[th]} </b>`;
  }
  // เพิ่ม column header 'Action' ไว้ท้ายแถว
  row.insertCell().innerHTML = `<b>Action</b>`

  // <tbody>
  let tbody = table.createTBody();
  // <tr>
  let tr;
  for (let i = 1; i < json.sheets.length; i++) {
    tr = tbody.insertRow();
    tr.setAttribute('id', i)
    // <td>      
    for (let td in json.sheets[i]) {          
      tr.insertCell().innerHTML = json.sheets[i][td];
    }
    // เพิ่มปุ่ม แก้ไข + ลบ ที่คอลัมน์ Action
    tr.insertCell().innerHTML = `
        <div class="btn-group" role="group">
          <button type="button" class="btn btn-outline-warning btn-sm" onclick="getTableRow(${i})">แก้ไข</button>
          <button type="button" class="btn btn-outline-danger btn-sm" onclick="accessDelete(${i})">ลบ</button>      
        </div>
        `;      
  }    

  var showData = document.getElementById("showData");
  showData.innerHTML = "";
  showData.appendChild(table);     
} 
```

ส่วนที่เพิ่มเข้ามาก็เป็นตำแหน่งเดียวกันกับบทบันทึกที่แล้ว คือเพิ่มเข้าไปอีกปุ่ม แต่จับทั้งสองปุ่มให้อยู่ใน `group` เดียวกัน ตามรูปแบบที่กำหนดใน `Bootstrap` และกำหนดเหตุการ `onclick="accessDelete(${i})"` เพื่อจับเหตุการเมื่อผู้ใช้คลิก `ลบ` แล้วให้เรียกฟังก์ชั่นมาดำเนินการ แบบนี้

```javascript
tr.insertCell().innerHTML = `
        <div class="btn-group" role="group">
          <button type="button" class="btn btn-outline-warning btn-sm" onclick="getTableRow(${i})">แก้ไข</button>
          <button type="button" class="btn btn-outline-danger btn-sm" onclick="accessDelete(${i})">ลบ</button>      
        </div>
        `;
```

### เพิ่มฟังก์ชั่น `accessDelete(index)` เพื่อส่งคำสั่ง `ลบ` ไปให้เซิร์ฟเวอร์

เพิ่มสคริปต์นี้ลงไปในไฟล์ `javascript.html`

```javascript
/*****************  DELETE  ********************/
function accessDelete(index) {
  let data_row = document.getElementById("table").rows[index].cells;    
  let id = data_row.item(0).innerHTML;

  if (confirm("ต้องการลบข้อมูลลูกค้า id " + id) == true) {
    google.script.run.withSuccessHandler(goAlert).deleteData(id);  
  } else {
    return;
  }   
}
```

เหมือนบทบันทึกที่แล้ว ก็คือรับข้อมูล `data_row` มาจาก `index` ที่ได้จากการคลิกปุ่มมาเก็บไว้ก่อนเพื่อหาหมายเลขไอดีลูกค้า

รับหมายเลขไอดีจาก `data_row` ฟิลด์แรกสุดคือ `0`

```javascript
let id = data_row.item(0).innerHTML;
```

เรียกไดอะล็อก `confirm()` เพื่อให้ผู้ใช้ยืนยันก่อน

```javascript
if (confirm("ต้องการลบข้อมูลลูกค้า id " + id) == true)
```

ถ้ากด `ตกลง` ค่าของไดอะล็อก `confirm` จะเท่ากับ `true` ฟังก์ชั่นจะสั่งให้ดำเนินการคำสั่ง

```javascript
google.script.run.withSuccessHandler(goAlert).deleteData(id);  
```

เพื่อส่งคำขอให้เซิร์ฟเวอร์ดำเนินการลบข้อมูล เมื่อเซิร์ฟเวอร์ลบข้อมูลแล้วจะส่งคำตอบกลับมา ฟังก์ชั่นจะส่งคำตอบไปแสดงผลที่ฟังก์ชั่น `goAlert()` ดังที่เคยแนะนำไว้ในบทบันทึกก่อนหน้านี้

### ทดสอบเว็บแอป

เมื่อแก้ไขสคริปต์เสร็จเรียบร้อยแล้ว ก่อนจะทำการบิวต์เว็บแอปของเรา จำเป็นต้องมีการทดสอบให้แน่ใจก่อนว่า สคริปต์ที่เราพากเพียรศึกษามานั้น สามารถทำงานได้อย่างถูกต้องหรือไม่ ขั้นตอนการนำลิงค์สำหรับทดสอบเว็บแอปนั้น ผู้บันทึกได้เคยแนะนำเอาไว้แล้วจากบทบันทึกก่อนหน้า หากจำไม่ได้ก็ย้อนกลับไปอ่าน [ตรงนี้](https://kms74.gitbook.io/learn-to-be/google-apps-script/form-insert-data-to-google-sheet#undefined-2) ได้เลย

* ผู้บันทึกได้ทำการเพิ่มรายการลูกค้า "โรงแรมบ้านสวนริมน้ำ" เอาไว้ก่อนแล้ว

![delete-sheet-before](https://user-images.githubusercontent.com/52767363/191158503-8451941c-64f5-43a8-b526-44b7e05fa23b.PNG)

* ทดลองกด `ลบ` เลย

![delete-sheet-0](https://user-images.githubusercontent.com/52767363/191158355-7d5c620b-7c42-4a1a-8b37-0f8ba74a9660.png)

* ฟังก์ชั่น `accessDelete(index)` จะแสดงไดอะล็อก `confirm` ขึ้นมา (สังเกตว่าเราได้ไอดีลูกค้ามาในขั้นตอนนี้แล้ว) ถ้ากด `ยกเลิก` ไดอะล็อกจะปิดไปไม่มีอะไรเกิดขึ้น

![delete-sheet-1](https://user-images.githubusercontent.com/52767363/191158506-429c3e4d-31ef-4f35-974f-9369d551f511.png)

* ถ้ากด `ตกลง` ที่ไดอะล็อก `confirm` ฟังก์ชั่นจะดำเนินงานต่อ จนได้รับคำตอบจากเซิร์ฟเวอร์ ก็จะแสดงไดอะล็อกจากฟังก์ชั่น `goAlert(result)` ออกมา

![delete-sheet-2](https://user-images.githubusercontent.com/52767363/191158498-6c7bdc07-14b8-43d7-bacf-09e5ed2b7ac9.png)

* เมื่อกด `ตกลง` จะเห็นว่าข้อมูลลูกค้า "โรงแรมบ้านสวนริมน้ำ" หายไปจากตารางข้อมูลแล้ว

![delete-sheet-3](https://user-images.githubusercontent.com/52767363/191158502-ae7adb1c-a326-4710-aa3a-33fb53de80de.png)

* และเมื่อไปตรวจสอบดูในฐานข้อมูล (Google Sheet)

![delete-sheet-finish](https://user-images.githubusercontent.com/52767363/191158504-e2a4265c-201c-4154-8b27-f4de120982ee.png)

## สรุป

ถึงตอนนี้เท่ากับว่าเราได้เว็บแอปที่พร้อมสำหรับ [เพิ่ม](https://kms74.gitbook.io/learn-to-be/google-apps-script/form-insert-data-to-google-sheet) [อ่าน](https://kms74.gitbook.io/learn-to-be/google-apps-script/read-google-sheet-to-web-app) [แก้ไข](https://kms74.gitbook.io/learn-to-be/google-apps-script/google-apps-script) และ ลบ หรือ `CRUD Operation` ข้อมูลในกูลเกิ้ลชีตเป็นที่เรียบร้อย หวังว่าคงจะมีประโยชน์สำหรับผู้ศึกษาที่จะนำไปปรับเปลี่ยน หรือพัฒนาต่อยอดให้เข้ากับกิจกรรมฐานข้อมูลในองค์กรของผู้ศึกษาได้

#### แสดงความคิดเห็นได้ที่ :point\_right: [![github-gist-button](https://user-images.githubusercontent.com/52767363/191145099-9f4a51a2-35cc-495f-82e1-284d769a9052.png)](https://gist.github.com/Komsan74/2e3741d7b67a1f7785456a229968039d)
