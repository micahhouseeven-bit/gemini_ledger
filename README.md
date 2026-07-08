# Ledger (Gemini edition — free)

A personal stock research checklist, running on Google's Gemini API. Enter a ticker, it runs a live Google Search and scores the company against a 12-factor fundamentals checklist, then gives an overall Buy/Hold/Pass call plus three closing ratings: riskiness (1–10), a target buy price, and an overall rating (1–10).

This version runs entirely on Gemini's **free tier** — Gemini 2.5 Flash and Flash-Lite include free tokens *and* free Google Search grounding (up to 500 requests/day). No billing account, no credit card. It's a static, single-file site — no build step, no backend.

## Set up

### 1. Create the repo
Create a new GitHub repository and add `index.html` and `README.md` — either upload them in the GitHub web UI, or:
```
git init
git add index.html README.md
git commit -m "Add Ledger (Gemini edition)"
git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPO.git
git push -u origin main
```

### 2. Turn on GitHub Pages
In the repo: **Settings → Pages → Build and deployment → Source: Deploy from a branch → Branch: main / (root)**. Save. GitHub gives you a URL like `https://YOUR_USERNAME.github.io/YOUR_REPO/` within a minute or two — that's your live app.

### 3. Get a free Gemini API key
Go to [aistudio.google.com/apikey](https://aistudio.google.com/apikey), sign in with a Google account, and click **Create API key**. No credit card, no billing setup required for the free tier.

### 4. Connect the key
Open your Ledger URL, click **"API key & model"** at the top, paste the key in, hit Save. It's stored only in that browser's local storage — never touches the GitHub repo, never leaves your device except in direct calls to `generativelanguage.googleapis.com`.

That's it — type a ticker and hit Research.

## Notes

- **Cost: $0.** Gemini 2.5 Flash and Flash-Lite are free at the API level, and Google Search grounding is free up to 500 requests/day (shared between the two models) — plenty for personal use. If Google changes these terms in the future, check [ai.google.dev/gemini-api/docs/pricing](https://ai.google.dev/gemini-api/docs/pricing) for current limits.
- **Rate limits:** the free tier also caps requests per minute (roughly 10–15 depending on model) — if you hit a `429` error, wait a minute and try again.
- **Model choice:** Gemini 2.5 Flash is the default (better research quality); Flash-Lite is faster and even higher-throughput if you want to run a lot of lookups.
- **Data usage:** on the free tier, Google may use your prompts to improve their products (this is disclosed on their pricing page). If that matters to you, that's a good reason to eventually move to a paid project instead — same code, just enable billing on your Google Cloud project.
- **Security:** this app calls the Gemini API directly from your browser, so your API key lives in that browser's local storage in plain text. Fine for a personal tool on a device you control — don't paste your key in on a shared or public computer, and don't repurpose this into something you hand out to other people with your key baked in.
- **History:** past lookups are cached in local storage so you can revisit them without using more of your daily quota. Local storage is per-browser — it won't sync across devices.
- **Not investment advice.** This is a research aid that reads public information at the moment you run it. It can miss recent news, misread a source, or lag real-time pricing. Verify anything material yourself before acting on it.

## Files

- `index.html` — the whole app.
