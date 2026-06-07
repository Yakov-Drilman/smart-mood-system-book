---
layout: default
title: Smart Mood System
body_class: home-page
---

<nav>
<a href="#hero">Hero</a>
  <a href="#about">About</a>
  <a href="#vision">Vision</a>
  <a href="#book">Engineering Journey</a>
  <a href="#project">Project Build Log</a>
</nav>

<section class="hero" id=hero>
  <h1>Smart Mood System</h1>

  <h2>מסע הנדסי חי, מסע מבניית רעיון למוצר SaaS</h2>

  <p>
מערכת חיה ומתפתחת שהופכת רעיונות לארכיטקטורה, קוד וחשיבה מוצר.
  </p>

<a href="{{ '/chapters/part-1-the-idea/01-how-it-all-started.html' | relative_url }}" class="read-book-btn">התחל לקרוא</a>

</section>


<section id="about" class="about-section">

  <div class="about-content">
    <h1>אודות</h1>

    <h2>אני יעקב דרילמן</h2>

    <p>
      הפרויקט הזה נולד מתוך רצון להבין כיצד אפשר לקחת חוויה אנושית
      מורכבת ולהפוך אותה למערכת תוכנה אמיתית.
    </p>
  </div>

  <img
    src="{{ '/assets/images/profile.jpg' | relative_url }}"
    alt="יעקב דרילמן"
    class="profile-image"
  >

</section>

<section id="vision"><h1>חזון</h1></section>

<section id="book">
<h1>הספר</h1>
<h2>
20 Chapters

From Idea To System

</h2>

<a href="{{ '/chapters/part-1-the-idea/01-how-it-all-started.html' | relative_url }}" class="read-book-btn">Read The Book</a>

</section>

<section id="project">
<h1>פרוייקט</h1>

<h2>
Follow The Build

Backend
Frontend
Database
Deployment

</h2>

<a href="#" class="read-book-btn">View Project Log</a>

</section>

<footer class="site-footer">
  <div class="footer-container">
    <p>&copy; <span id="year"></span> Smart Mood System</p>
  </div>
</footer>

<script>
  document.getElementById("year").textContent = new Date().getFullYear();
</script>
