---
layout: build-log
title: Day 2 – Backend Architecture & Full CRUD
hero_image: /assets/images/chapter-01-hero.png
---

# Day 2 – Backend Architecture & Full CRUD

## 🚀 From Simple Server → Real Architecture

ביום הזה התחלנו להפוך את ה-backend שלנו ממבנה פשוט של קובץ אחד  
למערכת מודולרית עם הפרדה בין שכבות (Architecture בסיסי).

---

## 🎯 מטרות היום

- הפרדת הקוד ל-routes
- יצירת מבנה backend מקצועי
- בניית REST API מסודר
- הוספת POST request (Create)
- הוספת DELETE request (Remove)
- הבנה של CRUD בסיסי

---

## 🏗️ מבנה הפרויקט החדש

```plaintext
backend/
│
├── routes/
│     └── moods.js
│
├── services/
├── controllers/
├── data/
│
└── server.
```

---

## 🧠 למה זה חשוב?

במקום שכל הלוגיקה תהיה בקובץ אחד:

❌ לפני:

הכל ב-server.js

✔ אחרי:

- server.js → ניהול אפליקציה
- routes → ניהול endpoints
- הפרדה בין אחריותים (Separation of Concerns)
- קוד שניתן להרחבה ותחזוקה

---

## 🌐 Routes – Moods

📁 routes/moods.js

```javascript
const express = require("express");
const router = express.Router();
```

## 📥 GET – קבלת נתונים

```javascript
router.get("/", (req, res) => {
  res.json(moods);
});
```

---

## 📊 דוגמה לתגובה:

```json
[
  {
    "id": 1,
    "mood": "happy",
    "note": "Good day"
  }
]
```

---

## ➕ POST – הוספת Mood חדש

```javascript
router.post("/", (req, res) => {
  const newMood = {
    id: moods.length + 1,
    mood: req.body.mood,
    note: req.body.note,
  };

  moods.push(newMood);

  res.json({
    message: "Mood added successfully",
    mood: newMood,
  });
});
```

---

## 📥 דוגמה לבקשה:

```javascript
{
  "mood": "excited",
  "note": "Learning backend"
}
```

## 🗑️ DELETE – מחיקת Mood

```javascript
router.delete("/:id", (req, res) => {
  const id = parseInt(req.params.id);

  const moodIndex = moods.findIndex((m) => m.id === id);

  if (moodIndex === -1) {
    return res.status(404).json({
      message: "Mood not found",
    });
  }

  moods.splice(moodIndex, 1);

  res.json({
    message: "Mood deleted successfully",
  });
});
```

---

## 🔁 server.js – חיבור הכל

```javascript
const express = require("express");
const cors = require("cors");

const moodsRoutes = require("./routes/moods");

const app = express();

app.use(cors());
app.use(express.json());

app.get("/", (req, res) => {
  res.json({
    message: "Smart Mood API is running",
  });
});

app.use("/moods", moodsRoutes);

const PORT = 3001;

app.listen(PORT, () => {
  console.log(`Server running on port ${PORT}`);
});
```

---

## 🧪 איך בודקים את ה-API

## GET

```text
http://localhost:3001/moods
```

---

## POST

```text
POST http://localhost:3001/moods
```

Body:

```json
{
  "mood": "tired",
  "note": "Long day"
}
```

---

## DELETE

```text
DELETE http://localhost:3001/moods/1
```

---

## 🧠 מה למדנו היום

- מה זה Architecture בסיסי ב-Backend
- הפרדה ל־routes
- עבודה עם REST API אמיתי
- POST request ו־req.body
- DELETE request ו־route params
- CRUD בסיסי (Create, Read, Delete)

---

## ⚠️ מגבלה חשובה

כרגע הנתונים נשמרים בזיכרון בלבד (RAM):

אם השרת נכבה → הכל נמחק

זה תקין לשלב הזה כי אנחנו מתמקדים בלמידת API ולא ב־Database.
