---
title: บทฝึกหัดนี้เป็นการสร้างตารางข้อมูล โดยใช้ react-bootstrap เฟรมเวิร์ค
description: Kms74 Sep, 2022
---

# Table with react-bootstrap

<figure><img src="https://github.com/Komsan74/react-bootstrap-table/raw/main/assets/react-bootstrap-table.PNG" alt=""><figcaption></figcaption></figure>

## [Table.js](https://github.com/Komsan74/react-bootstrap-table/blob/main/src/component/Table.js)

กำหนดแม่แบบตาราง โดยศึกษารูปแบบจาก [react-bootstrap](https://react-bootstrap.github.io/components/table/) แล้วให้รีเทิร์นค่าออกมาตาม props ที่เรากำหนด

* header = อาร์เรย์ชื่อส่วนหัวตาราง (column header)
* data = อาร์เรย์ข้อมูลที่นำมาแสดงในตาราง

```jsx
    <Tables data={data} header={["column1", "column2", "...columN"]} />
```

## [App.js](https://github.com/Komsan74/react-bootstrap-table/blob/main/src/App.js)

* กำหนด {data} ด้วยการดึงข้อมูลจำลองมาจาก https://fakestoreapi.com

Get all products

```jsx
    fetch('https://fakestoreapi.com/products')
                .then(res=>res.json())
                .then(json=>console.log(json))
```

## อ้างอิง

* [React-Bootstrap](https://react-bootstrap.netlify.app/components/table/)
* [Demo in codesandbox.io](https://codesandbox.io/s/github/Komsan74/react-bootstrap-table)
* [Source code in github.com](https://github.com/Komsan74/react-bootstrap-table)
