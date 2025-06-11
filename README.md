[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/w8H8oomW)
**<ins>Note</ins>: Students must update this `README.md` file to be an installation manual or a README file for their own CS403 projects.**

**รหัสโครงงาน:** 67-1_05_nri-s2

**ชื่อโครงงาน (ไทย):** การพัฒนาแชทบอทประเมินความวิตกกังวล (GAD-7)

**Project Title (Eng):** THE DEVELOPMENT OF GENERAL ANXIETY DISORDER-7 (GAD-7) CHATBOT

**อาจารย์ที่ปรึกษาโครงงาน:** ผศ.ดร.นุชจรินทร์ อินต๊ะหล้า

**ผู้จัดทำโครงงาน:**
1. นาย พีรณัฐ ศรีสุตโต 6209650107 peeranut.sri@dome.tu.ac.th
2. นางสาว ณัฎฐณิชา คำสวัสดิ์ 6309650262 nattanicha.kum@dome.tu.ac.th

# LINE Bot Project Structure

## 📁 โครงสร้างไฟล์

```
├── config/                 # การตั้งค่าระบบ
│   ├── lineConfig.js       # การตั้งค่า LINE Bot (Access Token, Channel Secret)
│   ├── logger.js           # การตั้งค่า Winston Logger
│   └── mongoConfig.js      # การเชื่อมต่อ MongoDB
│
├── logs/                   # ไฟล์ Log
│   └── bot.log            # Log ของ Bot
│
├── models/                 # MongoDB Schema Models
│   ├── testSchema.js       # Schema สำหรับข้อมูลการทดสอบ
│   └── userSchema.js       # Schema สำหรับข้อมูลผู้ใช้
│
├── utils/                  # Utility Functions
│   ├── activityRecommendations.js  # คำแนะนำกิจกรรม
│   ├── helpers.js         # Helper Functions
│   ├── messageTemplates.js # Template สำหรับข้อความ LINE
│   └── relaxationVideos.js # ข้อมูลวิดีโอผ่อนคลาย
│
├── bot.log              # Log ไฟล์หลัก
├── index.js             # ไฟล์หลักของ Bot
├── package.json         # NPM Dependencies
├── package-lock.json    # Lock file
├── replit.nix          # Nix configuration
└── richmenu.png        # รูปภาพ Rich Menu
```
   
### 1. สร้าง Replit Project และ Git Clone
- ไปที่ [https://replit.com/](https://replit.com/) และล็อกอิน
- คลิก **"+"** หรือ "Create" แล้วเลือก "Import from GitHub"
- ใส่ URL repository (https://github.com/ComSciThammasatU/2567-2-cs403-final-submission-67-1_05_nri-s2) แล้วคลิก "Import from GitHub"
- หรือใช้ Shell รัน: git clone https://github.com/ComSciThammasatU/2567-2-cs403-final-submission-67-1_05_nri-s2
- ย้ายไฟล์จากโฟลเดอร์ `line-bot` ไปยัง root directory และลบโฟลเดอร์ `line-bot`:
mv line-bot/* .
rmdir line-bot
- ตรวจสอบว่าไฟล์ `index.js` อยู่ที่ root directory
- ตั้งค่า Run Command ใน "Configure your App" เป็น:
node index.js
### 2. สร้าง MongoDB Atlas
- ไปที่ [https://www.mongodb.com/cloud/atlas](https://www.mongodb.com/cloud/atlas) และสมัครบัญชี
- สร้าง Cluster เลือก "Free Tier (M0)", Cloud Provider (เช่น AWS), Region (เช่น Singapore) แล้วคลิก "Create Cluster"
- ไปที่ "Network Access" คลิก "Add IP Address" เพิ่ม IP ปัจจุบันหรือ 0.0.0.0/0 แล้ว "Confirm"
- ไปที่ "Database Access" คลิก "Add New Database User" ใส่ Username (เช่น `myuser`) และ Password (เช่น `mypassword`) เลือก "Atlas Admin" แล้ว "Create User"
- ไปที่ "Clusters" คลิก "Connect" เลือก "Connect your application" (Node.js) คัดลอก Connection String (เช่น `mongodb+srv://myuser:[email protected]/test?retryWrites=true&w=majority`)

### 3. ตั้งค่า LINE Developer Console
- ไปที่ [https://developers.line.biz/](https://developers.line.biz/) และสมัครบัญชี
- ไปที่ "Console" คลิก "Create a Provider" ใส่ชื่อ (เช่น `MyBotProvider`) และอีเมล แล้ว "Create"
- ไปที่ "Messaging API" คลิก "Create a new channel" กรอกชื่อ (เช่น `MyLineBot`) เลือก Provider แล้ว "Create"
- ไปที่ "Channel Settings" คัดลอก **Channel Secret** และ **Channel Access Token**
- เปิด "Webhook" ใส่ URL Replit (เช่น `https://your-replit-url.onrender.com/webhook`) แล้วบันทึก

### 4. ตั้งค่า Secret ใน Replit
- ไปที่แท็บ "Secrets" ใน Replit
- เพิ่มตัวแปร Secret ดังนี้:
- CHANNEL_ACCESS_TOKEN: วาง Channel Access Token จาก LINE Developer Console
- CHANNEL_SECRET: วาง Channel Secret จาก LINE Developer Console
- MONGODB_URI: วาง Connection String จาก MongoDB Atlas
- บันทึกการเปลี่ยนแปลง

### 5. Deploy และทดสอบ
ไปที่แท็บ "Deploy" ใน Replit กด "Deploy"
ตั้งค่า URL Webhook ใน LINE Developer Console
สแกน QR Code จาก "Messaging API" เพื่อเพิ่มบอท แล้วส่งข้อความทดสอบ
  
