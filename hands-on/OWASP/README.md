# โปรเจกต์ศึกษาช่องโหว่ OWASP Top 10

## 📋 เกี่ยวกับโปรเจกต์

โปรเจกต์นี้เป็นแอปพลิเคชั่นตัวอย่างสำหรับการศึกษาช่องโหว่ตามมาตรฐาน OWASP Top 10 โดยแอปพลิเคชันถูกออกแบบให้มีช่องโหว่ความปลอดภัยเพื่อให้นักพัฒนาได้ศึกษาและเข้าใจถึงวิธีการป้องกันช่องโหว่เหล่านี้

> ⚠️ **คำเตือน**: แอปพลิเคชันนี้มีช่องโหว่ความปลอดภัย ห้ามนำไปใช้ในสภาพแวดล้อมจริงหรือระบบที่เข้าถึงจากภายนอก

## 🚀 การติดตั้งและใช้งาน

### วิธีรันโดยใช้ Docker

```bash
# สร้าง Docker image
docker build -t owasp-demo .

# รัน container
docker run -p 3000:3000 owasp-demo
```

### วิธีรันโดยตรง

```bash
# ติดตั้ง dependencies
npm install

# รันแอปพลิเคชัน
npm start
```

เข้าใช้งานแอปพลิเคชันได้ที่: http://localhost:3000

## 🔒 ช่องโหว่ที่มีในโปรเจกต์

โปรเจกต์นี้มีตัวอย่างช่องโหว่ตาม OWASP Top 10 ดังนี้

### 1. SQL Injection

**ไฟล์:** `app.js` (ฟังก์ชัน `/login`)

**คำอธิบาย:** แอปพลิเคชันรวมอินพุตจากผู้ใช้เข้าไปในคำสั่ง SQL โดยตรง โดยไม่มีการป้องกัน ทำให้ผู้ใช้สามารถแทรกคำสั่ง SQL เพื่อเข้าสู่ระบบโดยไม่ต้องรู้รหัสผ่าน

**ตัวอย่างการโจมตี:**
- ชื่อผู้ใช้: `admin' --`
- รหัสผ่าน: (อะไรก็ได้)

**วิธีแก้ไข:** ใช้ Parameterized Queries หรือ Prepared Statements
```javascript
// แก้ไขเป็น
db.get("SELECT * FROM users WHERE username = ? AND password = ?", [username, password], (err, user) => {
  // ...
});
```

### 2. Cross-Site Scripting (XSS)

**ไฟล์:** `app.js` (ฟังก์ชัน `/messages`) และ `public/index.html` (การแสดงข้อความ)

**คำอธิบาย:** แอปพลิเคชันไม่มีการตรวจสอบหรือ sanitize ข้อมูลที่รับเข้ามาจากผู้ใช้ก่อนที่จะนำไปแสดงผล ทำให้สามารถแทรก script ที่จะทำงานบนเบราว์เซอร์ของผู้ใช้งานอื่นได้

**ตัวอย่างการโจมตี:** 
```html
<script>alert('XSS')</script>
```

**วิธีแก้ไข:** ใช้การ sanitize ข้อมูลก่อนนำไปแสดงผล
```javascript
// แก้ไขโดยใช้ escaping library เช่น
const sanitizedMessage = escapeHtml(message);

// หรือใช้ DOM API แทนการใช้ innerHTML
const textNode = document.createTextNode(message);
element.appendChild(textNode);
```

### 3. Insecure Direct Object References (IDOR)

**ไฟล์:** `app.js` (ฟังก์ชัน `/messages/:id`)

**คำอธิบาย:** แอปพลิเคชันอนุญาตให้ผู้ใช้เข้าถึงข้อมูลโดยตรงผ่าน ID โดยไม่มีการตรวจสอบว่าผู้ใช้มีสิทธิ์เข้าถึงข้อมูลนั้นหรือไม่

**วิธีแก้ไข:** เพิ่มการตรวจสอบสิทธิ์ก่อนที่จะให้เข้าถึงข้อมูล
```javascript
// แก้ไขเป็น
const userId = req.cookies.user_id;
db.get("SELECT * FROM messages WHERE id = ? AND (user_id = ? OR user_id IN (SELECT id FROM users WHERE role = 'admin'))", 
  [messageId, userId], (err, message) => {
  // ...
});
```

### 4. Broken Access Control

**ไฟล์:** `app.js` (ฟังก์ชัน `/admin/users`)

**คำอธิบาย:** แอปพลิเคชันตรวจสอบสิทธิ์โดยใช้คุกกี้ที่ผู้ใช้สามารถแก้ไขได้ ทำให้ผู้ใช้ทั่วไปสามารถเปลี่ยนค่าคุกกี้เพื่อเข้าถึงฟังก์ชันของผู้ดูแลระบบได้

**วิธีแก้ไข:** ใช้ session management ที่เหมาะสมและมีการตรวจสอบสิทธิ์ที่ server ทุกครั้ง
```javascript
// แก้ไขโดยใช้ session แทนคุกกี้ธรรมดา
// ต้องเพิ่ม express-session ใน dependencies
const session = require('express-session');
app.use(session({
  secret: 'your-secret-key',
  resave: false,
  saveUninitialized: false,
  cookie: { 
    secure: true, // ใช้กับ HTTPS
    httpOnly: true, 
    sameSite: 'strict'
  }
}));

// และแก้ไขการตรวจสอบสิทธิ์
if (req.session.role === 'admin') {
  // ...
}
```

### 5. การจัดการคุกกี้ที่ไม่ปลอดภัย

**ไฟล์:** `app.js` (ฟังก์ชัน `/login`)

**คำอธิบาย:** แอปพลิเคชันใช้คุกกี้ปกติโดยไม่มีการตั้งค่า security flags เช่น HttpOnly, Secure หรือ SameSite ทำให้คุกกี้ถูกเข้าถึงจาก JavaScript หรือถูกขโมยได้ง่าย

**วิธีแก้ไข:** ตั้งค่าความปลอดภัยให้กับคุกกี้
```javascript
res.cookie('user_id', user.id, { 
  httpOnly: true, 
  secure: process.env.NODE_ENV === 'production', 
  sameSite: 'strict'
});
```

## 🧪 การทดสอบช่องโหว่

โปรเจกต์นี้มี UI สำหรับทดสอบช่องโหว่แต่ละประเภท ผู้ใช้สามารถลองโจมตีแอปพลิเคชันด้วยวิธีต่างๆ ตามคำแนะนำในหน้าเว็บ

## 📚 ทรัพยากรที่เกี่ยวข้อง

- [OWASP Top 10](https://owasp.org/www-project-top-ten/)
- [OWASP Cheat Sheet Series](https://cheatsheetseries.owasp.org/)
- [NodeJS Security Best Practices](https://github.com/goldbergyoni/nodebestpractices#6-security-best-practices)

## ⚠️ ข้อควรระวัง

โปรเจกต์นี้มีวัตถุประสงค์เพื่อการศึกษาเท่านั้น อย่านำไปใช้ในสภาพแวดล้อมการผลิตจริงหรือบนเซิร์ฟเวอร์ที่เข้าถึงได้จากภายนอก เนื่องจากมีช่องโหว่ความปลอดภัยโดยตั้งใจ
