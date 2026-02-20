# 🎨 Design Document — hello-actions-team

## Overview
A GitHub Actions workflow that builds up a README live, one section
per job, as a personal intro for the Actions Compute & Storage team
Friday demo session.

**Trigger:** `workflow_dispatch` with `reset` boolean input
**Duration:** ~1-2 minutes live
**Audience:** GitHub Actions Compute & Storage team

---

## Workflow Jobs Overview

| Job | Name | What It Does | README Section Added |
|---|---|---|---|
| 0 | `reset` | Wipes README to blank slate | None |
| 1 | `who-i-am` | Intro, name, role, fun fact | Section 1 |
| 2 | `my-journey` | ASU → LEAPS → DevBox → Actions | Section 2 |
| 3 | `what-ive-shipped` | Key PRs and features so far | Section 3 |
| 4 | `what-excites-me` | Interests, goals, what's next | Section 4 + Job Summary |

---

## README — Section by Section

### Initial State (after reset job)
```markdown
<!-- intro in progress... -->
```
> Blank, just a comment. Clean slate visible to anyone watching the repo.

---

### Section 1 — Who I Am (added by job: `who-i-am`)
```markdown
# 👋 Hi, I'm Jash!
### Software Engineer 2 — GitHub Actions Compute & Storage

> [one line personal tagline — here to build things that make developers faster."]

📍 Redmond, WA i come to the Bellevue Hub regularly!
🎓 MS Computer Science — Arizona State University
⚡ Fun fact: I am a huge Formula 1 fan and love to do Karting!
```

**Speaker notes (what you say live):**
> "So I'm Jash — I just joined the Actions Compute & Storage team
> and I wanted to do my intro in a way that felt on-brand for the team..."

---

### Section 2 — My Journey (added by job: `my-journey`)
```markdown
---
## 🗺️ My Journey

```
🔬 LEAPS Lab, ASU          →     📦 Microsoft DevBox      →     ⚡ GitHub Actions C&S
Energy & Power Systems           Dec 2025                        Jan 2026 (reorg)
[one line what you did]          [one line what you did]         Here now!
```

- **LEAPS Lab @ ASU** — [Built backend to support and run power systems optimizations and also lead AI initiatives]
- **Microsoft DevBox** — Joined Dec 2025, [Just onbaording and figuring out how many more entitlements and access i need :laughing emoji]
- **GitHub Actions C&S** — Came over with the team during the reorg :happy emoji
```

**Speaker notes (what you say live):**
> "after finishing my MS and Before Microsoft I was at an energy systems research lab at ASU — then joined DevBox in December and the
> reorg brought our whole team over here..."

---

### Section 3 — What I've Shipped (added by job: `what-ive-shipped`)
```markdown
---
## 🚀 What I've Shipped (< 2 months in)

| Feature | Description | Repos |
|---|---|---|
| 🖼️ Runner pool image editing | Allow base image + image gen toggle on existing pools | `github`, `github-ui`, `launch`, `actions-dotnet` |
| 📸 Snapshot versioning | Thread SnapshotName/Version through Actions pipeline | `actions-proto`, `actions-broker-worker`, `actions-run-service`, `actions-dotnet` |
| 🧹 Feature flag cleanup | Cleaned up fully shipped FF across the codebase | `github` |

> 22 PRs merged across 9 repos in under 2 months :sillye-emoji
```

**Speaker notes (what you say live):**
> "In the first couple of months I jumped straight into the runner
> pool image editing work — it was a big multi-repo effort and a
> great way to learn how everything connects..."

---

### Section 4 — What Excites Me (added by job: `what-excites-me`)
```markdown
---
## ⚡ What Excites Me

- 🏗️ **Infrastructure at scale** — GitHub Actions runs millions of
  workflows, that scale is fascinating to me
- 🧑‍💻 **Developer Experience** — my passion area, making devs faster
  and less frustrated
- 🔭 **Learning the full compute pipeline** — still connecting all
  the dots and loving it
- 🤝 **This team** — excited to build with everyone

---

*This README was built live by a GitHub Actions workflow.*
*Want to try it yourself? Hit the Run Workflow button 👆*

[![Run Intro](https://img.shields.io/badge/Run%20Intro-Workflow%20Dispatch-2ea44f?logo=githubactions)](
../../actions/workflows/intro.yml)
```

**Speaker notes (what you say live):**
> "What I'm most excited about is the infra scale here and the
> developer experience angle — that's always been what draws me
> to this kind of work. And honestly, really excited to be building
> with this team."

---

## Job Summary — Final Output

Rendered at the end of Job 4. Visible in the workflow run summary page.

```markdown
# 👋 Hello, Actions Team — I'm Jash!

---

## Quick Stats
| | |
|---|---|
| 🎓 | MS CS — Arizona State University |
| 🔬 | Former researcher, LEAPS Energy Lab @ ASU |
| 💼 | Joined Microsoft Dec 2025 — DevBox → Actions C&S |
| 📍 | [Location] |
| ⚡ | Fun fact: [fun fact] |

---

## Shipped in < 2 Months
- 🖼️ Runner pool image editing + image generation toggle
- 📸 Snapshot versioning through the Actions pipeline
- 🧹 Feature flag cleanup
- 📝 22 PRs across 9 repos

---

## What I Care About
> Infrastructure · Developer Experience · Building great tools

---

*Built with GitHub Actions, naturally.*
[![GitHub](https://img.shields.io/badge/github-jashkahar-181717?logo=github)](
https://github.com/jashkahar)
```

---

## Tone & Voice
- Casual but sharp
- Confident without being boastful
- Let the work speak (PRs, repos, numbers)
- A little humor is good — you're using Actions to introduce yourself
  on the Actions team, lean into that self-awareness

---

## Timing Guide

| Job | Approx runtime | What you say |
|---|---|---|
| reset | ~15s | "I'm going to click run and walk you through this..." |
| who-i-am | ~20s | Name, role, fun fact |
| my-journey | ~20s | ASU → LEAPS → DevBox → Actions |
| what-ive-shipped | ~20s | Key features, repos, PRs |
| what-excites-me | ~20s | Passion areas, excited to be here |
| **Total** | **~90s** | **Perfect for 1-2 min slot** |