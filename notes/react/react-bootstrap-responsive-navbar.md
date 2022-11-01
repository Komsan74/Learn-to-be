---
title: การสร้าง Responsive Navbar ด้วย react-bootstrap
description: Kms74 Nov, 2022
website:
    gist: 
    github: https://github.com/Komsan74/Learn-to-be/blob/main/notes/react/react-bootstrap-responsive-navbar
    gitbook: https://kms74.gitbook.io/Learn-to-be/notes/react/react-bootstrap-responsive-navbar.md
---

## บทเล่า<a name="info"></a>

บทบันทึกนี้จะเล่าถึงการสร้างแถบนำทางตรงส่วนหัวของ React Application (**Navigation Bar**) หรือเรียกง่าย ๆ ว่า **NavBar** ด้วยการใช้ CSS Framework อันเป็นที่นิยมอย่าง [Bootstrap](#) ซึ่งใน **React** จะมีไลบรารี่ชื่อ **react-bootstrap** ให้เรียกใช้งานได้โดยตรง

> react-bootstrap เป็นไลบรารี่ที่ re-implement เอา ฺBootstrap Component มาใช้ใน React อีกที

## ขั้นตอนดำเนินการ<a name="method"></a>

1. สร้างโครงงาน React ขึ้นมาใหม่ (ในตัวอย่างให้ชื่อโครงงานว่า react-responsive-nav)

```sh
npx creat-react-app react-responsive-nav
```

2. ย้ายพาธเข้าไปในโฟลเดอร์ของโครงงาน

```sh
cd react-responsive-nav
```

3. ติดตั้งไลบรารี่ `bootstrap` และ `react-bootstrap`


```sh
npm i bootstrap react-bootstrap
```

4. ทำการ Import Bootstrap ไว้ที่ `index.js`

```js
import "bootstrap/dist/css/bootstrap.min.css";
```

## Components

5. สร้างคอมโพเน้นท์ที่เราต้องการให้แสดงเป็นหน้าเว็บแอป ผู้บันทึกทำตัวอย่างไว้ 4 หน้าดังนี้

* Home --> `home.js`
* Customer --> `customer.js`
* Product --> `product.js`
* About --> `about.js`

โดยมีรายละเอียดภายในเป็นฟังก์ชั่น Javascript ดังนี้

```js
// home.js
export default function Home() {
    return <h1>Home Page</h1>
}
```

> :bulb: **Tip:** 
> คอมโพเน้นท์อื่น ๆ ก็เปลี่ยนชื่อฟังก์ชั่น และชื่อเพจ ให้ตรงกับชื่อของคอมโพเน้นท์นั้น ๆ


## Create NavBar

6. สร้างคอมโพเน้นท์ appNav.js โดยเขียนฟังก์ชั่น `Javascript` ดังนี้

```js
// appNav.js
import { Container, Nav, Navbar } from "react-bootstrap";
import { Link } from "react-router-dom";

export default function AppNav() {
  return (
    <Navbar collapseOnSelect expand="lg" bg="danger" variant="dark">
      <Container>
        <Navbar.Brand href="#">AppNav</Navbar.Brand>
        <Navbar.Toggle aria-controls="responsive-navbar-nav" />
        <Navbar.Collapse id="responsive-navbar-nav">
          <Nav className="me-auto">
            <Nav.Link eventKey="0" as={Link} to="/">
              Home
            </Nav.Link>
            <Nav.Link eventKey="1" as={Link} to="/customer">
              Customer
            </Nav.Link>
            <Nav.Link eventKey="2" as={Link} to="/product">
              Product
            </Nav.Link>
            <Nav.Link eventKey="3" as={Link} to="/about">
              About
            </Nav.Link>
          </Nav>
        </Navbar.Collapse>
      </Container>
    </Navbar>
  );
}
```
## Router

7. ในโครงงานตัวอย่างมีการเรียกใช้ **Router** จากไลบรารี่ **react-router-dom** ฉะนั้นก่อนจะเรียกใช้ได้เราจึงต้องติดตั้งเข้ามาก่อน

```sh
npm i react-router-dom
```

8. จากนั้นจึงไปกำหนดใช้งานใน `App.js` แบบนี้

```js
// App.js
import { HashRouter, Route, Routes } from "react-router-dom";
import About from "./components/about";
import Customer from "./components/customer";
import Home from "./components/home";
import Product from "./components/product";
import AppNav from "./components/appNav";
import "./styles.css";

export default function App() {
  return (
    <div className="App">
      <HashRouter>
        <AppNav />
        <Routes>
          <Route exact path="/" element={<Home />} />
          <Route path="/customer" element={<Customer />} />
          <Route path="/product" element={<Product />} />
          <Route path="/about" element={<About />} />
        </Routes>
      </HashRouter>
    </div>
  );
}
```

9. เมื่อทำทุกอย่างครบถ้วนแล้วก็ทำการทดสอบเว็บแอปของเรา

```sh
npm start
```

## ผลลัพท์<a name="result"></a>

10. ถ้าไม่มีข้อผิดพลาดใด ๆ ก็ควรจะเห็นเว็บแอปที่มี **NavBar** ดังรูป ลองกดเมนูแต่ละอัน **Router** จะทำหน้าที่เปลี่ยนหน้าแสดงผลให้เราได้อย่างถูกต้อง

![ใส่รูป](#)

และเมื่อแสดงผลในอุปกรณ์ที่หน้าจอแคบ เช่นแท็บเล็ท/มือถือ ก็จะทำการย่อเมนูไว้ที่ปุ่ม `Togle` แบบนี้

![ใส่รูป](#)

## บทสรุป<a name="conclusion"></a>
ในการสร้าง Navigation Bar หรือ NavBar ด้วย react-bootstrap ให้แสดงผลแบบ Responsive ได้ และเมื่อนำมาใช้ร่วมกับ react-router-dom แล้วทำให้ NavBar ทำงานได้สมบูรณ์ยิ่งขึ้น ผู้บันทึกหวังว่าบทบันทึกนี้จะเป็นแนวทางหนึ่งที่ช่วยให้ผู้ศึกษา ได้แนวความคิดในการพัฒนาต่อยอด ไปใช้ในกิจกรรมของตัวเองไม่มากก็น้อย

## บทบันทึกที่เกี่ยวข้อง
* [1](#)
* [2](#)