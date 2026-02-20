# 🛠️ Instructions — hello-actions-team

## What This Is
A GitHub Actions workflow that builds up a README live during a
demo session as a personal team intro. Each job adds a section to
the README. Fully repeatable via a `reset` input.

---

## Prerequisites
- GitHub account: `jashkahar`
- Repo: `jashkahar/hello-actions-team` (public)
- Git configured locally
- GitHub CLI (`gh`) optional but helpful

---

## Repo Setup

### 1. Create the repo
```bash
gh repo create jashkahar/hello-actions-team --public --clone
cd hello-actions-team
```
Or create manually on github.com then clone.

### 2. Create the folder structure
```bash
mkdir -p .github/workflows
mkdir assets
touch .github/workflows/intro.yml
touch README.md
touch DESIGN.md
touch INSTRUCTIONS.md
```

### 3. Set workflow permissions
Go to:
`repo → Settings → Actions → General → Workflow permissions`
Set to: **Read and write permissions** ✅
This is required so the workflow can commit to the README.

---

## How the Workflow Works

### Trigger
```yaml
on:
  workflow_dispatch:
    inputs:
      reset:
        description: 'Reset README before running?'
        type: boolean
        default: true
```
Manually triggered from the Actions tab. The `reset` input
controls whether the README is wiped before building.

---

### How README Updates Work
Each job:
1. Checks out the repo
2. Appends a markdown section to `README.md`
3. Commits and pushes the change

```yaml
- name: Update README
  run: |
    cat >> README.md << 'EOF'
    [markdown content here]
    EOF

- name: Commit and push
  run: |
    git config user.name "github-actions[bot]"
    git config user.email "github-actions[bot]@users.noreply.github.com"
    git add README.md
    git commit -m "intro: add [section name]"
    git push
```

---

### How the Reset Job Works
Job 0 runs first when `reset=true`:
```yaml
reset:
  if: ${{ inputs.reset == true }}
  runs-on: ubuntu-latest
  steps:
    - uses: actions/checkout@v4
    - name: Reset README
      run: echo "<!-- intro in progress... -->" > README.md
    - name: Commit reset
      run: |
        git config user.name "github-actions[bot]"
        git config user.email "github-actions[bot]@users.noreply.github.com"
        git add README.md
        git commit -m "reset: wipe README for fresh intro run"
        git push
```

---

### How Job Dependencies Work
Each job waits for the previous to finish:
```yaml
who-i-am:
  needs: reset        # waits for reset to finish

my-journey:
  needs: who-i-am     # waits for who-i-am to finish

what-ive-shipped:
  needs: my-journey

what-excites-me:
  needs: what-ive-shipped
```
This creates the sequential "lighting up" effect in the UI.

---

### How the Job Summary Works
In the final job, write to `$GITHUB_STEP_SUMMARY`:
```yaml
- name: Write Job Summary
  run: |
    cat >> $GITHUB_STEP_SUMMARY << 'EOF'
    # 👋 Hello, Actions Team!
    [full markdown content — see DESIGN.md]
    EOF
```
This renders as a rich markdown card on the workflow run page.

---

## Workflow Permissions
Add this to `intro.yml` at the top level:
```yaml
permissions:
  contents: write
```
Required for the workflow to commit README changes.

---

## How to Practice / Make It Repeatable

### Every practice run:
1. Go to `Actions` tab in the repo
2. Select `Team Intro` workflow
3. Click `Run workflow`
4. Set `Reset README` to `true` ✅
5. Click `Run workflow` green button
6. Watch it run — navigate to repo root to watch README update live

### To verify reset worked:
Check `README.md` — should show only:
```
<!-- intro in progress... -->
```
before job 1 starts.

---

## How to Record Backup Video

### Tools
- **Mac:** QuickTime → New Screen Recording
- **Windows:** Xbox Game Bar (Win+G) or OBS
- **Cross-platform:** OBS Studio (free)

### What to record
1. Start recording
2. Have the repo open in one browser tab
3. Have the Actions tab open in another
4. Click `Run workflow` with `reset=true`
5. Narrate as each job runs
6. End on the Job Summary page
7. Stop recording

### Tips
- Use a clean browser profile (no extensions visible)
- Zoom browser to 125% for visibility
- Have both tabs visible — split screen or switch between them
- Keep it to 90 seconds

---

## Live Demo Checklist (Day of)

- [ ] Practice run completed successfully at least 3 times
- [ ] Backup video recorded and saved
- [ ] Repo is public
- [ ] Browser zoomed to 125%
- [ ] Actions tab open and ready
- [ ] Repo root tab open (to show README updating)
- [ ] `reset=true` pre-selected
- [ ] Repo link copied and ready to share in chat
- [ ] Internet connection stable 😄

---

## Workflow File Location
`.github/workflows/intro.yml`
See `DESIGN.md` for full content of each section.