# Property Notebook — Prototype

A basic, voice-assisted notebook for real estate agents: structured fields (address, owner, list price, etc.), a "record → auto-fill" flow powered by Claude, and simple reminders. Single self-contained `index.html`, no build step.

## Run it locally (fastest way to test)
Just open `index.html` in Chrome. Voice recording needs either `localhost` or `https://` — opening the file directly (`file://`) may block the microphone in some browsers, so if that happens, run a tiny local server instead:

```
python3 -m http.server 8000
```
then visit `http://localhost:8000`.

## Put it on GitHub Pages (to test from your phone too)
1. Create a new GitHub repo (public or private both work for Pages on a paid plan; public is simplest on the free plan).
2. Add `index.html` (and this README) to the repo, commit, push.
3. In the repo: **Settings → Pages → Source → Deploy from a branch**, pick `main` and `/ (root)`, save.
4. GitHub gives you a URL like `https://yourusername.github.io/repo-name/` — that's HTTPS by default, so the microphone will work.

## Before it does anything AI-related
Click the ⚙ icon and paste in your own Anthropic API key (get one at console.anthropic.com). The key is stored only in your browser's localStorage and is sent directly to Anthropic's API — nothing passes through a server of ours, because there isn't one yet.

**Important:** this "paste your key into the browser" approach is fine for testing this alone, but do not share this link with anyone else once your key is in it on a shared/public device — anyone using that browser could see and use your key. A real version would move the API key to a backend before anyone but you touches it.

## What's real vs. mocked here
- Voice-to-text: real, using your browser's built-in speech recognition (Chrome works best; Safari/iPhone support is inconsistent).
- AI field extraction: real, calling Claude Haiku directly from the browser.
- Data storage: real, but local-only (browser localStorage) — nothing syncs between devices yet.
- Reminders: stored and sorted for real, but notifications only fire while this tab is open in a browser — no true OS-level alarms yet. That needs a native app (or at least a backend + push notifications).

## Known limitations of this prototype
- No login/accounts — it's single-user, single-browser.
- No backend, so nothing is backed up if you clear your browser data.
- Speech recognition quality depends entirely on the browser you use.
