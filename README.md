<!DOCTYPE html>
<html lang="en" data-theme="light">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Shrishti — Storyteller & Media Professional</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,500;0,600;1,300;1,400;1,500&family=DM+Sans:ital,opsz,wght@0,9..40,300;0,9..40,400;0,9..40,500;1,9..40,300&display=swap" rel="stylesheet">
<style>
:root {
  --navy: #0d1b35;
  --navy-mid: #162444;
  --navy-soft: #1e3058;
  --blue-accent: #2b5fc9;
  --blue-light: #5b8fe8;
  --ivory: #f8f4ee;
  --ivory-warm: #f0ead8;
  --cream: #faf8f4;
  --text-primary: #0d1b35;
  --text-secondary: #3d4f6b;
  --text-muted: #7a8ba3;
  --bg-primary: #faf8f4;
  --bg-card: #ffffff;
  --bg-surface: #f2eee6;
  --border: rgba(13,27,53,0.1);
  --border-accent: rgba(43,95,201,0.25);
  --serif: 'Cormorant Garamond', Georgia, serif;
  --sans: 'DM Sans', system-ui, sans-serif;
  --transition: 0.35s cubic-bezier(0.25, 0.46, 0.45, 0.94);
}
[data-theme="dark"] {
  --text-primary: #e8e2d6;
  --text-secondary: #a8b8d0;
  --text-muted: #6a7d98;
  --bg-primary: #09111f;
  --bg-card: #0f1e35;
  --bg-surface: #0d1829;
  --border: rgba(232,226,214,0.08);
  --border-accent: rgba(91,143,232,0.3);
  --ivory: #1a2840;
  --ivory-warm: #14202f;
  --cream: #09111f;
}
*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
html { scroll-behavior: smooth; font-size: 16px; }
body {
  font-family: var(--sans);
  background: var(--bg-primary);
  color: var(--text-primary);
  overflow-x: hidden;
  cursor: none;
  transition: background var(--transition), color var(--transition);
}
body.loaded #loader { opacity: 0; pointer-events: none; }

/* ── CUSTOM CURSOR ── */
#cursor, #cursor-trail {
  position: fixed; border-radius: 50%; pointer-events: none; z-index: 9999; transition: transform 0.15s;
}
#cursor { width: 8px; height: 8px; background: var(--blue-accent); top: -4px; left: -4px; }
#cursor-trail { width: 32px; height: 32px; border: 1.5px solid var(--blue-accent); opacity: 0.4; top: -16px; left: -16px; transition: top 0.12s, left 0.12s, transform 0.2s; }
@media (hover: none) { #cursor, #cursor-trail { display: none; } body { cursor: auto; } }

/* ── SCROLL PROGRESS ── */
#scroll-bar {
  position: fixed; top: 0; left: 0; height: 2px; width: 0%; background: linear-gradient(90deg, var(--blue-accent), var(--blue-light)); z-index: 1000; transition: width 0.1s;
}

/* ── LOADER ── */
#loader {
  position: fixed; inset: 0; background: var(--navy); z-index: 9998; display: flex; align-items: center; justify-content: center; flex-direction: column; gap: 1.5rem; transition: opacity 0.6s ease;
}
#loader .loader-name { font-family: var(--serif); font-size: clamp(2.5rem, 6vw, 4.5rem); color: #e8e2d6; font-weight: 300; letter-spacing: 0.08em; opacity: 0; animation: fadeIn 0.8s 0.3s forwards; }
#loader .loader-line { width: 0; height: 1px; background: rgba(91,143,232,0.6); animation: expand 1.2s 0.6s forwards; }
@keyframes fadeIn { to { opacity: 1; } }
@keyframes expand { to { width: 180px; } }

/* ── THEME TOGGLE ── */
#theme-toggle {
  position: fixed; top: 1.5rem; right: 1.5rem; z-index: 500; background: var(--bg-card); border: 1px solid var(--border); border-radius: 50px; padding: 0.5rem 1rem; font-family: var(--sans); font-size: 0.75rem; font-weight: 500; color: var(--text-secondary); cursor: none; display: flex; align-items: center; gap: 0.5rem; letter-spacing: 0.06em; text-transform: uppercase; transition: all var(--transition); backdrop-filter: blur(10px);
}
#theme-toggle:hover { background: var(--blue-accent); color: white; border-color: transparent; }
#theme-toggle svg { width: 14px; height: 14px; }

/* ── NAV ── */
nav {
  position: fixed; top: 0; left: 0; right: 0; z-index: 200; padding: 1.25rem 3rem; display: flex; align-items: center; justify-content: space-between; transition: all var(--transition);
}
nav.scrolled { background: var(--bg-primary); border-bottom: 1px solid var(--border); backdrop-filter: blur(20px); padding: 0.9rem 3rem; }
.nav-logo { font-family: var(--serif); font-size: 1.4rem; font-weight: 400; color: var(--text-primary); text-decoration: none; letter-spacing: 0.04em; font-style: italic; }
.nav-links { display: flex; gap: 2.5rem; list-style: none; }
.nav-links a { font-size: 0.75rem; text-transform: uppercase; letter-spacing: 0.12em; color: var(--text-secondary); text-decoration: none; font-weight: 500; transition: color var(--transition); position: relative; }
.nav-links a::after { content: ''; position: absolute; bottom: -2px; left: 0; width: 0; height: 1px; background: var(--blue-accent); transition: width var(--transition); }
.nav-links a:hover { color: var(--text-primary); }
.nav-links a:hover::after { width: 100%; }
.nav-hamburger { display: none; flex-direction: column; gap: 5px; background: none; border: none; cursor: none; padding: 4px; }
.nav-hamburger span { width: 22px; height: 1.5px; background: var(--text-primary); display: block; transition: all var(--transition); }
@media (max-width: 768px) {
  nav { padding: 1rem 1.5rem; }
  nav.scrolled { padding: 0.8rem 1.5rem; }
  .nav-links { display: none; position: fixed; inset: 0; background: var(--bg-primary); flex-direction: column; align-items: center; justify-content: center; gap: 3rem; z-index: 100; }
  .nav-links.open { display: flex; }
  .nav-links a { font-size: 1rem; }
  .nav-hamburger { display: flex; z-index: 101; }
}

