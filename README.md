# 🐦 Flappy Bird

A browser-based Flappy Bird clone built with HTML5 Canvas and vanilla JavaScript — featuring neon visuals, particle effects, animated sprites, and a scrolling city skyline.

🎮 **Live Demo → [https://dharani2403.github.io/Flappy_bird/](https://dharani2403.github.io/Flappy_bird/)**

---

## ✨ Features

- Smooth bird animation with flapping wings and rotation
- Neon glow effects, gradient pipes, and particle explosion on death
- Scrolling city skyline background with twinkling stars and drifting clouds
- Screen shake on collision
- +1 score popups and progressive difficulty
- High score tracker
- Works with Spacebar, Arrow Up, mouse click, and touch tap

---

## 🗂️ Project Structure

```
Flappy_bird/
├── docs/
│   └── index.html          ← entire game (single file, no dependencies)
└── .github/
    └── workflows/
        └── static-site.yaml  ← CI/CD pipeline for GitHub Pages
```

---

## 🚀 CI/CD Pipeline — What I Learned

This project was also a hands-on introduction to **CI/CD (Continuous Integration / Continuous Deployment)** using **GitHub Actions**.

### What is CI/CD?

| Term | What it means |
|---|---|
| **CI** (Continuous Integration) | Automatically check/validate code every time you push |
| **CD** (Continuous Deployment) | Automatically deploy the app when checks pass |

Instead of manually uploading files every time you make a change, the pipeline does it for you — instantly and reliably.

### How the Pipeline Works

```
You push code to main
        │
        ▼
┌─────────────────────┐
│   Job 1: CHECK      │  ← Validates docs/index.html exists
│   (CI)              │    and contains required HTML tags
└────────┬────────────┘
         │ passes?
         ▼
┌─────────────────────┐
│   Job 2: DEPLOY     │  ← Uploads docs/ folder to GitHub Pages
│   (CD)              │    and makes it live automatically
└─────────────────────┘
```

### Key Concepts I Picked Up

**Workflow triggers** — the pipeline runs automatically on specific git events:
```yaml
on:
  push:
    branches: [main]     # deploy when code lands on main
  pull_request:
    branches: [main]     # only validate on PRs, don't deploy
```

**Jobs and dependencies** — jobs can depend on each other:
```yaml
deploy:
  needs: check           # deploy only runs if check passes
```

**Environments and permissions** — GitHub Pages needs specific write permissions granted in the workflow, not manually.

**Artifacts** — the workflow packages the `docs/` folder as an artifact, hands it to GitHub Pages, and the site goes live at a public URL. No FTP, no manual upload.

**Pull Request safety** — on a PR, only the `check` job runs. The `deploy` job is skipped. This means broken code can never accidentally go live.

### The Deploy Flow in Plain English

1. You edit `docs/index.html` and push to `main`
2. GitHub Actions wakes up and runs the workflow
3. **Check job**: confirms the file exists and has valid HTML structure
4. **Deploy job**: packages the `docs/` folder and publishes it to GitHub Pages
5. Your live site updates within ~30 seconds — no manual steps

---

## 🛠️ Run Locally

No build tools or dependencies needed. Just open the file:

```bash
# Clone the repo
git clone https://github.com/dharani2403/Flappy_bird.git
cd Flappy_bird

# Open directly in browser
open docs/index.html
```

---

## 🎮 Controls

| Input | Action |
|---|---|
| `Space` or `↑` | Flap |
| Mouse click | Flap |
| Tap (mobile) | Flap |
| Any input on Game Over | Restart |

---

## 🧰 Built With

- HTML5 Canvas API
- Vanilla JavaScript (no frameworks)
- GitHub Actions (CI/CD)
- GitHub Pages (hosting)

---

## 📄 License

MIT — free to use and modify.
