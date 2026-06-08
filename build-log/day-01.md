# Day 1 – Backend Setup

## 🚀 Backend Foundation

ביום הראשון בנינו את הבסיס של מערכת Smart Mood System – אפליקציית SaaS לניהול ומעקב אחרי מצב רגשי.

המטרה הייתה להקים backend ראשוני עובד, עם שרת Node.js ו־API ראשון, שמייצר בסיס אמיתי להמשך פיתוח המערכת.

---

## 🎯 מטרות היום
- יצירת פרויקט Node.js
- הקמת שרת Express בסיסי
- יצירת endpoints ראשונים
- הרצת שרת מקומי
- חיבור ראשוני ל-GitHub
- יצירת Git tag ליום 1

---

## 🏗️ מה בנינו בפועל
### 📁 מבנה הפרויקט

```plaintext
smart-mood-system/
│
├── backend/
│   ├── server.js
│   ├── package.json
│
└── frontend/ (מוכן להמשך)
```
---

## ⚙️ שרת Node.js (Express)

השרת מאזין לפורט 3001 ומספק API בסיסי.

🌐 Endpoints
GET /

מחזיר סטטוס שהשרת פעיל:

{
  "message": "Smart Mood API is running"
}
GET /moods

מחזיר נתוני דוגמה של מצבי רוח:

[
  {
    "id": 1,
    "mood": "happy",
    "note": "Good day"
  },
  {
    "id": 2,
    "mood": "stressed",
    "note": "Too much work"
  }
]

---

## 🧪 איך מריצים את הפרויקט

בתוך תיקיית backend:

npm install
npm run dev

השרת ירוץ בכתובת:

http://localhost:3001
🧠 מה למדנו היום
איך מקימים backend מאפס
עבודה עם Express
יצירת REST API בסיסי
בדיקת endpoints בדפדפן
חיבור פרויקט ל־GitHub
שימוש ב־Git tag כ־snapshot של יום
🏷️ Git Snapshot
day-01

## 🔗 קישור לקוד:

[![Day 1](https://img.shields.io/badge/Code-Day_01-blue)](https://github.com/Yakov-Drilman/smart-mood-system/tree/day-01)
https://github.com/Yakov-Drilman/smart-mood-system/tree/day-01
📌 מצב הפרויקט בסוף היום

✔ Backend עובד
✔ API ראשון פעיל
✔ שרת רץ בהצלחה
✔ Git repository מחובר
✔ Tag של יום 1 נוצר
