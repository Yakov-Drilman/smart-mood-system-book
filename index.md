---
layout: default
title: Smart Mood System
body_class: home-page
---

<nav>
<a href="#hero">התחלה</a>
  <a href="#about">אודות</a>
  <a href="#vision">חזון</a>
  <a href="#book">מסע הנדסי</a>
  <a href="#project">יומן פרוייקט</a>
</nav>

<section class="hero" id=hero>
  <h1>Smart Mood System</h1>

  <h2>מסע הנדסי חי, מסע מבניית רעיון למוצר SaaS</h2>

  <p>
מערכת חיה ומתפתחת שהופכת רעיונות לארכיטקטורה, קוד וחשיבה מוצר.
  </p>

<a href="{{ '/journey-book/chapters/part-1-the-idea/01-how-it-all-started.html' | relative_url }}" class="read-book-btn">התחל לקרוא</a>

</section>

<section id="about" class="about-section">

  <div class="about-content">
    <h1>אודות</h1>
    <h2>אני יעקב דרילמן</h2>
    <p>
      הפרויקט הזה נולד מתוך רצון לחקור כיצד ניתן לקחת חוויה אנושית פנימית, רגשות, מחשבות ודפוסים, להפוך אותה למערכת תוכנה מדידה ומבוססת נתונים.
הפרויקט משמש גם כמסע למידה וגם כבסיס למוצר אמיתי.
</p>

  </div>

<img
src="{{ '/assets/images/profile.jpg' | relative_url }}"
alt="יעקב דרילמן"
class="profile-image"

>

</section>

<section id="vision">
<h1>חזון</h1>
החזון של Smart Mood System הוא לחבר בין עולם הרגש האנושי לבין עולם ההנדסה.

באמצעות שילוב של יומן רגשות, ניתוח מגמות, והמלצות מבוססות נתונים, המערכת שואפת להפוך מודעות עצמית לתהליך מדיד ומשופר לאורך זמן.

</section>

<section id="book">
<h1>הספר</h1>
<h2>
הספר "Engineering Journey" מתעד את תהליך הבנייה של המערכת מהשלב הראשון ועד למוצר שלם.

כל פרק מציג החלטות ארכיטקטוניות, אתגרים טכנולוגיים ותובנות שנולדו תוך כדי פיתוח אמיתי.

</h2>

<a href="{{ '/journey-book/chapters/part-1-the-idea/01-how-it-all-started.html' | relative_url }}" class="read-book-btn">קרא את הספר</a>

</section>

<section id="project">
<h1>פרוייקט</h1>

<h2>
Project Build Log הוא יומן הפיתוח הטכני של המערכת.

כאן מתועדים שלבי הפיתוח בפועל: Backend, Frontend, בסיסי נתונים, API, ארכיטקטורה ופריסה לענן.

זה החלק הטכני של המסע, בלי פילטרים, רק בנייה אמיתית.

</h2>

<a href="#" class="read-book-btn">קרא את יומן הפרויקט</a>

</section>

<footer class="site-footer">
  <div class="footer-container">
    <p>&copy; <span id="year"></span> Smart Mood System</p>
  </div>
</footer>

<script>
  document.getElementById("year").textContent = new Date().getFullYear();
</script>
