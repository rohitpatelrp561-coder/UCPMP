# UCPMP 2024 Compliance Chatbot

Marketing uploads a photo of an item (brand reminder, gift, leaflet) and the bot returns
APPROVED / NOT APPROVED / NEEDS COMPLIANCE REVIEW with reasons, based on UCPMP 2024.
Advisory only: Compliance gives final approval.

## Run locally
```bash
npm install
cp .env.example .env      # then fill values
export $(grep -v '^#' .env | xargs)
npm start                 # http://localhost:3000
```

## Push to GitHub
```bash
git init
git add .
git commit -m "UCPMP compliance chatbot"
git branch -M main
git remote add origin https://github.com/<your-org>/ucpmp-compliance-bot.git
git push -u origin main
```
Use a **private** repository. Never commit `.env`.

## Deploy on Render
1. Render dashboard → **New → Blueprint** → select the repo (uses `render.yaml`)
   (or **New → Web Service**: Build `npm install`, Start `npm start`).
2. Set environment variables: `ANTHROPIC_API_KEY`, `APP_PASSWORD`
   (optional: `ANTHROPIC_MODEL`, `VALUE_CAP_INR`).
3. Deploy. Open the URL; the browser asks for a password (any username, password = `APP_PASSWORD`).

## Customising rules
Edit the `SYSTEM` prompt in `server.js` (rules, item list, value cap) and redeploy.
