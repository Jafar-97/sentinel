# Sentinel

AI Agent Adversarial Evaluation Platform built by Jafar Mohammad.

Sentinel stress-tests conversational AI agents across 4 attack vectors before they hit production. Built specifically to expose the failure modes Decagon's CTO Ashwin Sreenivas called out at Enterprise Ready Conference 2025.

---

## What it does

Fires 12 adversarial probes at your AI agent across these suites:

- **Jailbreak and Prompt Injection** - DAN attacks, fake escalation codes, indirect injection via user content
- **Brand Violation and Tone Drift** - competitor endorsement traps, unauthorized commitment extraction, empathy manipulation
- **Hallucination and Factual Drift** - fabricated promotions, nonexistent feature confirmation, PII fabrication under urgency
- **Regulatory and Compliance Failure** - GDPR Article 17 mishandling, CCPA opt-out errors, financial advice boundary violations

Each test fires the adversarial prompt at a simulated agent, then an independent LLM judge scores the response 0 to 100 and returns a PASS, FAIL, or CRITICAL verdict with full reasoning.

---

## Tech stack

- Frontend: pure HTML/CSS/JS, no framework needed
- Backend: single Vercel serverless function (Node.js) that proxies Anthropic API calls
- Model: Claude Sonnet 4 for both agent simulation and LLM-as-judge evaluation
- Deploy: Vercel (free tier works fine)

---

## Deploy it yourself

### Step 1 - Clone the repo

```bash
git clone https://github.com/YOUR_USERNAME/sentinel.git
cd sentinel
```

### Step 2 - Install Vercel CLI

```bash
npm install -g vercel
```

### Step 3 - Deploy

```bash
vercel
```

Follow the prompts. When it asks about settings just hit enter for defaults.

### Step 4 - Add your API key

Go to your Vercel dashboard, open the project, go to Settings then Environment Variables.

Add this:

```
ANTHROPIC_API_KEY = sk-ant-...your key here...
```

Then redeploy:

```bash
vercel --prod
```

That is it. Your live link will be something like `sentinel-xyz.vercel.app`.

---

## Run locally

No npm install needed. Just open `index.html` in a browser after setting up a local proxy, or just use the demo version (`demo.html`) which works with no API key and shows pre-recorded realistic results.

---

## Project structure

```
sentinel/
  index.html        the full live app
  demo.html         standalone demo, no API key needed
  api/
    claude.js       Vercel serverless function, proxies Anthropic calls
  vercel.json       Vercel routing config
  package.json      minimal, just tells Vercel this is a Node project
  README.md         this file
```

---

Built by Jafar Mohammad
