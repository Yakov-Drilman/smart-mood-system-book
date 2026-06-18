---
layout: journey
title: פרק 8 - ה-API הראשון
hero_image: /assets/images/chapter-08-hero.png
---

פרק 8: ה־API הראשון

יש רגע בפרויקט שבו כל הדיאגרמות, ההחלטות והארכיטקטורה סוף סוף נבחנים במבחן אחד פשוט:

האם המערכת שלך באמת יודעת לקבל בקשה אמיתית?

לא רעיון.
לא תכנון.
בקשה חיה שמגיעה מהעולם.

וזה הרגע שבו בניתי את ה־API הראשון של Smart Mood System.

🧠 מה בעצם בודקים כאן?

ה־API הראשון לא היה “עוד פיצ’ר”.

הוא היה מבחן בסיסי:

האם אני יודע לקבל רגש מהמשתמש?
האם אני יודע לשמור אותו?
והאם אני יודע להחזיר תשובה עקבית?

אם זה עובד — יש מערכת.
אם לא — יש רק קוד.

⚙️ הבחירה הראשונה: endpoint אחד פשוט

במקום להתחיל מורכב, החלטתי על דבר אחד:

Endpoint אחד שמכניס רגש למערכת.

POST /api/emotions

זהו.

אין עוד מסכים.
אין עוד מורכבות.

רק נקודת כניסה אחת.

🧱 שלב 1: ה־Route
const express = require("express");
const router = express.Router();
const emotionsController = require("../controllers/emotionsController");

router.post("/", emotionsController.createEmotion);

module.exports = router;

כבר כאן יש החלטה חשובה:

ה־Route לא יודע כלום על לוגיקה.

הוא רק מעביר הלאה.

🧠 שלב 2: ה־Controller
const emotionsService = require("../services/emotionsService");

exports.createEmotion = async (req, res) => {
  try {
    const emotion = await emotionsService.createEmotion(req.body);
    res.status(201).json(emotion);
  } catch (error) {
    res.status(500).json({ message: "Error saving emotion" });
  }
};

ופה קורה משהו חשוב:

ה־Controller לא מנתח רגשות
הוא לא מחליט כלום
הוא רק מתווך
⚙️ שלב 3: ה־Service (הלב של המערכת)
const fs = require("fs");
const path = require("path");

const filePath = path.join(__dirname, "../data/emotions.json");

exports.createEmotion = async (data) => {
  const emotions = JSON.parse(fs.readFileSync(filePath, "utf-8"));

  const newEmotion = {
    id: Date.now().toString(),
    userId: data.userId,
    type: data.type,
    intensity: data.intensity,
    context: data.context,
    note: data.note,
    createdAt: new Date().toISOString()
  };

  emotions.push(newEmotion);

  fs.writeFileSync(filePath, JSON.stringify(emotions, null, 2));

  return newEmotion;
};

ופה קורה הדבר האמיתי:

רגש הופך לנתון במערכת.

🧪 הרגע שבו זה הפך ל”אמיתי”

ברגע הראשון שה־API עבד, משהו השתנה:

לא היה יותר “רעיון”.

היה:

בקשה שנכנסת
נתון שנשמר
תשובה שחוזרת

וזה כל מה שמערכת עושה.

🧠 ההבנה הקריטית של הפרק

מערכת לא נמדדת בכמה היא חכמה.

אלא בכמה היא עקבית.

וזה מה שה־API הראשון הוכיח:

אפשר להפוך רגש למבנה נתונים יציב.

⚠️ ומה עדיין חסר?

כמובן, זה עדיין רחוק ממערכת שלמה:

אין ולידציה
אין אבטחה
אין משתמשים אמיתיים
אין DB אמיתי

אבל זה לא משנה.

כי עכשיו יש בסיס.

🔥 שינוי החשיבה

בשלב הזה כבר לא חשבתי:

“איך בונים API”

אלא:

“איך כל פיצ’ר עתידי ייכנס לתוך המבנה הזה בלי לשבור אותו”

וזה ההבדל בין דמו למערכת.

🎯 סוף הפרק

בשלב הזה Smart Mood System כבר עשה משהו משמעותי:

הוא לא רק רעיון — הוא מערכת שמקבלת נתונים אמיתיים.

אבל זה רק הצעד הראשון.

בפרק הבא נתחיל לבנות את המנוע האמיתי של המערכת: