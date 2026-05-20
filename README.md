<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Umar Farouq — Explorer at the Edge</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=DM+Serif+Display:ital@0;1&family=Space+Mono:ital,wght@0,400;0,700;1,400&family=Figtree:wght@300;400;500;600&display=swap" rel="stylesheet">
<style>
  :root {
    --ink: #0a0a0f;
    --paper: #f5f0e8;
    --gold: #c9a84c;
    --gold-light: #e8cc7a;
    --electric: #00e5ff;
    --pulse: #ff3c6e;
    --mist: #8a8fa8;
    --void: #06060c;
    --sage: #4ade80;
    --serif: 'DM Serif Display', Georgia, serif;
    --mono: 'Space Mono', monospace;
    --sans: 'Figtree', sans-serif;
    --display: 'Bebas Neue', sans-serif;
  }
  *, *::before, *::after { margin: 0; padding: 0; box-sizing: border-box; }
  html { scroll-behavior: smooth; }
  body {
    background: var(--void);
    color: var(--paper);
    font-family: var(--sans);
    font-weight: 300;
    overflow-x: hidden;
    cursor: none;
  }

  /* CURSOR */
  .cursor {
    position: fixed; width: 10px; height: 10px;
    background: var(--electric); border-radius: 50%;
    pointer-events: none; z-index: 9999;
    transition: transform 0.15s ease;
    mix-blend-mode: screen;
  }
  .cursor-ring {
    position: fixed; width: 36px; height: 36px;
    border: 1px solid rgba(0,229,255,0.35); border-radius: 50%;
    pointer-events: none; z-index: 9998;
    transition: left 0.1s ease, top 0.1s ease, transform 0.3s ease;
    mix-blend-mode: screen;
  }

  /* NOISE */
  body::before {
    content: '';
    position: fixed; inset: 0;
    background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='1'/%3E%3C/svg%3E");
    opacity: 0.03; pointer-events: none; z-index: 8000;
  }

  /* NAV */
  nav {
    position: fixed; top: 0; left: 0; right: 0; z-index: 1000;
    padding: 22px 56px;
    display: flex; justify-content: space-between; align-items: center;
    background: linear-gradient(to bottom, rgba(6,6,12,0.97) 0%, transparent 100%);
    backdrop-filter: blur(4px);
  }
  .nav-logo {
    font-family: var(--mono); font-size: 12px;
    letter-spacing: 0.22em; color: var(--electric); text-transform: uppercase;
  }
  .nav-links { display: flex; gap: 36px; list-style: none; }
  .nav-links a {
    font-family: var(--mono); font-size: 10px; letter-spacing: 0.18em;
    color: var(--mist); text-decoration: none; text-transform: uppercase;
    transition: color 0.3s; position: relative;
  }
  .nav-links a::after {
    content: ''; position: absolute; bottom: -4px; left: 0;
    width: 0; height: 1px; background: var(--electric); transition: width 0.3s;
  }
  .nav-links a:hover { color: var(--electric); }
  .nav-links a:hover::after { width: 100%; }

  /* ─────── HERO ─────── */
  .hero {
    min-height: 100vh; display: grid;
    grid-template-columns: 1.1fr 0.9fr; position: relative; overflow: hidden;
  }
  .hero-bg {
    position: absolute; inset: 0;
    background:
      radial-gradient(ellipse 70% 60% at 72% 50%, rgba(0,229,255,0.07) 0%, transparent 65%),
      radial-gradient(ellipse 45% 45% at 18% 80%, rgba(201,168,76,0.06) 0%, transparent 55%),
      radial-gradient(ellipse 55% 70% at 50% 0%, rgba(255,60,110,0.04) 0%, transparent 55%);
  }
  .hero-grid {
    position: absolute; inset: 0;
    background-image:
      linear-gradient(rgba(0,229,255,0.035) 1px, transparent 1px),
      linear-gradient(90deg, rgba(0,229,255,0.035) 1px, transparent 1px);
    background-size: 64px 64px;
    animation: gridDrift 22s linear infinite;
  }
  @keyframes gridDrift { 0%{background-position:0 0} 100%{background-position:64px 64px} }

  .hero-left {
    display: flex; flex-direction: column; justify-content: center;
    padding: 130px 52px 90px 80px; position: relative; z-index: 1;
  }
  .hero-eyebrow {
    font-family: var(--mono); font-size: 10px; letter-spacing: 0.28em;
    color: var(--electric); text-transform: uppercase; margin-bottom: 26px;
    display: flex; align-items: center; gap: 14px;
  }
  .hero-eyebrow::before { content: ''; width: 36px; height: 1px; background: var(--electric); }
  .hero-name {
    font-family: var(--display); font-size: clamp(70px, 8.5vw, 128px);
    line-height: 0.88; letter-spacing: 0.02em; margin-bottom: 10px;
  }
  .hero-name .first { color: var(--paper); display: block; }
  .hero-name .last {
    color: transparent; -webkit-text-stroke: 1px var(--gold);
    letter-spacing: 0.06em; display: block;
  }
  .hero-role {
    font-family: var(--serif); font-style: italic;
    font-size: clamp(17px, 2vw, 24px); color: var(--gold-light);
    margin-top: 22px; margin-bottom: 28px; line-height: 1.45;
  }
  .hero-desc {
    font-size: 15px; color: var(--mist); line-height: 1.85;
    max-width: 440px; margin-bottom: 52px;
  }
  .hero-desc strong { color: var(--paper); font-weight: 500; }

  .hero-pills {
    display: flex; flex-wrap: wrap; gap: 10px; margin-bottom: 40px;
  }
  .pill {
    font-family: var(--mono); font-size: 9px; letter-spacing: 0.15em;
    text-transform: uppercase; padding: 6px 14px;
    border: 1px solid rgba(0,229,255,0.25); color: var(--electric);
    transition: all 0.3s; cursor: default;
  }
  .pill:hover { background: rgba(0,229,255,0.08); border-color: var(--electric); }
  .pill.gold { border-color: rgba(201,168,76,0.3); color: var(--gold-light); }
  .pill.gold:hover { background: rgba(201,168,76,0.08); border-color: var(--gold); }
  .pill.rose { border-color: rgba(255,60,110,0.3); color: #ff8aaa; }
  .pill.sage { border-color: rgba(74,222,128,0.3); color: var(--sage); }

  .hero-cta { display: flex; gap: 16px; flex-wrap: wrap; }
  .btn-primary {
    font-family: var(--mono); font-size: 11px; letter-spacing: 0.15em;
    text-transform: uppercase; padding: 15px 34px;
    background: var(--electric); color: var(--void); text-decoration: none; font-weight: 700;
    clip-path: polygon(0 0, calc(100% - 12px) 0, 100% 12px, 100% 100%, 12px 100%, 0 calc(100% - 12px));
    transition: all 0.3s;
  }
  .btn-primary:hover { background: var(--gold); transform: translate(-2px,-2px); box-shadow: 4px 4px 0 var(--pulse); }
  .btn-ghost {
    font-family: var(--mono); font-size: 11px; letter-spacing: 0.15em;
    text-transform: uppercase; padding: 15px 34px;
    border: 1px solid rgba(138,143,168,0.35); color: var(--mist);
    text-decoration: none; transition: all 0.3s;
  }
  .btn-ghost:hover { border-color: var(--electric); color: var(--electric); }

  /* HERO RIGHT ORB */
  .hero-right {
    display: flex; align-items: center; justify-content: center;
    position: relative; z-index: 1; padding: 130px 80px 90px 0;
  }
  .orb-wrap { position: relative; width: 400px; height: 400px; }
  .orb {
    position: absolute; border-radius: 50%;
  }
  .orb-1 {
    inset: 0;
    background: radial-gradient(circle at 35% 35%, rgba(0,229,255,0.18), rgba(0,229,255,0.04) 55%, transparent 70%);
    border: 1px solid rgba(0,229,255,0.18);
    animation: pulse 4s ease-in-out infinite;
  }
  .orb-2 {
    inset: 44px;
    background: radial-gradient(circle at 65% 65%, rgba(201,168,76,0.13), transparent 70%);
    border: 1px solid rgba(201,168,76,0.14);
    animation: pulse 4s ease-in-out infinite 1.2s;
  }
  .orb-3 {
    inset: 88px;
    background: radial-gradient(circle at 50% 50%, rgba(255,60,110,0.09), transparent 70%);
    border: 1px solid rgba(255,60,110,0.1);
    animation: pulse 4s ease-in-out infinite 2.4s;
  }
  .orb-core {
    position: absolute; inset: 136px;
    background: radial-gradient(circle, rgba(0,229,255,0.28), rgba(201,168,76,0.18) 45%, transparent 70%);
    border-radius: 50%;
    animation: coreGlow 3s ease-in-out infinite;
  }
  @keyframes pulse { 0%,100%{transform:scale(1);opacity:.6} 50%{transform:scale(1.045);opacity:1} }
  @keyframes coreGlow { 0%,100%{opacity:.45} 50%{opacity:1} }

  .ring { position: absolute; border-radius: 50%; border: 1px dashed; }
  .ring-a { inset:-28px; border-color:rgba(0,229,255,0.08); animation:spin 22s linear infinite; }
  .ring-b { inset:-58px; border-color:rgba(201,168,76,0.07); animation:spin 38s linear infinite reverse; }
  .ring-dot {
    position: absolute; width: 7px; height: 7px; border-radius: 50%;
    top: -3.5px; left: 50%; transform: translateX(-50%);
  }
  .ring-dot-a { background: var(--electric); box-shadow: 0 0 10px var(--electric); }
  .ring-dot-b { background: var(--gold); box-shadow: 0 0 10px var(--gold); top:auto; bottom:-3.5px; }
  @keyframes spin { from{transform:rotate(0deg)} to{transform:rotate(360deg)} }

  .float-label {
    position: absolute; font-family: var(--mono); font-size: 9px;
    letter-spacing: 0.15em; text-transform: uppercase; white-space: nowrap;
    display: flex; align-items: center; gap: 8px; opacity: 0.75;
  }
  .float-label::before { content:''; width:18px; height:1px; background:currentColor; opacity:.5; }
  .fl-web3 { top:22px; right:-56px; color:var(--electric); }
  .fl-ai   { top:50%; right:-78px; transform:translateY(-50%); color:var(--gold); }
  .fl-book { bottom:48px; right:-64px; color:var(--sage); }
  .fl-abe  { top:48px; left:-80px; color:#ff8aaa; flex-direction:row-reverse; }
  .fl-abe::before { background:currentColor; }

  /* TICKER */
  .ticker {
    background: rgba(0,229,255,0.05);
    border-top: 1px solid rgba(0,229,255,0.12);
    border-bottom: 1px solid rgba(0,229,255,0.12);
    padding: 11px 0; overflow: hidden;
  }
  .ticker-track {
    display: flex; animation: tickerMove 32s linear infinite; white-space: nowrap;
  }
  .t-item {
    font-family: var(--mono); font-size: 10px; letter-spacing: 0.2em;
    text-transform: uppercase; color: var(--electric); padding: 0 44px; opacity: .65; flex-shrink: 0;
  }
  .t-sep { color: var(--gold); opacity: .45; padding: 0; }
  @keyframes tickerMove { 0%{transform:translateX(0)} 100%{transform:translateX(-50%)} }

  /* ── SHARED LAYOUT ── */
  .section-eyebrow {
    font-family: var(--mono); font-size: 9px; letter-spacing: 0.3em;
    text-transform: uppercase; color: var(--electric); margin-bottom: 14px;
    display: flex; align-items: center; gap: 12px;
  }
  .section-eyebrow::after { content:''; flex:1; max-width:56px; height:1px; background:var(--electric); opacity:.4; }
  .section-title {
    font-family: var(--serif); font-size: clamp(34px, 4.5vw, 62px); line-height: 1.08; margin-bottom: 14px;
  }
  .fade-up { opacity:0; transform:translateY(30px); transition:opacity .8s ease, transform .8s ease; }
  .fade-up.visible { opacity:1; transform:translateY(0); }

  /* ─────── ABOUT ─────── */
  #about {
    padding: 120px 80px;
    background: linear-gradient(135deg, rgba(6,6,12,1), rgba(10,10,20,1));
  }
  .about-grid {
    display: grid; grid-template-columns: 1fr 1.15fr; gap: 96px;
    align-items: start; max-width: 1280px; margin: 0 auto;
  }
  .about-text { font-size: 15.5px; line-height: 1.9; color: var(--mist); margin-bottom: 24px; }
  .about-text strong { color: var(--paper); font-weight: 500; }
  .about-text a { color: var(--electric); text-decoration: none; }

  .id-stack { display: grid; gap: 2px; }
  .id-card {
    padding: 22px 26px; border-left: 3px solid transparent;
    background: rgba(255,255,255,0.025); transition: all .3s;
  }
  .id-card:hover { background: rgba(255,255,255,0.045); transform: translateX(5px); }
  .id-card.c1 { border-color: var(--electric); }
  .id-card.c2 { border-color: var(--gold); }
  .id-card.c3 { border-color: #a855f7; }
  .id-card.c4 { border-color: var(--pulse); }
  .id-card.c5 { border-color: var(--sage); }
  .id-tag { font-family:var(--mono); font-size:8px; letter-spacing:.22em; text-transform:uppercase; color:var(--mist); margin-bottom:6px; }
  .id-title { font-family:var(--serif); font-size:19px; color:var(--paper); margin-bottom:6px; }
  .id-body { font-size:13px; line-height:1.65; color:rgba(138,143,168,.85); }

  /* ─────── BOOK ─────── */
  #book {
    padding: 120px 80px;
    background: linear-gradient(160deg, rgba(6,6,12,1) 0%, rgba(12,8,4,1) 50%, rgba(6,6,12,1) 100%);
    position: relative; overflow: hidden;
  }
  #book::before {
    content: '';
    position: absolute; inset: 0;
    background: radial-gradient(ellipse 60% 70% at 80% 50%, rgba(201,168,76,0.06), transparent 65%),
                radial-gradient(ellipse 40% 50% at 10% 80%, rgba(74,222,128,0.04), transparent 60%);
    pointer-events: none;
  }
  .book-inner { max-width: 1280px; margin: 0 auto; display: grid; grid-template-columns: 1fr 1fr; gap: 100px; align-items: center; }

  /* The Book Visual */
  .book-visual { position: relative; display: flex; justify-content: center; align-items: center; padding: 40px 0; }
  .book-3d {
    position: relative; width: 220px; height: 300px;
    transform-style: preserve-3d; transform: rotateY(-20deg) rotateX(5deg);
    animation: bookFloat 5s ease-in-out infinite;
    filter: drop-shadow(0 40px 60px rgba(201,168,76,0.25));
  }
  @keyframes bookFloat {
    0%,100% { transform: rotateY(-20deg) rotateX(5deg) translateY(0); }
    50% { transform: rotateY(-20deg) rotateX(5deg) translateY(-14px); }
  }
  .book-cover {
    position: absolute; inset: 0;
    background: linear-gradient(145deg, #1a1408 0%, #2a1e08 40%, #1a1408 100%);
    border-radius: 3px 12px 12px 3px;
    border: 1px solid rgba(201,168,76,0.4);
    display: flex; flex-direction: column;
    align-items: center; justify-content: center;
    padding: 28px 22px; text-align: center; overflow: hidden;
  }
  .book-cover::before {
    content: '';
    position: absolute; inset: 8px;
    border: 1px solid rgba(201,168,76,0.2);
    border-radius: 0 8px 8px 0; pointer-events: none;
  }
  .book-cover::after {
    content: '';
    position: absolute; top: 0; left: 0; bottom: 0;
    width: 18px;
    background: linear-gradient(90deg, rgba(0,0,0,0.5), rgba(201,168,76,0.15), rgba(0,0,0,0.3));
    border-right: 1px solid rgba(201,168,76,0.2);
  }
  .book-ornament { font-size: 28px; margin-bottom: 16px; opacity: .85; }
  .book-cover-title {
    font-family: var(--serif); font-style: italic;
    font-size: 15px; color: var(--gold-light); line-height: 1.4;
    margin-bottom: 12px; position: relative; z-index: 1;
  }
  .book-cover-line {
    width: 48px; height: 1px; background: rgba(201,168,76,0.4); margin: 0 auto 12px;
  }
  .book-cover-author {
    font-family: var(--mono); font-size: 9px; letter-spacing: .2em;
    text-transform: uppercase; color: rgba(201,168,76,0.6);
    position: relative; z-index: 1;
  }
  /* Book spine */
  .book-spine {
    position: absolute; top: 0; left: -16px; bottom: 0; width: 16px;
    background: linear-gradient(90deg, #0d0d06, #1a1408);
    border-radius: 3px 0 0 3px;
    border: 1px solid rgba(201,168,76,0.2);
    transform-origin: right; transform: rotateY(90deg);
    display: flex; align-items: center; justify-content: center;
  }
  .spine-text {
    font-family: var(--mono); font-size: 7px; letter-spacing: .15em;
    text-transform: uppercase; color: rgba(201,168,76,.5);
    writing-mode: vertical-rl; text-orientation: mixed;
    transform: rotate(180deg);
  }
  /* glow rings behind book */
  .book-glow {
    position: absolute; border-radius: 50%;
    animation: bookGlow 4s ease-in-out infinite;
  }
  .bg-1 { width:320px; height:320px; top:50%; left:50%; transform:translate(-50%,-50%);
    background: radial-gradient(circle, rgba(201,168,76,0.06), transparent 65%); }
  .bg-2 { width:200px; height:200px; top:50%; left:50%; transform:translate(-50%,-50%);
    background: radial-gradient(circle, rgba(201,168,76,0.04), transparent 65%);
    animation-delay: 1.5s; }
  @keyframes bookGlow { 0%,100%{opacity:.5;transform:translate(-50%,-50%) scale(1)} 50%{opacity:1;transform:translate(-50%,-50%) scale(1.08)} }

  /* Book content */
  .book-content .section-title { color: var(--paper); }
  .book-content .section-title span { color: var(--gold-light); font-style: italic; }
  .book-desc {
    font-size: 15.5px; line-height: 1.9; color: var(--mist); margin: 24px 0 32px;
  }
  .book-desc strong { color: var(--paper); font-weight: 500; }

  .book-pillars { display: flex; flex-direction: column; gap: 2px; margin-bottom: 36px; }
  .pillar {
    padding: 18px 22px; background: rgba(201,168,76,0.04);
    border-left: 2px solid rgba(201,168,76,0.3);
    display: flex; align-items: flex-start; gap: 16px;
    transition: all .3s;
  }
  .pillar:hover { background: rgba(201,168,76,0.08); border-left-color: var(--gold); transform: translateX(4px); }
  .pillar-icon { font-size: 20px; flex-shrink: 0; margin-top: 1px; }
  .pillar-title { font-family: var(--serif); font-size: 17px; color: var(--gold-light); margin-bottom: 4px; }
  .pillar-body { font-size: 13px; line-height: 1.6; color: rgba(138,143,168,.85); }

  .book-badge {
    display: inline-flex; align-items: center; gap: 10px;
    padding: 12px 20px; background: rgba(201,168,76,0.08);
    border: 1px solid rgba(201,168,76,0.25);
    font-family: var(--mono); font-size: 10px; letter-spacing: .15em;
    text-transform: uppercase; color: var(--gold-light);
  }

  /* ─────── DOMAINS ─────── */
  #domains {
    padding: 120px 80px; background: var(--void);
  }
  .domains-inner { max-width: 1280px; margin: 0 auto; }
  .domains-header { margin-bottom: 72px; }
  .domains-grid { display: grid; grid-template-columns: repeat(2, 1fr); gap: 2px; }

  .domain-card {
    padding: 52px 46px; background: rgba(255,255,255,0.022);
    position: relative; overflow: hidden; transition: all .4s;
  }
  .domain-card::before {
    content: ''; position: absolute; inset: 0; opacity: 0; transition: opacity .4s;
  }
  .domain-card:hover { transform: scale(1.008); }
  .domain-card:hover::before { opacity: 1; }
  .dc1::before { background: radial-gradient(ellipse at 0% 100%, rgba(0,229,255,0.07), transparent 55%); }
  .dc2::before { background: radial-gradient(ellipse at 100% 0%, rgba(201,168,76,0.07), transparent 55%); }
  .dc3::before { background: radial-gradient(ellipse at 0% 0%, rgba(255,60,110,0.07), transparent 55%); }
  .dc4::before { background: radial-gradient(ellipse at 100% 100%, rgba(168,85,247,0.07), transparent 55%); }

  .domain-num {
    font-family: var(--display); font-size: 88px; line-height: 1;
    color: transparent; margin-bottom: 20px;
  }
  .dc1 .domain-num { -webkit-text-stroke: 1px rgba(0,229,255,0.15); }
  .dc2 .domain-num { -webkit-text-stroke: 1px rgba(201,168,76,0.15); }
  .dc3 .domain-num { -webkit-text-stroke: 1px rgba(255,60,110,0.15); }
  .dc4 .domain-num { -webkit-text-stroke: 1px rgba(168,85,247,0.15); }

  .domain-icon { font-size: 30px; margin-bottom: 14px; display: block; }
  .domain-title { font-family: var(--display); font-size: 34px; letter-spacing: .04em; margin-bottom: 10px; }
  .dc1 .domain-title { color: var(--electric); }
  .dc2 .domain-title { color: var(--gold-light); }
  .dc3 .domain-title { color: var(--pulse); }
  .dc4 .domain-title { color: #c084fc; }

  .domain-sub { font-family:var(--serif); font-style:italic; font-size:15px; color:var(--mist); margin-bottom:18px; }
  .domain-body { font-size:13.5px; line-height:1.8; color:rgba(138,143,168,.82); }
  .domain-tags { display:flex; flex-wrap:wrap; gap:8px; margin-top:22px; }
  .tag {
    font-family:var(--mono); font-size:8.5px; letter-spacing:.14em;
    text-transform:uppercase; padding:4px 11px; border:1px solid;
  }
  .dc1 .tag { border-color:rgba(0,229,255,0.18); color:rgba(0,229,255,.6); }
  .dc2 .tag { border-color:rgba(201,168,76,0.18); color:rgba(201,168,76,.6); }
  .dc3 .tag { border-color:rgba(255,60,110,0.18); color:rgba(255,60,110,.6); }
  .dc4 .tag { border-color:rgba(168,85,247,0.18); color:rgba(168,85,247,.6); }

  /* ─────── STACK ─────── */
  #stack {
    padding: 110px 80px;
    background: linear-gradient(180deg, rgba(6,6,12,1), 
