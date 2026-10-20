This is **vibe coded software**.

---

# 🌳 ChatGPT JSON Tree Viewer

**Your AI conversation is a tree. Every viewer shows you a list. This one shows you the tree.**

Load an export from ChatGPT, Claude, Grok, DeepSeek, Qwen, Mistral, GLM or opencode — or just a Markdown transcript — and get a map you can actually explore: every branch, every regenerated answer, every "wait, which version did I keep?" moment.

Main UI
![Main UI](docs/screenshot-main.png)

---

## The problem you already know

You ask a question. The answer is *almost* right. You hit **Regenerate**. Then again. And again.

The model keeps one of those answers. The other four disappear — along with that side question you asked three messages ago, and the entire conversation that quietly grew out of it.

Your export still has all of it. It's just… JSON. A wall of `mapping`, `parent`, `children` and UUIDs that no human should read on purpose.

This viewer reads it so you don't have to.

## What you get

**A real tree, not a timeline.** Every message is a node, every regeneration is a sibling branch, and you can pan, zoom and click your way through the whole thing. There's a minimap for when the tree gets ambitious. Colours tell you who's talking — blue for you, green for the model, grey dashed for the system messages hiding in the plumbing.

**A branch panel that keeps its bearings.** Pick any node and see the exact path that leads to it — role chips, message previews, and little arrows to hop between siblings so you can compare what the model said the first time versus the fifth.

**Search that finds the thing you half-remember.** Full-text across every loaded conversation, grouped by conversation, with matches highlighted. No more scrolling through 400 messages hunting for "the bit about the database".

**Copy anything, in whatever shape you need.** Rendered (formatting intact), Markdown, HTML or raw JSON — per message, per selection, or the entire conversation. The changelog has the same treatment, because of course it does.

**Pop any message — or the whole branch — into its own tab.** A real tab beside the app, not a cramped little window, with the same branded header, a view switcher and copy buttons that follow whatever view you're in.

**Get it out of the browser.** Print-ready PDF, the visible branch as HTML / Markdown / JSON (it follows your view), and the graph itself as PNG, JPG or SVG.

**Themes, including the one you didn't ask for.** System (follows your OS light/dark setting, live), light, dark, blue, green, purple — and **Windows XP**, Luna chrome and all. There's a colour picker too, if you're feeling artistic.

**It fits in your pocket.** Single-column layout, bottom navigation, pinch-zoom and two-finger pan on phones.

**Big files don't scare it.** A 300 MB export gets split in a background worker and imported chunk by chunk, without freezing the tab.

**A help section that actually helps.** 18 searchable topics, plus the full changelog with copy buttons and a raw Markdown view — and a tooltip on essentially every control, so nothing is a mystery button.

## Your conversations stay yours

Everything runs in your browser. The file you drop in is parsed, rendered and stored locally — there is no server, no account, no upload, no analytics and no telemetry.

The third-party libraries are pinned with SRI integrity hashes and the page ships a Content Security Policy, so a tampered CDN file gets refused rather than executed. Message bodies are sanitised before rendering, and imported titles, model names and node IDs are escaped everywhere they appear. Imported files are treated as what they are: untrusted input.

The short version: your chats never leave your machine, and the app is built to keep it that way.

## Opening it

1. Download `chatgpt-json-tree-viewer.html`
2. Double-click it — that *is* the install
3. Drop your export onto the graph, or hit **Load File**

No build step, no `npm install`, no "please create an account to continue". One file, one browser tab.

Haven't exported yet? ChatGPT hides it under **Settings → Data Controls → Export Data** (you get an email with a ZIP; the file inside is `conversations.json`). Claude: **Settings → Export Data**. Everyone else: poke around settings for "export".

It needs an internet connection the first time (the pinned libraries and fonts come from a CDN, then your browser caches them). After that, everything works offline except importing an opencode `.db`, which fetches the SQLite engine on demand.

## What it reads

| Where your chats live | What to drop in |
| --- | --- |
| ChatGPT / OpenAI export | `conversations.json` |
| Claude (new and classic exports) | `.json` |
| DeepSeek (exporter, chat export, conversation) | `.json` |
| Grok / xAI backend export | `.json` |
| Mistral | `.json` |
| GLM / Zhipu | `.json` |
| Qwen Chat | `.json` |
| opencode | `opencode.db` (`.db`, `.sqlite`, `.sqlite3`) |
| Anything else | `.md`, `.markdown`, `.txt` — parsed as a transcript |

Multiple files at once? Sure. Each becomes its own entry in the sidebar. Format detection is automatic, and branching survives the trip wherever the source format recorded it.

## Small things that add up

- A minimap, breadcrumbs and role filters, so a 200-message tree stays navigable
- Drag either side panel to whatever width you like — the graph takes the rest
- Search results grouped by conversation, collapsible with one click
- Notifications instead of silent failures when a file won't parse
- Everything is a single HTML file — copy it to a USB stick and it still works

## About that "vibe coded" label

It's one HTML file containing all the CSS and JavaScript, assembled by a human and a rotating cast of language models, then bullied into shape by an unreasonable number of edge cases and a headless browser.

There is no test suite. The test suite is a person clicking things and saying "huh, that shouldn't do that." Which is also how most of the features got added.

It works, it's honest about it, and the whole thing is small enough to read if you don't trust either of us.

## Libraries used

| Library | Purpose |
| --- | --- |
| [D3.js](https://d3js.org) v7.9.0 | Interactive tree map |
| [marked](https://marked.js.org) v9.1.6 | Markdown → HTML rendering |
| [DOMPurify](https://github.com/cure53/DOMPurify) v3.0.6 | Sanitising rendered message HTML |
| [html2canvas](https://html2canvas.hertzen.com) v1.4.1 | PNG / JPG export of the graph |
| [sql.js](https://sql.js.org) v1.10.3 | In-browser SQLite, for reading opencode databases |

Fonts: [DM Sans](https://fonts.google.com/specimen/DM+Sans), [Literata](https://fonts.google.com/specimen/Literata) and [JetBrains Mono](https://fonts.google.com/specimen/JetBrains+Mono), served via Google Fonts.

---

## License

MIT — free to use, modify, and share. See [LICENSE](LICENSE) for details.

---

## Star History

[![Star History Chart](https://api.star-history.com/svg?repos=akivacp/chatgpt-json-tree-viewer&type=date&legend=top-left)](https://www.star-history.com/#akivacp/chatgpt-json-tree-viewer&type=date&legend=top-left)
