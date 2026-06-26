# 🇨🇳 HSK-4 Quiz — Radicals & Essential Words

<p align="center">
  <strong>A premium, production-grade quiz web application for mastering HSK-4 Chinese radicals and vocabulary.</strong><br>
  Unique randomised quizzes every session. Zero dependencies. Lightning fast.
</p>

<p align="center">
  <a href="https://hsk4-radicals-quiz.vercel.app">🌐 Live Demo</a> ·
  <a href="https://github.com/Jubayer-Ahmed-Sajid/hsk4-radicals-quiz">📦 Repository</a>
</p>

---

## ✨ Overview

HSK-4 Quiz is a self-contained, single-page web application designed to help learners of Mandarin Chinese master the **100 essential radicals** and **300 most important vocabulary words** at the HSK-4 proficiency level. The application generates unique, randomised quizzes on every session, ensuring that no two study experiences are ever the same.

Built as a single `index.html` file with zero external JavaScript dependencies, the app delivers a premium, production-grade experience with a black, white, and gold design system, subtle micro-animations, and full dark/light mode support. It deploys instantly on Vercel as a static site with no build step required.

---

## 🎯 Key Features

### Dual Quiz Modes
The application offers two distinct quiz modes accessible via a tabbed interface:

- **✏️ Radicals Mode** — Quiz yourself on 100 essential HSK-4 radicals organised across 6 thematic sections: Human & Body (11), Nature & Elements (18), Actions & Movement (14), Objects & Places (18), Shapes & Numbers (17), and Supplementary (18). Each radical is presented with its character, pinyin, and English meaning.

- **📖 Essential Words Mode** — Quiz yourself on 300 of the most important HSK-4 vocabulary words organised into 10 thematic groups: Essential Verbs (60), Essential Adjectives (46), Time & Frequency (29), Connecting Words (29), Emotions & Thinking (30), Society & Work (30), Body & Health (20), Travel & Places (20), Common Nouns (30), and Adverbs & Useful Words (30).

### Section Selection & Range Control
- **Individual section cards** — Click any section to generate a quiz focused exclusively on that group of radicals or words.
- **Range selector** — Choose any combination of sections using From/To dropdowns. Select Sections 1–3 for a focused drill, or Sections 1–6 (or 1–10 for words) for a comprehensive review. The range selector displays the total item count, number of questions, and total question count including multiple quizzes.

### Quiz Count Selector
Choose how many quizzes to generate per session: **1, 2, 3, 5, or 10**. All quizzes are concatenated into one seamless session. For example, selecting 3 quizzes on Essential Verbs generates 126 questions (42 per quiz × 3), each independently randomised.

### Unique Random Generation
Every quiz is guaranteed unique through four layers of randomisation:

1. **70% sampling** — Each quiz randomly selects 70% of the items from the chosen section(s), ensuring coverage without overwhelming.
2. **Random question types** — For radicals: meaning, pinyin, or character identification (3 types). For words: meaning or character identification (2 types). The type is randomised per question.
3. **Random distractors** — The 3 wrong answer options are randomly selected from the same section pool, making same-section distractors challenging.
4. **Shuffled order** — Both the selected items and the final question order are fully shuffled.

### Question Flow
Each question presents 4 clickable options (A, B, C, D). Upon selection:
- ✅ Correct: Green highlight with a spring-bounce animation, score increments
- ❌ Wrong: Red highlight with a horizontal shake, correct answer revealed
- Auto-advances to the next question after 1.3 seconds

### Results & Review
After completing all questions, the results screen displays:
- **Score percentage** with colour-coded tiering (gold for ≥80%, orange for ≥50%, red below)
- **Emoji award** — 🏆 Perfect, ✨ Excellent, 💪 Good, 📖 Keep Studying
- **Animated progress bar** that fills to the score percentage
- **Wrong answer review** — Every missed item is listed with its character, pinyin, and meaning for immediate study
- **New Quiz button** that re-randomises with the same settings

---

## 🎨 Design System

### Colour Palette
The application uses a premium **black, white, and gold** colour system:

