---
title: "Portfolio"
date: 2026-09-08
draft: false
hidemeta: true
---

<div class="portfolio-cards">

<a class="portfolio-card" href="/portfolio/academic/">
  <h2>🎓 Academic</h2>
  <p>Talks, publications, and research.</p>
</a>

<a class="portfolio-card" href="/portfolio/races/">
  <h2>🏃 Races & Sport</h2>
  <p>Races I've run and other sport stuff.</p>
</a>

<a class="portfolio-card" href="/portfolio/photos/">
  <h2>📷 Photos</h2>
  <p>A few favorites, added as I go.</p>
</a>

</div>

<style>
.portfolio-cards {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
  gap: 1.2rem;
  margin-top: 1.5rem;
}
.portfolio-card {
  display: block;
  padding: 1.5rem;
  border-radius: 12px;
  border: 1px solid var(--border);
  background: var(--entry);
  text-decoration: none;
  color: var(--primary);
  transition: transform 0.15s ease, box-shadow 0.15s ease;
}
.portfolio-card:hover {
  transform: translateY(-3px);
  box-shadow: 0 6px 18px rgba(0,0,0,0.08);
}
.portfolio-card h2 {
  margin: 0 0 0.4rem 0;
  font-size: 1.15rem;
}
.portfolio-card p {
  margin: 0;
  font-size: 0.92rem;
  color: var(--secondary);
}
</style>