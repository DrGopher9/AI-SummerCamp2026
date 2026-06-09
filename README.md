# AI & Data Science Camp — Camp Command Center

**Alexandria Technical & Community College — Summer 2026**

A student-facing web app for the ATCC AI & Data Science Camp. Built for 9–12th grade students exploring AI, data science, and cybersecurity over a multi-day camp experience.

---

## Live Site

🔗 [https://drgopher9.github.io/AI-SummerCamp2026](https://drgopher9.github.io/AI-SummerCamp2026)

---

## What This Is

A guided, interactive web app that students follow throughout each day of camp. Each day is broken into sections that unlock sequentially — students must submit a response to unlock the next block of content. Instructor responses are collected via embedded Microsoft Forms into OneDrive Excel files for live monitoring.

---

## File Structure

```
AI-SummerCamp2026/
├── index.html          ← Camp home page / day selector
├── day1.html           ← Day 1 full interactive experience
├── README.md           ← This file
```

> Days 2–4 pages will be added as the camp is built out.

---

## Features

- 🌙 Dark / light theme toggle (persists across pages)
- 🔒 Sequential section unlocking — students can't skip ahead
- 📋 Microsoft Forms embedded in each section for response collection
- 💻 Copy buttons on every terminal command
- 📊 Live progress bar tracking day completion
- 📱 Responsive — works on Pi 400 Chromium browser

---

## Day 1 Sections

| # | Section | Time | Unlocks When |
|---|---|---|---|
| 01 | Intro & Icebreaker | 9:00 – 9:35 | Always open |
| 02 | AI & Data Science | 9:35 – 10:30 | Form 1 submitted |
| 03 | Pi 400 Setup | 10:45 – 11:30 | Form 2 submitted |
| 04 | Frontier Models | 12:00 – 1:00 | Form 3 submitted |
| 05 | Local Models | 1:00 – 2:00 | Form 4 submitted |
| 06 | Exploration & Wrap Up | 2:15 – 4:00 | Form 5 submitted |

---

## Setup Instructions

### 1. Enable GitHub Pages
- Go to repo **Settings → Pages**
- Source: **Deploy from a branch**
- Branch: **main** / root
- Save — site will be live at `https://drgopher9.github.io/AI-SummerCamp2026`

### 2. Create Microsoft Forms
Create 6 forms in your school OneDrive account. See the **Forms Guide** section below for exact questions for each form.

### 3. Embed Forms into day1.html
For each form:
1. Open the form in Microsoft Forms
2. Click **Share → Embed**
3. Copy the `<iframe>` code
4. In `day1.html`, find the comment `<!-- FORM_EMBED_X -->` (where X is 1–6)
5. Replace the comment with your iframe code

### 4. Update the Server IP
In both `index.html` and `day1.html`, search for `10.2.128.89` and update to the current IP of the camp Ollama server. Check the IP the morning of camp with `hostname -I` on the server machine.

### 5. Pre-camp Checklist
- [ ] GitHub Pages enabled and site loading correctly
- [ ] All 6 Microsoft Forms created and embedded
- [ ] Server IP confirmed and updated in both files
- [ ] Site tested on a Pi 400 in Chromium
- [ ] Student Open WebUI accounts pre-created
- [ ] Theme toggle tested (dark and light)
- [ ] All copy buttons tested

---

## Forms Guide

### Form 1 — Icebreaker Check-in
**Questions:**
1. What is your first name? *(Short answer)*
2. What is your team name? *(Short answer)*
3. Write one of your 5 Hot Take or Fact statements here — make it your best one. *(Long answer)*

---

### Form 2 — AI & Data Science Check
**Questions:**
1. Which app did your pair get for the "Who's Feeding the Machine?" activity? *(Short answer)*
2. Who benefits most from that app's AI — you or the company? Explain in one sentence. *(Long answer)*
3. You guessed how many times AI made a decision about you today. Now that you've learned more — what's your revised answer? *(Short answer)*

---

### Form 3 — Pi 400 Setup Check
**Questions:**
1. What is your first name? *(Short answer)*
2. What is your Pi setup status right now? *(Multiple choice)*
   - ✅ Ollama installed, Gemma running, all good
   - ⏳ Still installing or downloading
   - ⚠️ Hit an issue — need help
3. What did Gemma say when you asked it "What is artificial intelligence in one sentence?" — paste or summarize the response. *(Long answer)*

---

### Form 4 — Frontier Models Check
**Questions:**
1. What is your first name? *(Short answer)*
2. Which frontier model gave the best response to the YouTube algorithm prompt, and why? *(Long answer)*
3. What is one weakness you noticed in any of the four models during the demo? *(Long answer)*

---

### Form 5 — Local Models Check
**Questions:**
1. What is your first name? *(Short answer)*
2. After using the camp server (Llama 3.1 8B) and your Pi (Gemma 2B), how did they compare to the frontier models you saw this morning? *(Long answer)*
3. Looking at the comparison table — which option would you personally choose and why? Is there a right answer? *(Long answer)*

---

### Form 6 — End of Day Reflection
**Questions:**
1. What is your first name? *(Short answer)*
2. What is one thing you learned today that genuinely surprised you? *(Long answer)*
3. What is one thing you want to explore more this week? *(Long answer)*
4. What would you build if you could build anything with AI? *(Long answer)*
5. Describe your system prompt AI personality from Round 2 — what did you build and how did it behave? *(Long answer)*

---

## Instructor Notes

### Monitoring Responses Live
Each Microsoft Form automatically saves responses to an Excel file in your OneDrive. Open these files on your instructor machine before camp starts and keep them open — they update in real time as students submit.

**Tip:** Sort by the "Name" column so you can quickly spot which students are stuck or haven't submitted yet.

### Server IP Changes
The camp Ollama server uses DHCP. Check the IP address each morning before students arrive:
```bash
hostname -I
```
Update `10.2.128.89` in both `index.html` and `day1.html` if it has changed.

### Emergency Fallback
If the embedded forms fail to load (network issue, OneDrive outage):
- Students can still use the "Mark complete & unlock" button to progress through sections
- Collect responses verbally or on paper as a backup
- All terminal commands and content are still fully accessible without the forms

### Adding Future Days
To add Day 2, 3, or 4:
1. Duplicate `day1.html` and rename it `day2.html` etc.
2. Update the content for that day
3. Update the nav links in all files to enable the new day
4. Create the corresponding Microsoft Forms
5. Update this README

---

## Hardware Reference

### Student Pi 400s
- **OS:** Raspberry Pi OS Full Desktop
- **Username:** Student's first name
- **Password:** `Password01`
- **Browser:** Chromium (pre-installed)
- **AI Model:** Gemma 2B via Ollama

### Camp AI Server (Machine 1)
- **OS:** Ubuntu 26.04 LTS
- **GPU:** NVIDIA RTX 5000 32GB
- **Services:** Ollama + Open WebUI + ComfyUI
- **Access:** `http://[SERVER-IP]:3000`
- **Default model:** Llama 3.1 8B

---

## Quick Command Reference

```bash
# Install Ollama (run on student Pi)
curl -fsSL https://ollama.com/install.sh | sh

# Pull Gemma 2B
ollama pull gemma:2b

# Run Gemma 2B
ollama run gemma:2b

# Exit Ollama
/bye

# Check Pi IP address
hostname -I

# List downloaded models
ollama list
```

---

## Credits

Built by Steven Van Voorhis — Faculty, Cybersecurity, Virtualization & Networking Program  
Alexandria Technical & Community College  
[github.com/DrGopher9](https://github.com/DrGopher9)

---

*Last updated: June 2026*