/* ── HERO ── */
#hero {
  min-height: 100vh; display: flex; align-items: center; position: relative; overflow: hidden; background: var(--bg-primary);
  padding: 8rem 3rem 5rem;
}
.hero-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 4rem; align-items: center; max-width: 1200px; margin: 0 auto; width: 100%; }
.hero-text { }
.hero-eyebrow { font-size: 0.7rem; text-transform: uppercase; letter-spacing: 0.2em; color: var(--blue-accent); margin-bottom: 1.5rem; font-weight: 500; display: flex; align-items: center; gap: 0.75rem; }
.hero-eyebrow::before { content: ''; width: 30px; height: 1px; background: var(--blue-accent); display: inline-block; }
.hero-name { font-family: var(--serif); font-size: clamp(4rem, 8vw, 7rem); font-weight: 300; line-height: 0.95; letter-spacing: -0.01em; color: var(--text-primary); margin-bottom: 1.5rem; }
.hero-name em { font-style: italic; color: var(--blue-accent); }
.hero-headline { font-family: var(--serif); font-size: clamp(1.1rem, 2.2vw, 1.4rem); font-weight: 300; line-height: 1.65; color: var(--text-secondary); margin-bottom: 2.5rem; max-width: 480px; }
.hero-roles { display: flex; flex-wrap: wrap; gap: 0.6rem; margin-bottom: 3rem; }
.role-tag { font-size: 0.72rem; padding: 0.35rem 1rem; border: 1px solid var(--border-accent); border-radius: 50px; color: var(--text-secondary); letter-spacing: 0.06em; text-transform: uppercase; font-weight: 500; transition: all var(--transition); }
.role-tag:hover { background: var(--blue-accent); color: white; border-color: var(--blue-accent); }
.hero-cta { display: flex; gap: 1rem; flex-wrap: wrap; }
.btn-primary { padding: 0.85rem 2.2rem; background: var(--navy); color: var(--ivory); font-family: var(--sans); font-size: 0.8rem; font-weight: 500; text-transform: uppercase; letter-spacing: 0.1em; border: none; border-radius: 2px; cursor: none; text-decoration: none; transition: all var(--transition); display: inline-block; }
.btn-primary:hover { background: var(--blue-accent); transform: translateY(-2px); }
[data-theme="dark"] .btn-primary { background: var(--blue-accent); }
[data-theme="dark"] .btn-primary:hover { background: var(--blue-light); }
.btn-ghost { padding: 0.85rem 2.2rem; background: transparent; color: var(--text-primary); font-family: var(--sans); font-size: 0.8rem; font-weight: 500; text-transform: uppercase; letter-spacing: 0.1em; border: 1px solid var(--border); border-radius: 2px; cursor: none; text-decoration: none; transition: all var(--transition); display: inline-block; }
.btn-ghost:hover { border-color: var(--blue-accent); color: var(--blue-accent); transform: translateY(-2px); }
.hero-visual { position: relative; display: flex; justify-content: center; }
.hero-frame {
  width: 100%; max-width: 420px; aspect-ratio: 3/4; background: var(--bg-surface); border: 1px solid var(--border); position: relative; overflow: hidden;
}
.hero-frame-inner { position: absolute; inset: 0; display: flex; align-items: center; justify-content: center; flex-direction: column; gap: 1rem; }
.hero-placeholder-img { width: 80%; height: 70%; background: linear-gradient(135deg, var(--navy-soft) 0%, #2b5fc9 100%); opacity: 0.15; }
.hero-monogram { position: absolute; font-family: var(--serif); font-size: 9rem; font-weight: 300; color: var(--text-primary); opacity: 0.06; bottom: -1rem; right: 1rem; line-height: 1; letter-spacing: -0.05em; user-select: none; }
.hero-caption { position: absolute; bottom: 1.5rem; left: 1.5rem; font-size: 0.65rem; text-transform: uppercase; letter-spacing: 0.15em; color: var(--text-muted); }
.hero-number { position: absolute; top: 1.5rem; right: 1.5rem; font-family: var(--serif); font-size: 4rem; font-weight: 300; color: var(--text-primary); opacity: 0.06; line-height: 1; }
.floating-badge { position: absolute; bottom: 2rem; left: -2rem; background: var(--bg-card); border: 1px solid var(--border); padding: 1rem 1.25rem; max-width: 200px; }
.floating-badge p { font-family: var(--serif); font-size: 1rem; font-weight: 400; line-height: 1.4; color: var(--text-primary); font-style: italic; }
.floating-badge span { font-size: 0.65rem; text-transform: uppercase; letter-spacing: 0.1em; color: var(--text-muted); display: block; margin-top: 0.5rem; }
@media (max-width: 900px) {
  #hero { padding: 7rem 1.5rem 4rem; }
  .hero-grid { grid-template-columns: 1fr; gap: 3rem; }
  .hero-visual { order: -1; }
  .hero-frame { max-width: 300px; }
  .floating-badge { left: 0; }
}
.hero-bg-text { position: absolute; bottom: 0; right: 0; font-family: var(--serif); font-size: clamp(5rem, 14vw, 12rem); font-weight: 300; color: var(--text-primary); opacity: 0.025; line-height: 1; pointer-events: none; white-space: nowrap; letter-spacing: -0.03em; }

/* ── SECTION BASE ── */
section { padding: 6rem 3rem; max-width: 1200px; margin: 0 auto; }
.section-eyebrow { font-size: 0.7rem; text-transform: uppercase; letter-spacing: 0.2em; color: var(--blue-accent); margin-bottom: 1rem; font-weight: 500; display: flex; align-items: center; gap: 0.75rem; }
.section-eyebrow::before { content: ''; width: 20px; height: 1px; background: var(--blue-accent); display: inline-block; }
.section-title { font-family: var(--serif); font-size: clamp(2rem, 4.5vw, 3.5rem); font-weight: 300; line-height: 1.15; color: var(--text-primary); margin-bottom: 1rem; }
.section-subtitle { font-size: 1.05rem; color: var(--text-secondary); line-height: 1.7; max-width: 600px; }
@media (max-width: 768px) { section { padding: 4rem 1.5rem; } }

/* ── DIVIDER ── */
.section-divider { width: 100%; height: 1px; background: var(--border); }

/* ── ABOUT ── */
.about-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 5rem; align-items: start; margin-top: 4rem; }
.about-quote { font-family: var(--serif); font-size: clamp(1.6rem, 3.5vw, 2.4rem); font-weight: 300; line-height: 1.35; color: var(--text-primary); font-style: italic; position: relative; padding-left: 2rem; border-left: 2px solid var(--blue-accent); margin-bottom: 2.5rem; }
.about-bio { font-size: 1rem; line-height: 1.85; color: var(--text-secondary); }
.about-bio p + p { margin-top: 1.25rem; }
.strengths-grid { display: grid; grid-template-columns: repeat(2, 1fr); gap: 0.75rem; }
.strength-item { padding: 0.9rem 1rem; border: 1px solid var(--border); display: flex; align-items: center; gap: 0.75rem; transition: all var(--transition); }
.strength-item:hover { border-color: var(--blue-accent); background: var(--bg-surface); transform: translateX(4px); }
.strength-dot { width: 6px; height: 6px; border-radius: 50%; background: var(--blue-accent); flex-shrink: 0; }
.strength-name { font-size: 0.82rem; font-weight: 500; letter-spacing: 0.04em; }
@media (max-width: 900px) { .about-grid { grid-template-columns: 1fr; gap: 3rem; } }

/* ── STATS ── */
#stats { background: var(--navy); padding: 5rem 3rem; max-width: none; }
.stats-inner { max-width: 1200px; margin: 0 auto; display: grid; grid-template-columns: repeat(4, 1fr); gap: 3rem; }
.stat-item { text-align: center; }
.stat-number { font-family: var(--serif); font-size: clamp(2.5rem, 5vw, 4rem); font-weight: 300; color: #e8e2d6; line-height: 1; margin-bottom: 0.5rem; }
.stat-label { font-size: 0.7rem; text-transform: uppercase; letter-spacing: 0.15em; color: rgba(232,226,214,0.5); font-weight: 500; }
@media (max-width: 768px) { .stats-inner { grid-template-columns: repeat(2, 1fr); gap: 2rem; } #stats { padding: 4rem 1.5rem; } }

/* ── TIMELINE ── */
.timeline { margin-top: 4rem; position: relative; }
.timeline::before { content: ''; position: absolute; left: 140px; top: 0; bottom: 0; width: 1px; background: var(--border); }
.timeline-item { display: grid; grid-template-columns: 140px 1fr; gap: 0; margin-bottom: 3.5rem; position: relative; }
.timeline-year { font-family: var(--serif); font-size: 1.75rem; font-weight: 300; color: var(--text-muted); padding-right: 2.5rem; text-align: right; padding-top: 0.1rem; }
.timeline-content { padding-left: 2.5rem; position: relative; }
.timeline-content::before { content: ''; position: absolute; left: -4px; top: 10px; width: 8px; height: 8px; border-radius: 50%; background: var(--bg-primary); border: 2px solid var(--blue-accent); }
.timeline-item:hover .timeline-content::before { background: var(--blue-accent); }
.timeline-title { font-family: var(--serif); font-size: 1.35rem; font-weight: 400; margin-bottom: 0.5rem; color: var(--text-primary); }
.timeline-desc { font-size: 0.92rem; color: var(--text-secondary); line-height: 1.7; }
@media (max-width: 600px) {
  .timeline::before { left: 0; }
  .timeline-item { grid-template-columns: 1fr; padding-left: 1.5rem; }
  .timeline-year { text-align: left; padding-right: 0; font-size: 1.1rem; margin-bottom: 0.25rem; }
  .timeline-content { padding-left: 1.5rem; }
  .timeline-content::before { left: -1.5rem; }
}

/* ── ACHIEVEMENTS ── */
.achievements-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(280px, 1fr)); gap: 1.5rem; margin-top: 3.5rem; }
.achievement-card { background: var(--bg-card); border: 1px solid var(--border); padding: 2rem; transition: all var(--transition); position: relative; overflow: hidden; }
.achievement-card::before { content: ''; position: absolute; top: 0; left: 0; width: 3px; height: 0; background: var(--blue-accent); transition: height 0.4s; }
.achievement-card:hover { transform: translateY(-4px); border-color: var(--border-accent); box-shadow: 0 20px 40px rgba(13,27,53,0.08); }
.achievement-card:hover::before { height: 100%; }
[data-theme="dark"] .achievement-card:hover { box-shadow: 0 20px 40px rgba(0,0,0,0.3); }
.achievement-icon { font-family: var(--serif); font-size: 2.5rem; color: var(--blue-accent); opacity: 0.4; line-height: 1; margin-bottom: 1rem; font-weight: 300; }
.achievement-title { font-family: var(--serif); font-size: 1.2rem; font-weight: 500; color: var(--text-primary); margin-bottom: 0.5rem; }
.achievement-desc { font-size: 0.85rem; color: var(--text-secondary); line-height: 1.65; }

/* ── GALLERY ── */
.gallery-header { display: flex; justify-content: space-between; align-items: flex-end; margin-bottom: 2.5rem; }
.gallery-grid { display: grid; grid-template-columns: 2fr 1fr 1fr; grid-template-rows: auto auto; gap: 1rem; }
.gallery-item { overflow: hidden; position: relative; cursor: none; }
.gallery-item:first-child { grid-row: 1 / 3; }
.gallery-img { width: 100%; height: 100%; min-height: 200px; object-fit: cover; display: block; background: var(--bg-surface); transition: transform 0.6s cubic-bezier(0.25,0.46,0.45,0.94); }
.gallery-item:hover .gallery-img { transform: scale(1.04); }
.gallery-placeholder { width: 100%; height: 100%; min-height: 200px; display: flex; align-items: center; justify-content: center; flex-direction: column; gap: 0.5rem; background: var(--bg-surface); }
.gallery-item:first-child .gallery-placeholder { min-height: 420px; }
.gallery-placeholder-icon { font-family: var(--serif); font-size: 2.5rem; color: var(--text-muted); opacity: 0.3; }
.gallery-placeholder-label { font-size: 0.65rem; text-transform: uppercase; letter-spacing: 0.15em; color: var(--text-muted); }
.gallery-overlay { position: absolute; inset: 0; background: linear-gradient(to top, rgba(13,27,53,0.7) 0%, transparent 50%); opacity: 0; transition: opacity var(--transition); display: flex; align-items: flex-end; padding: 1.25rem; }
.gallery-item:hover .gallery-overlay { opacity: 1; }
.gallery-caption { font-family: var(--serif); font-size: 0.9rem; color: white; font-style: italic; }
@media (max-width: 768px) { .gallery-grid { grid-template-columns: 1fr 1fr; grid-template-rows: none; } .gallery-item:first-child { grid-row: auto; grid-column: 1 / 3; } }

/* ── SKILLS ── */
.skills-grid { display: grid; grid-template-columns: repeat(2, 1fr); gap: 1rem; margin-top: 3.5rem; max-width: 700px; }
.skill-row { }
.skill-label { display: flex; justify-content: space-between; margin-bottom: 0.4rem; }
.skill-name { font-size: 0.8rem; font-weight: 500; text-transform: uppercase; letter-spacing: 0.08em; color: var(--text-secondary); }
.skill-pct { font-size: 0.8rem; color: var(--text-muted); font-family: var(--serif); }
.skill-track { height: 2px; background: var(--border); position: relative; overflow: hidden; }
.skill-fill { height: 100%; background: var(--blue-accent); width: 0; transition: width 1.2s cubic-bezier(0.4, 0, 0.2, 1); }

/* ── ASPIRATIONS ── */
.aspirations-inner { display: grid; grid-template-columns: 1fr 2fr; gap: 5rem; align-items: center; margin-top: 4rem; }
.aspirations-visual { }
.aspirations-circle { width: 100%; aspect-ratio: 1; max-width: 300px; border-radius: 50%; border: 1px solid var(--border-accent); display: flex; align-items: center; justify-content: center; position: relative; margin: 0 auto; }
.aspirations-circle::before { content: ''; position: absolute; inset: 15px; border-radius: 50%; border: 1px dashed var(--border-accent); animation: spin 20s linear infinite; }
.aspirations-circle-text { font-family: var(--serif); font-size: 3.5rem; font-weight: 300; color: var(--blue-accent); }
@keyframes spin { to { transform: rotate(360deg); } }
.aspirations-content p { font-family: var(--serif); font-size: 1.2rem; font-weight: 300; line-height: 1.8; color: var(--text-secondary); }
.aspiration-tags { display: flex; flex-wrap: wrap; gap: 0.6rem; margin-top: 2rem; }
.aspiration-tag { padding: 0.5rem 1.2rem; border: 1px solid var(--border-accent); font-size: 0.78rem; color: var(--blue-accent); letter-spacing: 0.06em; font-weight: 500; text-transform: uppercase; border-radius: 50px; transition: all var(--transition); }
.aspiration-tag:hover { background: var(--blue-accent); color: white; border-color: var(--blue-accent); }
@media (max-width: 900px) { .aspirations-inner { grid-template-columns: 1fr; gap: 3rem; } .aspirations-circle { max-width: 200px; } }

/* ── RESUME ── */
.resume-card { background: var(--navy); color: #e8e2d6; padding: 3.5rem; display: grid; grid-template-columns: 1fr auto; gap: 3rem; align-items: center; margin-top: 3.5rem; }
.resume-title { font-family: var(--serif); font-size: 2rem; font-weight: 300; margin-bottom: 0.75rem; }
.resume-desc { font-size: 0.9rem; color: rgba(232,226,214,0.6); line-height: 1.7; max-width: 500px; }
.resume-btn { display: flex; align-items: center; gap: 0.75rem; padding: 1rem 2rem; background: transparent; border: 1px solid rgba(232,226,214,0.3); color: #e8e2d6; font-family: var(--sans); font-size: 0.78rem; text-transform: uppercase; letter-spacing: 0.1em; font-weight: 500; text-decoration: none; cursor: none; transition: all var(--transition); white-space: nowrap; }
.resume-btn:hover { background: var(--blue-accent); border-color: var(--blue-accent); transform: translateY(-2px); }
.resume-btn svg { width: 16px; height: 16px; }
@media (max-width: 768px) { .resume-card { grid-template-columns: 1fr; gap: 2rem; padding: 2.5rem 2rem; } }

/* ── CONTACT ── */
.contact-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 5rem; margin-top: 4rem; }
.contact-intro { font-family: var(--serif); font-size: clamp(1.5rem, 3vw, 2.2rem); font-weight: 300; line-height: 1.45; color: var(--text-primary); margin-bottom: 2rem; }
.contact-links { list-style: none; display: flex; flex-direction: column; gap: 1rem; }
.contact-link-item a { display: flex; align-items: center; gap: 1rem; text-decoration: none; color: var(--text-secondary); font-size: 0.9rem; font-weight: 500; transition: all var(--transition); group: true; padding: 1rem; border: 1px solid var(--border); }
.contact-link-item a:hover { color: var(--blue-accent); border-color: var(--blue-accent); padding-left: 1.5rem; }
.contact-link-icon { width: 20px; height: 20px; opacity: 0.6; }
.contact-link-item a:hover .contact-link-icon { opacity: 1; }
.contact-form { display: flex; flex-direction: column; gap: 1rem; }
.contact-field { }
.contact-field label { display: block; font-size: 0.7rem; text-transform: uppercase; letter-spacing: 0.1em; color: var(--text-muted); margin-bottom: 0.5rem; font-weight: 500; }
.contact-field input, .contact-field textarea { width: 100%; padding: 0.85rem 1rem; background: transparent; border: 1px solid var(--border); color: var(--text-primary); font-family: var(--sans); font-size: 0.92rem; outline: none; transition: border-color var(--transition); resize: vertical; }
.contact-field input:focus, .contact-field textarea:focus { border-color: var(--blue-accent); }
@media (max-width: 768px) { .contact-grid { grid-template-columns: 1fr; gap: 3rem; } }

/* ── FOOTER ── */
footer { background: var(--navy); color: #e8e2d6; padding: 3rem; text-align: center; }
footer p { font-family: var(--serif); font-size: 1rem; font-weight: 300; color: rgba(232,226,214,0.5); }
footer .footer-name { font-size: 1.2rem; color: #e8e2d6; margin-bottom: 0.5rem; font-style: italic; }

/* ── REVEAL ANIMATIONS ── */
.reveal { opacity: 0; transform: translateY(30px); transition: opacity 0.7s ease, transform 0.7s ease; }
.reveal.visible { opacity: 1; transform: none; }
.reveal-delay-1 { transition-delay: 0.1s; }
.reveal-delay-2 { transition-delay: 0.2s; }
.reveal-delay-3 { transition-delay: 0.3s; }

/* ── MOBILE MENU ACTIVE ── */
.nav-hamburger.open span:nth-child(1) { transform: rotate(45deg) translate(5px, 5px); }
.nav-hamburger.open span:nth-child(2) { opacity: 0; }
.nav-hamburger.open span:nth-child(3) { transform: rotate(-45deg) translate(5px, -5px); }
</style>
</head>
<body>

<div id="loader">
  <div class="loader-name">Shrishti</div>
  <div class="loader-line"></div>
</div>

<div id="scroll-bar"></div>
<div id="cursor"></div>
<div id="cursor-trail"></div>

<button id="theme-toggle" aria-label="Toggle theme">
  <svg id="sun-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><circle cx="12" cy="12" r="5"/><path d="M12 1v2M12 21v2M4.22 4.22l1.42 1.42M18.36 18.36l1.42 1.42M1 12h2M21 12h2M4.22 19.78l1.42-1.42M18.36 5.64l1.42-1.42"/></svg>
  <svg id="moon-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" style="display:none"><path d="M21 12.79A9 9 0 1 1 11.21 3 7 7 0 0 0 21 12.79z"/></svg>
  <span id="theme-label">Dark</span>
</button>

<nav id="main-nav">
  <a href="#" class="nav-logo">Shrishti</a>
  <ul class="nav-links" id="nav-links">
    <li><a href="#about">About</a></li>
    <li><a href="#story">Story</a></li>
    <li><a href="#achievements">Work</a></li>
    <li><a href="#skills">Skills</a></li>
    <li><a href="#contact">Contact</a></li>
  </ul>
  <button class="nav-hamburger" id="hamburger" aria-label="Menu">
    <span></span><span></span><span></span>
  </button>
</nav>

<!-- ── HERO ── -->
<header id="hero">
  <div class="hero-grid">
    <div class="hero-text">
      <p class="hero-eyebrow reveal">Portfolio</p>
      <h1 class="hero-name reveal reveal-delay-1">Shrish<em>ti</em></h1>
      <p class="hero-headline reveal reveal-delay-2">Collecting stories, chasing ideas, and pretending I have my life figured out.</p>
      <div class="hero-roles reveal reveal-delay-2">
        <span class="role-tag">Student</span>
        <span class="role-tag">Content Creator</span>
        <span class="role-tag">Storyteller</span>
        <span class="role-tag">Communicator</span>
       <span class="role-tag">Aspiring Media Professional</span>
      </div>
      <div class="hero-cta reveal reveal-delay-3">
        <a href="#about" class="btn-primary">Explore My Story</a>
        <a href="#contact" class="btn-ghost">Let's Connect</a>
      </div>
    </div>
    <div class="hero-visual reveal reveal-delay-2">
      <div class="hero-frame">
        <div class="hero-frame-inner">
          <div style="width:100%;height:100%;display:flex;align-items:center;justify-content:center;flex-direction:column;gap:0.5rem;padding:2rem">
            <div style="width:80px;height:80px;border-radius:50%;border:1px solid var(--border-accent);display:flex;align-items:center;justify-content:center;margin-bottom:1rem">
              <span style="font-family:var(--serif);font-size:2rem;font-weight:300;color:var(--blue-accent)">S</span>
            </div>
            <p style="font-family:var(--serif);font-size:0.85rem;font-style:italic;color:var(--text-muted);text-align:center;padding:0 1rem">Photograph Coming Soon</p>
          </div>
        </div>
        <div class="hero-monogram">S</div>
        <div class="hero-caption">Portfolio 2026</div>
        <div class="hero-number">01</div>
      </div>
      <div class="floating-badge reveal reveal-delay-3">
        <p>"Curiosity opens the door. Communication brings people in."</p>
        <span>— Shrishti</span>
      </div>
    </div>
  </div>
  <div class="hero-bg-text">Stories</div>
</header>

<div class="section-divider"></div>

<!-- ── HIGHLIGHTS ── -->
<div id="stats">
  <div class="stats-inner">

    <div class="stat-item reveal">
      <div class="stat-number">💡</div>
      <div class="stat-label">Creative Thinker</div>
    </div>

    <div class="stat-item reveal reveal-delay-1">
      <div class="stat-number">🗣️</div>
      <div class="stat-label">Great With People</div>
    </div>

    <div class="stat-item reveal reveal-delay-2">
      <div class="stat-number">🔍</div>
      <div class="stat-label">Naturally Curious</div>
    </div>

    <div class="stat-item reveal reveal-delay-3">
      <div class="stat-number">✨</div>
      <div class="stat-label">Observant Storyteller</div>
    </div>

  </div>
</div>

<!-- ── ABOUT ── -->
<section id="about">
  <div class="section-eyebrow reveal">About Me</div>
  <h2 class="section-title reveal">I don't just consume stories.<br>I study people, collect<br>experiences, and create my own.</h2>
  <div class="about-grid">
    <div>
      <blockquote class="about-quote reveal">
        Hi, I'm Shrishti.

I've always been the person asking one more question, starting one more conversation, and somehow ending up knowing everyone's life story.

I'm fascinated by people — what they think, what they create, what they dream about, and why certain stories stay with us long after they're told.

Right now I'm exploring media, communication, content creation, photography, and digital storytelling while trying to turn curiosity into something meaningful.      </blockquote>
      <div class="about-bio reveal">
        <p>I love understanding what makes people think, feel, and connect. Whether I'm leading a team, creating content, observing trends, or simply talking to someone new, I'm always searching for ideas worth sharing and stories worth telling.</p>
        <p>My curiosity pushes me to explore beyond the obvious, and my ambition pushes me to turn those discoveries into meaningful work.</p>
      </div>
    </div>
    <div>
     <p class="section-eyebrow reveal" style="margin-bottom:1.5rem">Things I Bring To The Table</p>

<div class="strengths-grid">
  <div class="strength-item reveal"><span class="strength-dot"></span><span class="strength-name">Communication</span></div>

  <div class="strength-item reveal reveal-delay-1"><span class="strength-dot"></span><span class="strength-name">Creative Thinking</span></div>

  <div class="strength-item reveal"><span class="strength-dot"></span><span class="strength-name">Storytelling</span></div>

  <div class="strength-item reveal reveal-delay-1"><span class="strength-dot"></span><span class="strength-name">Public Speaking</span></div>

  <div class="strength-item reveal"><span class="strength-dot"></span><span class="strength-name">Curiosity</span></div>

  <div class="strength-item reveal reveal-delay-1"><span class="strength-dot"></span><span class="strength-name">Trend Awareness</span></div>

  <div class="strength-item reveal"><span class="strength-dot"></span><span class="strength-name">Adaptability</span></div>

  <div class="strength-item reveal reveal-delay-1"><span class="strength-dot"></span><span class="strength-name">People Skills</span></div>
</div>
</div>
</section>

<div class="section-divider"></div>

<!-- ── STORY ── -->
<section id="story">
  <div class="section-eyebrow reveal">My Journey</div>
  <h2 class="section-title reveal">The story so far</h2>
  <p class="section-subtitle reveal">Every chapter shaped who I'm becoming. Here's how it unfolded.</p>

  <div class="timeline">
    <div class="timeline-item reveal">
      <div class="timeline-year">Chapter 1</div>
      <div class="timeline-content">
        <h3 class="timeline-title">The Curious Child</h3>
        <p class="timeline-desc">Born with an insatiable need to understand the world. I explored everything — books, art, music, people. Every question led to a dozen more. Curiosity wasn't just a trait; it was a lifestyle.</p>
      </div>
    </div>
    <div class="timeline-item reveal">
      <div class="timeline-year">Chapter 2</div>
      <div class="timeline-content">
        <h3 class="timeline-title">The Competitor</h3>
        <p class="timeline-desc">I threw myself into competitions — singing, drawing, painting, quizzes, recitation, spell bee, and cultural events. Stage fright was never an option. I showed up, I performed, I learned.</p>
      </div>
    </div>
    <div class="timeline-item reveal">
      <div class="timeline-year">Chapter 3</div>
      <div class="timeline-content">
        <h3 class="timeline-title">The Achiever</h3>
        <p class="timeline-desc">First place. Second place. Third place. Participation that counted. Years of earning certificates taught me that showing up with full effort always leaves a mark — regardless of the final rank.</p>
      </div>
    </div>
    <div class="timeline-item reveal">
      <div class="timeline-year">Chapter 4</div>
      <div class="timeline-content">
        <h3 class="timeline-title">Stepping Up</h3>
<p class="timeline-desc">When the opportunity appeared, I stepped forward and took on the role of School Head Girl. The experience taught me confidence, responsibility, communication, and how to represent others with maturity. It showed me that leadership is often less about being chosen and more about being willing to step up.</p>      </div>
    </div>
    <div class="timeline-item reveal">
      <div class="timeline-year">Chapter 5</div>
      <div class="timeline-content">
        <h3 class="timeline-title">The Digital Explorer</h3>
<p class="timeline-desc">Social media became more than entertainment for me. I became fascinated by online trends, digital culture, content formats, and the way people connect through screens. The internet became a place where curiosity could run wild.</p> </div>
    </div>
    <div class="timeline-item reveal">
      <div class="timeline-year">Chapter 6</div>
      <div class="timeline-content">
        <h3 class="timeline-title">The Content Creator</h3>
        <p class="timeline-desc">A passion for content creation and media ignited. I started understanding the architecture of stories — how they're built, why they spread, and what makes people stop scrolling and actually feel something.</p>
      </div>
    </div>
<div class="timeline-item reveal">
  <div class="timeline-year">2026</div>
  <div class="timeline-content">
    <h3 class="timeline-title">The Professional Beginning</h3>
    <p class="timeline-desc">
      In March 2026, I completed a remote Content Writing Internship with InAmigos NGO Foundation.

      It was my first experience working in a professional environment and taught me how communication, writing, and teamwork operate beyond the classroom.

      The internship strengthened my interest in media, storytelling, and digital communication.
    </p>
  </div>
</div>
    <div class="timeline-item reveal">
      <div class="timeline-year">Now</div>
      <div class="timeline-content">
        <h3 class="timeline-title">The Journey Ahead</h3>
        <p class="timeline-desc">Currently pursuing a future in communication, media, and digital storytelling.

My goal is to keep learning, creating, connecting with people, and building meaningful experiences through media and communication.

The story is still being written, and the best chapters are yet to come.
</p>

    </div>
    </div>
  </div>
</section>

<div class="section-divider"></div>

<!-- ── ACHIEVEMENTS ── -->
<section id="achievements">
  <div class="section-eyebrow reveal">Recognition</div>
  <h2 class="section-title reveal">Achievements & Experience</h2>
  <p class="section-subtitle reveal">A career built on showing up fully, in every room, on every stage.</p>
  <div class="achievements-grid">
    <div class="achievement-card reveal">
      <div class="achievement-icon">★</div>
      <h3 class="achievement-title">School Head Girl</h3>
      <p class="achievement-desc">Elected to lead the student body — representing the school, mentoring peers, and setting a standard of excellence and integrity in everything I did.</p>
    </div>
    <div class="achievement-card reveal reveal-delay-1">
      <div class="achievement-icon">◈</div>
      <h3 class="achievement-title">English Olympiad Participant</h3>
      <p class="achievement-desc">Competed at the national level in the English Olympiad, demonstrating strong command of language, comprehension, and analytical thinking.</p>
    </div>
    <div class="achievement-card reveal reveal-delay-2">
      <div class="achievement-icon">◎</div>
      <h3 class="achievement-title">Academic & Co-curricular Awards</h3>
      <p class="achievement-desc">Earned multiple first, second, and third place certificates across academics and co-curricular competitions throughout my school years.</p>
    </div>
    <div class="achievement-card reveal">
      <div class="achievement-icon">⊕</div>
      <h3 class="achievement-title">Investigatory Projects</h3>
      <p class="achievement-desc">Designed and executed in-depth investigatory projects, demonstrating research skills, analytical thinking, and the ability to present complex ideas clearly.</p>
    </div>
    <div class="achievement-card reveal reveal-delay-1">
      <div class="achievement-icon">♦</div>
      <h3 class="achievement-title">Public Speaking & Hosting</h3>
      <p class="achievement-desc">Hosted school events, delivered speeches, and competed in recitation and debate. Comfortable behind the mic and in front of an audience.</p>
    </div>
    <div class="achievement-card reveal reveal-delay-2">
      <div class="achievement-icon">◇</div>
      <h3 class="achievement-title">Creative Competitions</h3>
      <p class="achievement-desc">Participated in singing, drawing, painting, spell bee, and cultural events — building a multidisciplinary creative foundation across arts and culture.</p>
    </div>
    <div class="achievement-card reveal">
      <div class="achievement-icon">∞</div>
      <h3 class="achievement-title">Community Building</h3>
      <p class="achievement-desc">Built and managed online communities and social media pages, learning what it truly takes to grow engaged audiences and foster meaningful digital connections.</p>
    </div>
  </div>
</section>

<div class="section-divider"></div>

<!-- ── GALLERY ── -->
<section id="gallery">
  <div class="gallery-header">
    <div>
      <div class="section-eyebrow reveal">Visual</div>
      <h2 class="section-title reveal" style="margin-bottom:0">Gallery</h2>
    </div>
    <p class="reveal" style="font-size:0.8rem;color:var(--text-muted);text-transform:uppercase;letter-spacing:0.1em;font-weight:500">Replace with your photos</p>
  </div>
  <div class="gallery-grid">
    <div class="gallery-item reveal">
      <div class="gallery-placeholder" style="min-height:420px">
        <div class="gallery-placeholder-icon">◈</div>
        <span class="gallery-placeholder-label">Featured Photo</span>
      </div>
      <div class="gallery-overlay"><span class="gallery-caption">Leading the way</span></div>
    </div>
    <div class="gallery-item reveal reveal-delay-1">
      <div class="gallery-placeholder">
        <div class="gallery-placeholder-icon">◎</div>
        <span class="gallery-placeholder-label">Moment</span>
      </div>
      <div class="gallery-overlay"><span class="gallery-caption">On stage</span></div>
    </div>
    <div class="gallery-item reveal reveal-delay-2">
      <div class="gallery-placeholder">
        <div class="gallery-placeholder-icon">★</div>
        <span class="gallery-placeholder-label">Achievement</span>
      </div>
      <div class="gallery-overlay"><span class="gallery-caption">Recognition</span></div>
    </div>
    <div class="gallery-item reveal reveal-delay-1">
      <div class="gallery-placeholder">
        <div class="gallery-placeholder-icon">◇</div>
        <span class="gallery-placeholder-label">Creative</span>
      </div>
      <div class="gallery-overlay"><span class="gallery-caption">Creating</span></div>
    </div>
    <div class="gallery-item reveal reveal-delay-2">
      <div class="gallery-placeholder">
        <div class="gallery-placeholder-icon">♦</div>
        <span class="gallery-placeholder-label">Community</span>
      </div>
      <div class="gallery-overlay"><span class="gallery-caption">Building connections</span></div>
    </div>
  </div>
</section>

<div class="section-divider"></div>

<!-- ── SKILLS ── -->
<section id="skills">
  <div class="section-eyebrow reveal">Capabilities</div>
  <h2 class="section-title reveal">Things I'm Good At (and Things I'm Learning)</h2>
  <div class="skills-grid">
    <div class="skill-row reveal">
      <div class="skill-label"><span class="skill-name">Communication</span><span class="skill-pct">Core Strength</span></div>
      <div class="skill-track"><div class="skill-fill" data-width="96"></div></div>
    </div>
    <div class="skill-row reveal reveal-delay-1">
      <div class="skill-label"><span class="skill-name">Content Creation</span><span class="skill-pct">Growing Skill</span></div>
      <div class="skill-track"><div class="skill-fill" data-width="88"></div></div>
    </div>
    <div class="skill-row reveal">
      <div class="skill-label"><span class="skill-name">Social Media</span><span class="skill-pct">Strong Interest</span></div>
      <div class="skill-track"><div class="skill-fill" data-width="85"></div></div>
    </div>
    <div class="skill-row reveal reveal-delay-1">
      <div class="skill-label"><span class="skill-name">Photography</span><span class="skill-pct">Creative Practice</span></div>
      <div class="skill-track"><div class="skill-fill" data-width="75"></div></div>
    </div>
    <div class="skill-row reveal">
      <div class="skill-label"><span class="skill-name">Video Editing</span><span class="skill-pct">Developing SKill</span></div>
      <div class="skill-track"><div class="skill-fill" data-width="70"></div></div>
    </div>
    <div class="skill-row reveal reveal-delay-1">
      <div class="skill-label"><span class="skill-name">Trend Research</span><span class="skill-pct">Strong Interest</span></div>
      <div class="skill-track"><div class="skill-fill" data-width="90"></div></div>
    </div>
    <div class="skill-row reveal">
      <div class="skill-label"><span class="skill-name">Leadership</span><span class="skill-pct">Core strength</span></div>
      <div class="skill-track"><div class="skill-fill" data-width="92"></div></div>
    </div>
    <div class="skill-row reveal reveal-delay-1">
      <div class="skill-label"><span class="skill-name">Public Speaking</span><span class="skill-pct">Core Strength</span></div>
      <div class="skill-track"><div class="skill-fill" data-width="88"></div></div>
    </div>
    <div class="skill-row reveal">
      <div class="skill-label"><span class="skill-name">Creative Thinking</span><span class="skill-pct">Core Strength</span></div>
      <div class="skill-track"><div class="skill-fill" data-width="94"></div></div>
    </div>
   
  </div>
</section>

<div class="section-divider"></div>

<!-- ── ASPIRATIONS ── -->
<section id="aspirations">
  <div class="section-eyebrow reveal">Vision</div>
  <h2 class="section-title reveal">Where I'm Going</h2>
  <div class="aspirations-inner">
    <div class="aspirations-visual reveal">
      <div class="aspirations-circle">
        <span class="aspirations-circle-text">→</span>
      </div>
    </div>
    <div class="reveal">
      <p class="aspirations-content" style="font-family:var(--serif);font-size:clamp(1.1rem,2vw,1.3rem);font-weight:300;line-height:1.8;color:var(--text-secondary)">
        <p class="aspirations-content" style="font-family:var(--serif);font-size:clamp(1.1rem,2vw,1.3rem);font-weight:300;line-height:1.8;color:var(--text-secondary)">
  The dream?

To build a career in media, communication, content creation, and storytelling.

I'm endlessly curious about people, stories, trends, and the way ideas travel through the world. I want to work on projects that connect people, collaborate with inspiring voices, explore the entertainment and media industry, and create things that leave a lasting impact.

And yes, if life goes well, I'd love to spoil my friends, spoil myself a little, meet fascinating people, and build a life filled with meaningful work, creativity, and stories 

</p>
 <em style="color:var(--text-primary)">worth telling.</em>
      </p>
      <div class="aspiration-tags">
        <span class="aspiration-tag">Media</span>
        <span class="aspiration-tag">Communications</span>
        <span class="aspiration-tag">Digital Storytelling</span>
        <span class="aspiration-tag">Content Creation</span>
        <span class="aspiration-tag">Brand Strategy</span>
        <span class="aspiration-tag">Journalism</span>
        <span class="aspiration-tag">Public Relations</span>
      </div>
    </div>
  </div>
</section>

<div class="section-divider"></div>

<section id="education" style="padding-top:4rem;padding-bottom:4rem">
  <div class="section-eyebrow reveal">Education</div>
  <h2 class="section-title reveal">Academic Journey</h2>

  <div class="about-grid">

    <div class="strength-item reveal" style="padding:2rem">
      <h3 style="margin-bottom:1rem">B.Sc. Extension & Communication (Honours)</h3>
      <p>Currently Pursuing</p>
    </div>

    <div class="strength-item reveal reveal-delay-1" style="padding:2rem">
      <h3 style="margin-bottom:1rem">Class XII</h3>
      <p>81.2%</p>
    </div>

    <div class="strength-item reveal reveal-delay-2" style="padding:2rem">
      <h3 style="margin-bottom:1rem">Class X</h3>
      <p>84%</p>
    </div>

  </div>
</section>

<div class="section-divider"></div>
<!-- ── RESUME ── -->
<section id="resume" style="padding-top:4rem;padding-bottom:4rem">
  <div class="section-eyebrow reveal">Download</div>
  <h2 class="section-title reveal">Resume</h2>
  <div class="resume-card reveal">
    <div>
      <h3 class="resume-title">Shrishti — Full Resume</h3>
      <p class="resume-desc">A complete overview of my academic background, achievements, skills, and experiences. Updated and ready for your review.</p>
    </div>
    <a href="#" class="resume-btn" onclick="alert('Replace this link with your actual resume PDF URL!'); return false;">
      <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M12 15V3m0 12l-4-4m4 4l4-4M2 17l.621 2.485A2 2 0 004.561 21h14.878a2 2 0 001.94-1.515L22 17"/></svg>
      Download PDF
    </a>
  </div>
</section>

<div class="section-divider"></div>

<section id="random-things">
  <div class="section-eyebrow reveal">Unfiltered</div>
  <h2 class="section-title reveal">Random Things About Me</h2>
  <p class="section-subtitle reveal">A few completely unnecessary but very accurate facts.</p>

  <div class="about-grid">
<div class="strength-item reveal note note-1">
  <h3>📸</h3>
  <p>I stop walking when the sky looks pretty.</p>
</div>

<div class="strength-item reveal reveal-delay-1 note note-2">
  <h3>🎤</h3>
  <p>Public speaking doesn't scare me. Awkward silence does.</p>
</div>

<div class="strength-item reveal reveal-delay-2 note note-3">
  <h3>📱</h3>
  <p>I spend way too much time observing internet culture and trends.</p>
</div>

<div class="strength-item reveal note note-1">
  <h3>🧠</h3>
  <p>People fascinate me. Everyone has a story and I want to hear it.</p>
</div>

<div class="strength-item reveal reveal-delay-1 note note-2">
  <h3>☕</h3>
  <p>My best ideas usually arrive at the worst possible time.</p>
</div>


<div class="strength-item reveal reveal-delay-2 note note-3">
  <h3>🎬</h3>
  <p>I can spend an embarrassing amount of time analyzing why a piece of content went viral.</p>
</div>

  </div>
</section>

<div class="section-divider"></div>

<!-- ── CONTACT ── -->
<section id="contact">
  <div class="section-eyebrow reveal">Come Say Hi</div>
  <h2 class="section-title reveal">Got a cool idea?<br>Let's talk.</h2>
  <div class="contact-grid">
    <div>
      <p class="contact-intro reveal">Whether you have an opportunity, a creative idea, a question, or simply want to talk about media, storytelling, or life, I'd genuinely love to hear from you.</p>
      <ul class="contact-links">
        <li class="contact-link-item reveal">
          <a href="mailto:shrishtikoli6@gmail.com">
            <svg class="contact-link-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><rect x="2" y="4" width="20" height="16" rx="2"/><path d="m22 7-8.97 5.7a1.94 1.94 0 01-2.06 0L2 7"/></svg>
            shrishtikoli6@gmail.com
          </a>
        </li>
        <li class="contact-link-item reveal reveal-delay-2">
  <a href="https://www.linkedin.com/in/shrishti-koli-0b2a14364" target="_blank">
    <svg class="contact-link-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">
      <rect x="2" y="2" width="20" height="20" rx="2"/>
      <path d="M7 10v7M7 7v.01M11 17v-4c0-1.1.9-2 2-2s2 .9 2 2v4M11 10v7"/>
    </svg>
    LinkedIn Profile
  </a>
</li>
          </a>
        </li>
      </ul>
    </div>
    <div class="reveal">
      <form class="contact-form" onsubmit="alert('Message feature coming soon! Reach out via email or social media.'); return false;">
        <div class="contact-field">
          <label>Your Name</label>
          <input type="text" placeholder="Jane Doe">
        </div>
        <div class="contact-field">
          <label>Email</label>
          <input type="email" placeholder="jane@example.com">
        </div>
        <div class="contact-field">
          <label>Message</label>
          <textarea rows="4" placeholder="Tell me about your project or idea..."></textarea>
        </div>
        <button type="submit" class="btn-primary" style="width:100%;cursor:none">Send Message</button>
      </form>
    </div>
  </div>
</section>

<footer>
  <p class="footer-name">Shrishti</p>
  <p>Storyteller · Communicator · Future Media Professional</p>
  <p style="margin-top:1rem;font-size:0.75rem">© 2024 · Crafted with intention</p>
</footer>

<script>
(function() {
  // ── LOADER ──
  window.addEventListener('load', () => {
    setTimeout(() => {
      document.body.classList.add('loaded');
      document.querySelectorAll('#hero .reveal').forEach((el, i) => {
        setTimeout(() => { el.classList.add('visible'); }, i * 100);
      });
    }, 1400);
  });

  // ── CUSTOM CURSOR ──
  const cursor = document.getElementById('cursor');
  const trail = document.getElementById('cursor-trail');
  let mx = 0, my = 0, tx = 0, ty = 0;
  document.addEventListener('mousemove', e => {
    mx = e.clientX; my = e.clientY;
    cursor.style.left = mx + 'px';
    cursor.style.top = my + 'px';
  });
  function animTrail() {
    tx += (mx - tx) * 0.15;
    ty += (my - ty) * 0.15;
    trail.style.left = tx + 'px';
    trail.style.top = ty + 'px';
    requestAnimationFrame(animTrail);
  }
  animTrail();
  document.querySelectorAll('a,button,.gallery-item,.achievement-card').forEach(el => {
    el.addEventListener('mouseenter', () => {
      cursor.style.transform = 'scale(2)';
      trail.style.transform = 'scale(0.5)';
    });
    el.addEventListener('mouseleave', () => {
      cursor.style.transform = 'scale(1)';
      trail.style.transform = 'scale(1)';
    });
  });

  // ── SCROLL PROGRESS ──
  const bar = document.getElementById('scroll-bar');
  window.addEventListener('scroll', () => {
    const pct = window.scrollY / (document.body.scrollHeight - window.innerHeight) * 100;
    bar.style.width = pct + '%';
  }, { passive: true });

  // ── NAV SCROLL ──
  const nav = document.getElementById('main-nav');
  window.addEventListener('scroll', () => {
    nav.classList.toggle('scrolled', window.scrollY > 80);
  }, { passive: true });

  // ── HAMBURGER ──
  const ham = document.getElementById('hamburger');
  const navLinks = document.getElementById('nav-links');
  ham.addEventListener('click', () => {
    ham.classList.toggle('open');
    navLinks.classList.toggle('open');
  });
  navLinks.querySelectorAll('a').forEach(a => {
    a.addEventListener('click', () => { ham.classList.remove('open'); navLinks.classList.remove('open'); });
  });

  // ── THEME TOGGLE ──
  const toggle = document.getElementById('theme-toggle');
  const sun = document.getElementById('sun-icon');
  const moon = document.getElementById('moon-icon');
  const label = document.getElementById('theme-label');
  let dark = false;
  toggle.addEventListener('click', () => {
    dark = !dark;
    document.documentElement.setAttribute('data-theme', dark ? 'dark' : 'light');
    sun.style.display = dark ? 'none' : 'block';
    moon.style.display = dark ? 'block' : 'none';
    label.textContent = dark ? 'Light' : 'Dark';
  });

  // ── REVEAL ON SCROLL ──
  const reveals = document.querySelectorAll('.reveal:not(#hero .reveal)');
  const observer = new IntersectionObserver((entries) => {
    entries.forEach(e => {
      if (e.isIntersecting) { e.target.classList.add('visible'); observer.unobserve(e.target); }
    });
  }, { threshold: 0.12, rootMargin: '0px 0px -40px 0px' });
  reveals.forEach(r => observer.observe(r));

  // ── SKILL BARS ──
  const skillObserver = new IntersectionObserver((entries) => {
    entries.forEach(e => {
      if (e.isIntersecting) {
        e.target.querySelectorAll('.skill-fill').forEach(fill => {
          const w = fill.dataset.width;
          setTimeout(() => { fill.style.width = w + '%'; }, 200);
        });
        skillObserver.unobserve(e.target);
      }
    });
  }, { threshold: 0.3 });
  const skillSection = document.getElementById('skills');
  if (skillSection) skillObserver.observe(skillSection);

  // ── COUNTER ANIMATION ──
  const counterObserver = new IntersectionObserver((entries) => {
    entries.forEach(e => {
      if (e.isIntersecting) {
        e.target.querySelectorAll('[data-count]').forEach(el => {
          const target = parseInt(el.dataset.count);
          let current = 0;
          const step = Math.max(1, Math.floor(target / 40));
          const timer = setInterval(() => {
            current = Math.min(current + step, target);
            el.textContent = current;
            if (current >= target) clearInterval(timer);
          }, 40);
        });
        counterObserver.unobserve(e.target);
      }
    });
  }, { threshold: 0.5 });
  const statsSection = document.getElementById('stats');
  if (statsSection) counterObserver.observe(statsSection);
})();
</script>
</body>
</html>
