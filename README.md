# PROJ.ZERO — Training Log & Content Vault

**Live site:** https://zachc0des.github.io/zjim/
**TikTok:** [@proj.zero1](https://www.tiktok.com/@proj.zero1)

A single-page, zero-dependency web vault for everything PROJ.ZERO lifts, films, and saves — gym clips, form breakdowns, the apps actually in rotation, and the gear worth buying. Built as one self-contained `index.html` and served straight off GitHub Pages.

---

## What it's for

Most fitness content dies in a camera roll or a Pinterest board nobody revisits. PROJ.ZERO is the permanent home for it: a public, linkable archive that doubles as a landing page for the TikTok audience.

It serves three jobs at once:

1. **Training log** — a running feed of gym pics, videos, and form checks, with a "plate rack" counter that visually stacks a plate for every post logged.
2. **Recommendation vault** — curated apps, gear, food, and recovery routines, each with a plain-language note on *why* it earned a spot.
3. **Brand front door** — a navy/cobalt landing page that funnels visitors to the TikTok account.

## Who it's for

Beginners and gym-anxious lifters — people who want a short, opinionated answer instead of a 40-minute video. The tone throughout is deliberately low-pressure: entry-level gear, free apps, and recovery habits that don't require a coach or a membership.

---

## Sections

| Tab | Contents | Filters |
|---|---|---|
| **Feed** | Gym pics, training videos, guides, Pinterest finds | All · Gym Pics · Videos · Guides & Tutorials · Pinterest Finds |
| **Apps** | What's actually on the phone — logging, food tracking, gym-anxiety tools | All · Training · Nutrition · Recovery · Mindset |
| **Gear** | Low-anxiety home gym essentials through wishlist items | All · Home Gym · Recovery · Apparel · Tech |
| **Fuel** | Meal prep, recipes, nutrition guides, supplements | All · Meal Prep · Recipes · Nutrition Guides · Supplements |
| **Recovery** | Yoga flows, mobility work, sleep habits, active recovery | All · Yoga · Stretching & Mobility · Sleep · Active Recovery |

Every panel has its own scoped filter chips and its own empty state, so an unfinished section reads as intentional rather than broken.

---

## How it works

- **One file.** All markup, CSS, and JavaScript live in `index.html`. No build step, no framework, no package manager.
- **Content lives in code.** Five arrays at the top of the script block (`POSTS`, `APPS`, `GEAR`, `FUEL`, `RECOVERY`) are the single source of truth. There is no on-page add/remove UI and no database — updating the site means copying an existing entry, changing the fields, and pushing the commit.
- **Client-side rendering.** Tab switching, filtering, and card rendering are handled by vanilla JS on load. All user input is passed through an `escapeHtml()` helper before it hits the DOM.
- **Video is self-hosted.** Clips sit in `/videos/` in the repo and play inline via native `<video controls playsinline>`.
- **Graceful failure.** Broken images hide themselves via `onerror` rather than leaving a dead icon in the layout.

### Adding a post

```js
const POSTS = [
  { id:3, url:'videos/aug02.mp4', type:'video', caption:'Form check.', category:'Videos', source:'' },
];
```

`type` accepts `video` or `image`. `source` is an optional outbound credit link. Feed items render newest-first.

---

## Design

| Token | Value | Use |
|---|---|---|
| `--paper` | `#eef2f9` | Page background |
| `--navy` | `#101d42` | Wordmark, headings |
| `--cobalt` | `#2745d6` | Accents, tags, active states |
| `--electric` | `#3f5bff` | Highlights |
| `--steel` | `#5c6a92` | Secondary text |

Typography is **Anton** for the wordmark, **Inter** for body copy, and **JetBrains Mono** for eyebrow labels and counters. A fixed blueprint grid sits behind the page under a radial mask, reinforcing the technical-log feel. Fully responsive, mobile-first — the wordmark scales with `clamp()`.

---

## Stack

HTML · CSS · Vanilla JavaScript · Google Fonts · GitHub Pages

No dependencies, no tracking, no backend.

---

## Structure

```
zjim/
├── index.html          # entire site: markup, styles, data, logic
└── videos/             # self-hosted training clips
```

---

© PROJ.ZERO
