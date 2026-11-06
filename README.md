# Cyber Awareness Lab

A free, static website for teaching students to recognize phishing and
social-engineering tricks — built as plain HTML/CSS/JS so it can be hosted for
free on GitHub Pages or Azure Static Web Apps.

## What's inside

- `index.html` — landing page linking the two modules
- `demo-wifi.html` — **Module 1**: a clearly-labeled, simulated fake wifi
  sign-in portal. It never reads, stores, or transmits anything typed into it
  (no backend, no `fetch`, no `localStorage`, no cookies) — submitting just
  clears the fields and reveals an annotated breakdown of the red flags on
  that same screen.
- `quiz.html` — **Module 2**: a scored "Spot the Phish" quiz using fictional
  brand mockups (wifi portal, SMS, pop-up, DM) where students pick out the
  red flag in each scenario.
- `style.css` — shared dark theme styling.

No data is collected anywhere on this site. There is no server-side code,
database, or analytics — it's pure static HTML/CSS/JS.

## Deploy option 1: GitHub Pages (simplest, fully free)

1. Create a new GitHub repository (e.g. `cyber-awareness-lab`).
2. Push these files to the repo root:
   ```bash
   git init
   git add .
   git commit -m "Cyber awareness lab site"
   git branch -M main
   git remote add origin https://github.com/<your-username>/cyber-awareness-lab.git
   git push -u origin main
   ```
3. In the repo on GitHub: **Settings → Pages → Build and deployment**.
   Set **Source** to "Deploy from a branch", branch `main`, folder `/root`.
4. Save. GitHub gives you a URL like
   `https://<your-username>.github.io/cyber-awareness-lab/` within a minute or two.

## Deploy option 2: Azure Static Web Apps (free tier)

Azure Static Web Apps' Free plan is built specifically for static sites like
this one and deploys straight from your GitHub repo via GitHub Actions.

1. Push the same repo to GitHub (steps 1–2 above).
2. In the [Azure Portal](https://portal.azure.com), search **Static Web Apps**
   → **Create**.
3. Fill in:
   - **Subscription / Resource group**: your own (create a new resource group if needed)
   - **Name**: e.g. `cyber-awareness-lab`
   - **Plan type**: **Free**
   - **Deployment source**: **GitHub** → sign in and authorize → pick your
     organization, repository, and `main` branch
   - **Build details**: Build Presets → **Custom**; leave **App location** as
     `/`, **Api location** blank, **Output location** blank (this is a plain
     static site with no build step)
4. Click **Review + create** → **Create**. Azure automatically commits a
   GitHub Actions workflow file (`.github/workflows/azure-static-web-apps-*.yml`)
   into your repo that builds and deploys on every push to `main`.
5. After the first deployment finishes (watch the **Actions** tab in GitHub),
   the Azure portal's **Overview** page shows your live URL, something like
   `https://<random-name>.azurestaticapps.net`.
6. Any future push to `main` redeploys automatically.

### Custom domain (optional, either option)
Both GitHub Pages and Azure Static Web Apps support adding a free custom
domain later via **Settings → Custom domains** (GitHub) or **Custom domains**
in the Static Web App resource (Azure) — not required to get started.

## Using it with students

1. Open Module 1 together and have a volunteer "fill it in" live. Immediately
   after clicking Connect, the page reveals the red-flag breakdown — use that
   as the discussion anchor rather than treating it as a trick to catch them out.
2. Hand off to Module 2 for individual or paired work, then regroup on the
   results and explanations.
3. The footer notes on both pages are there so a student who reads the page
   source (or asks) can immediately confirm nothing is actually transmitted —
   worth pointing out explicitly, since "trust but verify" is part of the lesson.
