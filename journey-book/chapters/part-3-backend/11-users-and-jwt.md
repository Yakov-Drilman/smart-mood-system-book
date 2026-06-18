---
layout: journey
title: פרק 11 - ניהול משתמשים ו-JWT
hero_image: /assets/images/chapter-11-hero.png
---


פרק 11: ניהול משתמשים ו-JWT

עד עכשיו המערכת ידעה לעשות דבר אחד טוב:

לנהל רגשות.

אבל היה חסר פרט קטן אחד… שהוא בעצם כל ההבדל בין דמו למוצר:

מי בכלל הבעלים של הרגש?

🧠 הבעיה שהתעלמתי ממנה בהתחלה

בהתחלה זה היה נוח להעמיד פנים שכולם אותו משתמש.

פשוט:

שולחים רגש
שומרים אותו
מחזירים אותו

אבל מהר מאוד זה נהיה לא ריאלי.

כי בעולם אמיתי:

לכל משתמש יש היסטוריה שונה
כל רגש שייך למישהו
וכל נתון צריך הקשר

וזה הרגע שבו המערכת “מתבגרת”.

⚙️ השאלה החדשה

ברגע שמוסיפים משתמשים, השאלה משתנה:

איך אני יודע שכל רגש שייך למשתמש הנכון?

וזה כבר לא בעיית נתונים.

זו בעיית זהות.

🧱 שלב 1: יצירת משתמשים

התחלתי מהבסיס:

const mongoose = require("mongoose");

const userSchema = new mongoose.Schema({
  name: String,
  email: String,
  password: String,
  createdAt: {
    type: Date,
    default: Date.now
  }
});

module.exports = mongoose.model("User", userSchema);

וזה נראה פשוט.

אבל זה שינוי גדול:

עכשיו יש ישויות שונות במערכת, לא רק רגשות.

🔐 שלב 2: למה צריך JWT?

ברגע שיש משתמשים, חייבים פתרון לשאלה:

איך המערכת יודעת מי אתה בכל בקשה?

האפשרויות:

לשלוח userId כל פעם (לא מאובטח)
לשמור session בצד שרת (כבד)
או להשתמש ב־JWT (מודרני ונפוץ)

בחרתי JWT.

⚙️ שלב 3: יצירת טוקן התחברות
const jwt = require("jsonwebtoken");
const bcrypt = require("bcryptjs");
const User = require("../models/User");

exports.login = async (req, res) => {
  const { email, password } = req.body;

  const user = await User.findOne({ email });
  if (!user) return res.status(400).json({ message: "User not found" });

  const isMatch = await bcrypt.compare(password, user.password);
  if (!isMatch) return res.status(400).json({ message: "Wrong password" });

  const token = jwt.sign(
    { userId: user._id },
    "SECRET_KEY",
    { expiresIn: "1d" }
  );

  res.json({ token });
};

ופה קורה משהו חשוב:

המערכת מתחילה “לזהות” משתמשים.

🧠 שינוי תפיסה עמוק

לפני JWT:

כל בקשה הייתה “אנונימית”

אחרי JWT:

כל בקשה נושאת זהות

וזה משנה הכל.

🧱 שלב 4: Middleware לאימות

כדי להגן על המערכת:

const jwt = require("jsonwebtoken");

module.exports = (req, res, next) => {
  const token = req.headers.authorization;

  if (!token) return res.status(401).json({ message: "No token" });

  try {
    const decoded = jwt.verify(token, "SECRET_KEY");
    req.userId = decoded.userId;
    next();
  } catch (err) {
    res.status(401).json({ message: "Invalid token" });
  }
};

וזה קריטי:

כל בקשה עכשיו עוברת דרך “שומר שער”.

🧩 חיבור רגשות למשתמשים

עכשיו משנים את ה־Emotion:

userId: {
  type: mongoose.Schema.Types.ObjectId,
  ref: "User"
}

ומאותו רגע:

רגש לא קיים לבד. הוא תמיד שייך למישהו.

⚙️ שינוי ב־Service
exports.createEmotion = async (data, userId) => {
  const emotion = new Emotion({
    ...data,
    userId
  });

  return await emotion.save();
};

וזה שינוי מבני חשוב מאוד:

המערכת כבר לא רק “שומרת רגשות”
היא שומרת “רגשות של אנשים”
🔥 ההבנה המרכזית של הפרק

זה לא פרק על אבטחה.

זה פרק על זהות.

כי ברגע שמוסיפים משתמשים:

מערכת הופכת מ־Data System ל־Human System.

⚠️ הטעות שנמנעה

בלי JWT:

כל משתמש היה רואה את כל הנתונים
אין הפרדה
אין פרטיות
אין מוצר אמיתי
🧠 שינוי החשיבה הסופי של הפרק

בשלב הזה כבר לא חשבתי:

“איך לשמור רגש?”

אלא:

“איך לשמור רגש בצורה שלא תתערבב בין אנשים?”

וזה כבר עולם אחר לגמרי.

🎯 סוף הפרק

עכשיו Smart Mood System יודע:

לנהל רגשות ✔
לשמור אותם במסד נתונים ✔
לזהות משתמשים ✔
להפריד מידע לפי זהות ✔

אבל עדיין חסר משהו אחד:

ממשק אמיתי שמציג את כל זה בצורה חכמה.