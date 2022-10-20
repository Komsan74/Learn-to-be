---
description: Kms74 Sep, 2022
---

# Pagination with react-bootstrap

<figure><img src="https://github.com/Komsan74/react-bootstrap-pagination/raw/main/assets/react-bootstrap-pagination.PNG" alt=""><figcaption></figcaption></figure>

## [DataList.js](https://github.com/Komsan74/react-bootstrap-pagination/blob/main/src/controller/DataList.js)

สร้างฟังก์ชั่น dataList ใช้กำหนดรูปแบบการแสดงข้อมูลในแต่ละหน้า ว่าจะให้แสดงผลในแต่ละหน้าได้กี่แถวข้อมูล ในบทฝึกหัดนี้ใช้ตัวอย่างเป็นตารางข้อมูล ที่ดึงข้อมูลจำลองมาจาก https://fakestoreapi.com เช่นเคย รูปแบบการใช้งานฟังก์ชั่นเป็นดังนี้

```jsx
dataList(data, rowsPerPage, pageNumber);
```

เมื่อเรากำหนดค่าลงไป ฟังก์ชั่นนี้จะรีเทิร์นค่าออกมาดังนี้

* pageList = อาร์เรย์รายการข้อมูลที่จะให้แสดงในแต่ละหน้า
* items = อาร์เรย์ระบุหมายเลขหน้าที่จะส่งไปให้ Pagination

## [Table.js](https://github.com/Komsan74/react-bootstrap-pagination/blob/main/src/component/Table.js)

กำหนดแม่แบบตาราง โดยศึกษารูปแบบจาก [react-bootstrap](https://react-bootstrap.github.io/components/table/) แล้วให้รีเทิร์นค่าออกมาตาม props ที่เรากำหนด

* header = อาร์เรย์ชื่อส่วนหัวตาราง (column header)
* data = อาร์เรย์ข้อมูลที่นำมาแสดงในตาราง

```jsx
<Table data={data} header={["column1", "column2", "...columN"]} />
```

## [App.js](https://github.com/Komsan74/react-bootstrap-pagination/blob/main/src/App.js)

* กำหนด {data} ด้วยการดึงข้อมูลจำลองมาจาก https://fakestoreapi.com

Get all products

```jsx
fetch("https://fakestoreapi.com/products")
  .then((res) => res.json())
  .then((json) => console.log(json));
```

* กำหนด Pagination ไว้ในลำดับสุดท้ายของหน้า ในตัวอย่างได้เพิ่ม button `Prev` กับ `Next` เพื่อใช้ในการเลื่อนหน้า พร้อมเขียนฟังก์ชั่นควบคุม รูปแบบในการวาง Pagination ก็จะเป็นดังนี้

```jsx
<Container>
  ...
  <Pagination>
    <Pagination.Prev onClick={_function()} />
    <Pagination.Item active={page_number} onClick={_function()}>
      {page_number}
    </Pagination.Item>
    <Pagination.Item>{page_number}</Pagination.Item>
    ...
    <Pagination.Next onClick={_function()} />
  </Pagination>
</Container>
```

## อ้างอิง

* [React-Bootstrap](https://react-bootstrap.netlify.app/components/pagination/)
* [Demo in CodeSandbox.io](https://codesandbox.io/s/github/Komsan74/react-bootstrap-pagination)
* [Source code in github.com](https://github.com/Komsan74/react-bootstrap-pagination)
