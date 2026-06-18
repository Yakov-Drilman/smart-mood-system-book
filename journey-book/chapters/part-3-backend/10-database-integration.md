---
layout: journey
title: פרק 10 - חיבור למסד נתונים
hero_image: /assets/images/chapter-11-hero.png
---

פרק 10: חיבור למסד נתונים

יש רגע בפרויקט שבו אתה מפסיק “לשחק עם נתונים”
ומתחיל לנהל אותם באמת.

עד עכשיו הכל היה פשוט:

קובץ JSON
קריאה/כתיבה ישירה לדיסק
שליטה מלאה, כמעט נאיבית

זה עובד.
אבל זה עובד כמו אב טיפוס.

ואז מגיעה ההבנה:

מערכת אמיתית לא יכולה להסתמך על קובץ.

🧠 הבעיה שלא ראית עד עכשיו

ברגע שמתחילים לחשוב קצת קדימה, הקובץ מתחיל להראות בעייתי:

אין concurrency אמיתי
כל כתיבה דורסת את הקובץ
אין סקייל
אין שאילתות חכמות
אין אינדקסים

ובעיקר:

אי אפשר לגדול ככה.

⚙️ נקודת המפנה

בשלב הזה כבר לא שאלתי:

“איך אני שומר רגשות?”

אלא:

“איך אני שומר מערכת של רגשות לאורך זמן?”

וזה הבדל עצום.

🧱 הבחירה: מעבר ל־MongoDB

בחרתי במסד נתונים NoSQL, לא במקרה.

כי המערכת שלי הייתה:

דינמית
מבוססת אובייקטים
משתנה כל הזמן
בלי סכימה קשיחה מדי

MongoDB התאים בדיוק לאופי הזה.

🧠 שינוי החשיבה: מקובץ למסד נתונים

עד עכשיו:

fs.readFile → modify → fs.writeFile

מעכשיו:

Client → DB Query → Persisted Data

וזה כבר עולם אחר.

⚙️ שלב 1: חיבור בסיסי
const mongoose = require("mongoose");

mongoose.connect("mongodb://localhost:27017/smartmood", {
  useNewUrlParser: true,
  useUnifiedTopology: true,
});

ופה קורה משהו קטן אבל חשוב:

המערכת מפסיקה להיות “קבצים” ומתחילה להיות “שירות”.

🧩 שלב 2: מודל רגש

במקום JSON ידני, מגדירים Schema:

const mongoose = require("mongoose");

const emotionSchema = new mongoose.Schema({
  userId: String,
  type: String,
  intensity: Number,
  context: String,
  note: String,
  createdAt: {
    type: Date,
    default: Date.now
  }
});

module.exports = mongoose.model("Emotion", emotionSchema);

וזה רגע חשוב:

עכשיו יש למערכת “חוקי מציאות”.

🧠 מה השתנה באמת?

לפני כן:

הנתונים היו “קבצים”
האחריות הייתה על הקוד

עכשיו:

הנתונים חיים בתוך מסד נתונים
יש שכבת אבטחה פנימית
יש עקביות
יש מבנה
⚙️ שלב 3: שינוי ה־Service
const Emotion = require("../models/Emotion");

exports.createEmotion = async (data) => {
  const emotion = new Emotion(data);
  return await emotion.save();
};

exports.getAllEmotions = async () => {
  return await Emotion.find();
};

exports.updateEmotion = async (id, updates) => {
  return await Emotion.findByIdAndUpdate(id, updates, { new: true });
};

exports.deleteEmotion = async (id) => {
  return await Emotion.findByIdAndDelete(id);
};

ופה קורה משהו עמוק:

הקוד נהיה קצר יותר — אבל חזק יותר.

🔥 שינוי פרדיגמה

זה אחד הרגעים הכי חשובים במערכת:

פחות קוד
יותר יכולת
פחות שליטה ידנית
יותר אחריות למערכת
🧠 ההבנה הקריטית של הפרק

מסד נתונים הוא לא “אחסון”.

הוא:

הזיכרון הקבוע של המערכת שלך.

וברגע שאתה מחבר אותו — אתה קובע איך המערכת תזכור את המשתמשים שלה.

⚠️ הטעות שנמנעה

אם הייתי נשאר עם JSON הייתי מקבל:

באגים של דריסת מידע
חוסר עקביות
בעיות ביצועים
מערכת שלא מתרחבת
🎯 סוף הפרק

בשלב הזה Smart Mood System כבר לא “פרויקט קוד”.

הוא מערכת עם:

API אמיתי
CRUD מלא
מסד נתונים
שכבות הפרדה

אבל עדיין חסר משהו קריטי:

משתמשים אמיתיים והזדהות.