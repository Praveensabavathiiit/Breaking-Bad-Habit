# Rewire — break the habit, one day at a time

A GenAI-powered habit-breaking companion built for **PromptWars Hyderabad 2026** (Main Challenge: *Breaking Bad Habits & Addiction*).

## The idea

Most habit trackers just count days. Rewire uses Generative AI as the **core support mechanism** — the part that actually helps in the moment:

1. **Personalized plan** — describe your habit, reason, and goal → the AI coach writes a plan tailored to your specific trigger
2. **Personalized tracking** — daily check-ins (on track / slip + mood + trigger), streaks, best streak, success rate
3. **Adaptive coaching** — "Get today's nudge" reads your actual streak and recent check-ins and coaches you where you are — encouraging on a streak, compassionate after a slip
4. **In-the-moment support** — "I'm craving right now" gives an immediate, healthy coping response (urge-surfing, delay, breathing) when it matters most

## How GenAI is the core (not bolted on)

Four distinct prompts power four different jobs: plan generation, adaptive nudges, craving support, and structured output. Remove the AI and the product stops working — that's the brief's requirement met.

## Architecture

- **Frontend:** single-file HTML/CSS/JS, no framework, no build step
- **AI:** Groq (Llama 3.3 70B) via the user's own API key (nothing hardcoded)
- **Storage:** `localStorage` — habit data is private and single-user, so it lives on the user's own device. Persists across sessions, zero setup, works offline.

## How to run

1. Open `index.html` (or the deployed link)
2. Paste a free Groq key from https://console.groq.com/keys
3. Pick your habit, set a goal, generate your plan

## Tests

Open `tests.html` — unit tests for the streak logic, helpers, and the `escHtml` XSS-sanitization function that AI output is routed through before rendering.

## Safety

Rewire supports everyday behaviour change, not clinical treatment. It shows a standing note that serious addictions deserve professional support, and its coping guidance is strictly healthy (no pain- or punishment-based techniques).

## Rubric alignment

- **Problem alignment** — nudges, tracking, adaptive coaching, and support mechanisms, all AI-driven
- **Security** — user-supplied key, all AI output HTML-escaped, no secrets in repo
- **Accessibility** — ARIA roles, live regions, keyboard nav, focus rings, modal Escape-to-close, reduced-motion
- **Efficiency** — no dependencies, single network call per action
- **Testing** — unit tests for core logic
- **Code quality** — pure helpers separated from DOM/network, commented throughout
