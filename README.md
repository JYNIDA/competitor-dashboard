# EO Global — Competitor Tier Dashboard

A single-page dashboard for tracking and analyzing YouTube channels that compete with or complement [EO Global](https://www.youtube.com/@eoglobal).

**Live Demo:** [competitor-dashboard.vercel.app](https://competitor-dashboard.vercel.app) *(update this link with your actual Vercel URL)*

## What It Does

- Displays competitor channels in **Card** or **Matrix** view
- Categorizes channels by type: **Direct** / **Potential** / **Big Media**
- Auto-assigns tiers (S/A/B/C) based on subscriber count
- Fetches live stats (subscribers, views, thumbnails) via **YouTube Data API v3**
- Tracks upload frequency, trending videos, and avg views per channel
- Add/remove channels and filter/sort in real time
- All data stored in browser `localStorage` — no backend needed

## Pre-loaded Channels (15+)

Y Combinator, a16z, Fireship, Dwarkesh Patel, Lenny's Podcast, OpenAI, Anthropic, Two Minute Papers, WSJ, Bloomberg, TED, and more.

## How to Run Locally

Just open `index.html` in any browser. That's it — no install, no server.

```
git clone https://github.com/JYNIDA/competitor-dashboard.git
cd competitor-dashboard
open index.html
```

## Project Structure

```
competitor-dashboard/
  index.html    ← entire app (HTML + CSS + JS in one file, ~1,600 lines)
  README.md     ← this file
```

### Inside index.html

| Section | Lines (approx) | What it does |
|---------|----------------|--------------|
| CSS Variables & Styles | 1–890 | Dark theme, card layouts, matrix grid, modals |
| HTML | 890–970 | Header, filters, card container, add-channel modal |
| Channel Data | 975–995 | Pre-loaded array of 15+ competitor channels |
| Core Logic | 1000–1200 | `init()`, `loadChannels()`, YouTube API fetch, data merge |
| Rendering | 1200–1400 | Card/matrix view rendering, tier badges, summary bar |
| Interactions | 1400–1582 | Filters, sorting, add/remove channel, modal controls |

## How to Modify

### Change channel list
Edit the `DEFAULT_CHANNELS` array around **line 977**. Each channel looks like:
```js
{ id: 'UCxxx', name: 'Channel Name', handle: '@handle', type: 'direct', subscribers: 0, videoCount: 0, avgViews: 0, notes: 'Why this channel matters', avatar: '', videos: [] }
```
- `type`: `'direct'` | `'potential'` | `'bigmedia'`

### Change styles
CSS variables are at the top of the file (**lines 10–29**). Key variables:
```css
--bg: #0f0f0f;        /* background */
--surface: #272727;    /* card background */
--tier-s: #fbbf24;     /* S-tier color (gold) */
--tier-a: #a78bfa;     /* A-tier color (purple) */
```

### Enable live YouTube data
1. Get a [YouTube Data API v3](https://console.cloud.google.com/apis/library/youtube.googleapis.com) key
2. Paste it in the API Key field in the dashboard header
3. Click **Refresh**

## Contributing

1. Clone the repo
2. Create a branch: `git checkout -b your-name/what-you-changed`
3. Make changes to `index.html`
4. Commit and push: `git push origin your-name/what-you-changed`
5. Open a Pull Request on GitHub

Since the entire app is one file, describe **which section** you changed (CSS / data / logic / rendering) in your PR description.
