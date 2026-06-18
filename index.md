---
layout: home
title: Smart Mood System
---

<section class="hero" id="hero">
      <div class="overlay"></div>
      <div class="hero-content">
        <h1>Smart Mood System</h1>
        <h2>מסע הנדסי חי, מרעיון ועד מערכת SaaS אמיתית</h2>
        <p>
          מערכת חיה המתעדת בזמן אמת כיצד רעיון הופך לארכיטקטורה, לקוד ולמוצר
          אמיתי.
        </p>
        <a href="{{ '/journey-book/chapters/part-1-the-idea/01-how-it-all-started.html' | relative_url }}" class="btn read-book-btn"> התחל לקרוא </a>
      </div>
</section>

<section id="about" class="about-section">
      <div class="about-content">
        <span class="section-tag"> ABOUT </span>
        <h1>אודות</h1>
        <h2>אני יעקב דרילמן</h2>
        <p>
          הפרויקט הזה נולד מתוך רצון לחקור כיצד ניתן לקחת רגשות, מחשבות ודפוסים
          אנושיים ולהפוך אותם למערכת תוכנה מדידה.
        </p>
        <p>
          Smart Mood System משלב בין מסע למידה, תיעוד הנדסי ופיתוח של מוצר
          אמיתי.
        </p>
        <p>האתר משמש כספר דיגיטלי, כתיעוד ארכיטקטוני וכיומן פיתוח חי.</p>
      </div>
      <div class="about-image">
        <img class="profile-image" src="{{ '/assets/images/avatar.jpg' | relative_url }}" alt="Profile" />
      </div>
</section>

<section id="vision" class="vision-section">
      <div class="vision-overlay"></div>
      <div class="vision-content">
        <span class="section-tag"> VISION </span>
        <h1>החזון</h1>
        <h2>לחבר בין עולם הרגש לבין עולם ההנדסה והתוכנה</h2>
        <p>
          באמצעות יומן רגשות, ניתוח מגמות, תהליכי קבלת החלטות והמלצות מבוססות
          נתונים.
        </p>
        <p>להפוך מודעות עצמית לתהליך מדיד ומתועד.</p>
      </div>
</section>

 <section id="journey" class="split-section">
      <div class="split-content">
        <span class="section-tag"> ENGINEERING JOURNEY </span>
        <h1>ספר המסע</h1>
        <h2>הספר המתעד את הדרך</h2>
        <p>הספר מתעד את תהליך החשיבה מאחורי המערכת.</p>
        <p>
          החל מהרעיון הראשוני, דרך הארכיטקטורה, בחירת טכנולוגיות וקבלת החלטות
          הנדסיות.
        </p>
        <a href="{{ '/journey-book/chapters/part-1-the-idea/01-how-it-all-started.html' | relative_url }}" class="btn"> קרא את הספר </a>
      </div>
      <div class="split-image journey-image"></div>
</section>

<section id="build-log" class="split-section reverse">
      <div class="split-image build-image"></div>
      <div class="split-content">
        <span class="section-tag"> BUILD LOG </span>
        <h1>יומן הפיתוח</h1>
        <h2>המסע המעשי</h2>
        <p>יומן הפיתוח מתעד את הבנייה בפועל של Smart Mood System.</p>
        <ul class="feature-list">
          <li>Backend</li>
          <li>Frontend</li>
          <li>API</li>
          <li>Database</li>
          <li>Git & GitHub</li>
          <li>Cloud Deployment</li>
          <li>Architecture</li>
        </ul>
        <a href="{{ '/build-log/day-01.html' | relative_url }}" class="btn read-book-btn"> קרא את היומן </a>
      </div>
</section>

<footer>
      <h2>Smart Mood System</h2>
      <p>מסע הנדסי חי המתועד בזמן אמת</p>
      <p id="year"></p>
</footer>

<script>
      document.getElementById("year").innerHTML =
        "© " + new Date().getFullYear();
</script>
