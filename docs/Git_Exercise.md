# Git Exercise - แนวทางการใช้งาน Git

## 📑 สารบัญ
1️⃣ [บทนำเกี่ยวกับ Git](#-บทนำเกี่ยวกับ-git)  
2️⃣ [การติดตั้ง Git](#-การติดตั้ง-git)  
3️⃣ [คำสั่งพื้นฐานใน Git](#-คำสั่งพื้นฐานใน-git)  
4️⃣ [การจัดการ Branch และ Merging](#-การจัดการ-branch-และ-merging)  
5️⃣ [แนวทางปฏิบัติที่ดีที่สุด](#-แนวทางปฏิบัติที่ดีที่สุด)  

---

## 📖 บทนำเกี่ยวกับ Git
Git คือระบบควบคุมเวอร์ชันที่ช่วยให้คุณสามารถติดตามและจัดการการพัฒนาโค้ดได้อย่างมีประสิทธิภาพ  
// ...existing guidelines...

## 🔧 การติดตั้ง Git
- สามารถดาวน์โหลด Git ได้จาก [git-scm.com](https://git-scm.com)
- ติดตั้งบน Windows, macOS หรือ Linux ตามคำแนะนำในเว็บไซต์
// ...existing guidelines...

## ⌨️ คำสั่งพื้นฐานใน Git
- `git init` : สร้าง repository ใหม่
- `git clone <url>` : คัดลอก repository
- `git add .` : เพิ่มไฟล์ใน staging area
- `git commit -m "ข้อความ"` : บันทึกการเปลี่ยนแปลง
- `git status` : ตรวจสอบสถานะของ repository
// ...existing guidelines...

## 🌿 การจัดการ Branch และ Merging
- การสร้าง Branch: `git branch <branch-name>`
- การสลับ Branch: `git checkout <branch-name>`
- การ Merge Branch: `git merge <branch-name>`
// ...existing guidelines...

## 📌 แนวทางปฏิบัติที่ดีที่สุด
- เขียน commit message ให้ชัดเจนและสั้นกระชับ
- อัปเดต Branch บ่อยครั้งจาก master/main
- ทดสอบโค้ดก่อน Merge  
// ...existing guidelines...
