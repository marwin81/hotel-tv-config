# Hotel TV Config

ไฟล์ตั้งค่าและรูปของแต่ละโรงแรม สำหรับแอป Hotel TV Launcher
กล่องทีวีโหลดไฟล์จาก repo นี้โดยตรง แก้ไฟล์ที่นี่แล้วทุกกล่องของโรงแรมนั้นจะเปลี่ยนตามเอง

> repo นี้เป็น Public — ใครมีลิงก์ก็เปิดไฟล์ได้ อย่าใส่ข้อมูลที่เป็นความลับ

## โครงสร้าง

```
<ชื่อโรงแรม>/
  config.json      ไฟล์ตั้งค่า (ข้อความ, Wi-Fi, ปุ่มแอป)
  background.jpg   รูปพื้นหลัง (แนะนำ 1920×1080 JPG ไม่เกิน ~1 MB)
```

## ลิงก์ที่ใช้ตั้งค่ากล่อง

```
https://raw.githubusercontent.com/marwin81/hotel-tv-config/main/<ชื่อโรงแรม>/config.json
```

ตั้งกล่องผ่าน ADB:

```
adb shell am start -n com.hoteltv.launcher/.SetupActivity --es config_url "<ลิงก์ด้านบน>" --es pin <PIN>
```

## เปลี่ยนรูปหรือข้อความ

- **รูป:** อัปไฟล์ใหม่ทับ `background.jpg` ชื่อเดิมได้เลย
- **ข้อความ:** แก้ `config.json` แล้ว commit
- GitHub แคชไฟล์ประมาณ 5 นาที กล่องเช็กทุก `refreshMinutes` นาที จึงอาจต้องรอรวมกันสักพัก
- ถ้า `config.json` เขียนผิดรูปแบบ กล่องจะไม่ใช้ไฟล์นั้นและแสดงค่าล่าสุดที่ถูกต้องต่อไป

| โรงแรม | โฟลเดอร์ |
|---|---|
| Space Hotel | `space-hotel/` |
| Galleria 12 Hotel Bangkok (G12) | `g12/` |
| Galleria 10 Hotel Bangkok (G10) | `g10/` |
| The Key Premier | `the-key-premier/` |