| Token | Dark Mode | Light Mode |
|-------|-----------|------------|
| Background | #09090b | #fafaf9 |
| Surface | #141418 | #ffffff |
| Border | #27272a | #e7e5e4 |
| Text Primary | #fafafa | #1c1917 |
| Text Secondary | #a1a1aa | #78716c |
| Gold Primary | #d4a847 | #d4a847 |
| Gold Light | #f5d98a | #f5d98a |

Gold remains consistent across both modes for brand identity.

### Typography
- **Inter** — Used for all UI text, labels, buttons, and body content
- **Noto Serif SC** — Used exclusively for Chinese character display, providing authentic serif rendering that honours the calligraphic tradition

### Micro-Animations
The application features carefully crafted animations that enhance without distracting:
- `fadeDown` — Header entrance with vertical slide
- `fadeUp` — Cards and UI elements with staggered delays (each card offsets by 50ms)
- `cardIn` — Question card entrance with combined translateY + scale
- `popCorrect` — Spring-bounce on correct answer selection
- `shakeWrong` — Horizontal shake on incorrect answer
- `goldShift` — Continuous gradient shimmer on the brand text "Quiz"
- `scaleIn` — Results card entrance with subtle zoom
- Hover effects — Cards lift with shadow, options glow with radial gradient, wrong items slide right on hover
- Active states — Immediate feedback with 50ms transition duration for pressed feel

### Dark & Light Mode
- Toggle button fixed in the top-right corner showing 🌙 (in dark) or ☀️ (in light)
- Defaults to the user's system `prefers-color-scheme` preference
- Persists choice to `localStorage` — survives page reloads and return visits
- All colours are driven by CSS custom properties on `[data-theme]`, ensuring instant switching with no flash

---

## 🏗️ Architecture

### Single-File Design
The entire application is contained in one `index.html` file (~47KB). All CSS, JavaScript, and data are embedded inline. This architecture choice provides:

- **Zero build step** — No Webpack, Vite, or bundler needed
- **Zero dependencies** — No npm packages, no CDN scripts
- **Instant deployment** — Push to any static host and it works
- **Offline capable** — Works without network once loaded
- **Fast cold starts** — Single HTTP request delivers the entire app

### Data Architecture
All quiz data is embedded as JavaScript const arrays:
- `RADICALS` — 6 section objects, each containing an array of radical objects with `c` (character), `p` (pinyin), and `m` (meaning)
- `WORDS` — 10 section objects, each containing an array of word objects with the same schema

This eliminates any need for API calls or external data fetching.

### Deployment
Deployed on Vercel as a static site:
- `vercel.json` configures the `@vercel/static` builder
- GitHub connected for automatic deployments on push to `main`
- Production URL: [hsk4-radicals-quiz.vercel.app](https://hsk4-radicals-quiz.vercel.app)
- Build time: ~6 seconds
- Zero server-side computation

---

## 📱 Responsiveness

The application is fully responsive with a mobile-first approach:
- Section cards reflow from multi-column to single-column below 640px
- Option buttons stack vertically on small screens
- Chinese character font size scales down for mobile
- Mode tabs stack vertically on narrow viewports
- Range selector inputs go full-width on mobile
- Touch-friendly hit targets on all interactive elements

---

## 📊 Content Summary

| Mode | Sections | Total Items | Questions per Quiz (70%) | With 10 Quizzes |
|------|----------|-------------|--------------------------|-----------------|
| Radicals | 6 | 96 | ~67 | ~670 |
| Essential Words | 10 | 304 | ~213 | ~2,130 |

All data sourced from the official HSK-4 100 Essential Radicals Reference Sheet and the HSK-4 300 Most Important Words Vocabulary Deck.

---

## 🛠️ Tech Stack

| Layer | Technology |
|-------|-----------|
| Markup | HTML5 |
| Styling | CSS3 (Custom Properties, Grid, Flexbox, Animations) |
| Logic | Vanilla JavaScript (ES6+) |
| Chinese Font | Google Fonts — Noto Serif SC |
| UI Font | Google Fonts — Inter |
| Hosting | Vercel (Static) |
| Version Control | Git + GitHub |

---

## 📄 License

MIT License. Free to use, modify, and distribute.
