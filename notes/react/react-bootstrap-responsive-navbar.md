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

> react-bootstrap เป็นการ re-implement เอา ฺBootstrap Component มาใช้ใน React อีกที

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

## Components

4. สร้างคอมโพเน้นท์ที่เราต้องการให้แสดงเป็นหน้าเว็บแอป ผู้บันทึกทำตัวอย่างไว้ 4 หน้าดังนี้

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

สร้างคอมโพเน้นท์ appNav.js โดยเขียนฟังก์ชั่น `Javascript` ดังนี้

```js
// appNav.js
f
```

## ผลลัพท์<a name="result"></a>

## บทสรุป<a name="conclusion"></a>