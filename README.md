# GitHub + Jira Integration Guide

A beginner-friendly, step-by-step guide to connect your GitHub repository with Jira so you can track commits, branches, and pull requests directly from your Jira tickets.

---

## Objectives

- Establish a seamless connection between GitHub and Jira to unify development and project management workflows
- Enable automatic traceability between code changes and Jira tickets
- Reduce manual status updates by automating ticket transitions based on GitHub activity
- Improve team visibility into development progress directly from the Jira board
- Automate Jira ticket transitions so that creating a branch moves the ticket to "In Progress" and merging a PR moves it to "Ready for QA/Testing"

---

## Advantages of GitHub + Jira Integration

| Advantage | Description |
|-----------|-------------|
| **Full Traceability** | Every commit, branch, and PR is linked to a Jira ticket — creating a clear audit trail |
| **Time Savings** | No need to manually update Jira tickets; automation handles status transitions |
| **Better Collaboration** | Developers and project managers share a single source of truth |
| **Faster Code Reviews** | Reviewers can see the Jira context (requirements, acceptance criteria) directly from the PR |
| **Real-Time Visibility** | Managers see development progress on the Jira board without asking developers for updates |
| **Reduced Context Switching** | Navigate between Jira and GitHub with one click — no searching for related items |
| **Free to Use** | The GitHub for Jira app is provided by Atlassian at no additional cost |
| **Automated Workflow Transitions** | Jira tickets move automatically — branch creation → "In Progress", PR merged → "Ready for QA/Testing" — no manual dragging needed |
| **QA Handoff Without Communication Gaps** | QA team instantly knows a feature is ready for testing when the ticket moves automatically after a merge |
| **No Manual Updates for Developers** | Developers focus on coding — no need to open Jira and drag tickets between columns manually |
| **PM/Scrum Master Visibility** | Project managers and scrum masters see real-time progress without asking developers for status updates |
| **QA No Longer Chases Developers** | QA doesn't need to follow up with devs to ask "is this ready?" — the ticket moves automatically and has full event logs (commits, branches, PRs) as proof of progress |

---

## What This Integration Does

Once connected, you'll be able to:

- See GitHub commits, branches, and pull requests inside Jira tickets
- Automatically move Jira tickets when you create a branch or merge a PR
- from Jira → GitHub (and vice versa) to jump between tools
- Track development progress without leaving Jira

---

## Before You Start

Make sure you have:

| Requirement | Details |
|-------------|---------|
| Jira Account | You need **admin access** to your Jira project (Cloud version) |
| GitHub Account | You need **admin access** to your GitHub repository |
| Browser | Any modern browser (Chrome, Safari, Firefox) |

> ⚠️ This guide is for **Jira Cloud** (the web version at `yourteam.atlassian.net`). If you use Jira Server/Data Center, the steps are slightly different.

---

## Part 1: Install the GitHub App in Jira

### Step 1 — Open Jira Settings

1. Log in to your Jira at `https://yourteam.atlassian.net`
2. Click the **⚙️ gear icon** (top-right corner)
3. Click **"Apps"** from the dropdown menu

![Location: Top-right gear icon → Apps]

---

### Step 2 — Find the GitHub App

1. On the left sidebar, click **"Find new apps"**
2. In the search bar, type: **"GitHub for Jira"**
3. Find the app called **"GitHub for Jira"** (by Atlassian)
4. Click **"Get app"** (it's free)
5. Click **"Get it now"** to confirm installation

> Wait for the installation to complete. You'll see a success message.

---

### Step 3 — Open the GitHub for Jira Configuration

1. After installation, you'll be redirected to the app settings
2. If not, go to: **⚙️ Settings → Apps → Manage apps → GitHub for Jira → "Get started"**
3. You'll see a page that says **"Connect GitHub to Jira"**

---

## Part 2: Connect Your GitHub Account

### Step 4 — Start the Connection

1. On the "Connect GitHub to Jira" page, click **"Connect GitHub organization"**
2. A popup will appear asking you to log in to GitHub
3. Log in with your GitHub account (e.g., `Jmarco07`)

---

### Step 5 — Install the Jira App on GitHub

1. After logging in, GitHub will ask: **"Where do you want to install Jira?"**
2. Select your **GitHub account** or **organization** (e.g., `Jmarco07`)
3. Choose which repositories to connect:
   - **"All repositories"** — connects all current and future repos
   - **"Only select repositories"** — pick specific repos (e.g., `github_demo`)
4. Click **"Install"**

> 💡 Recommendation: Choose **"Only select repositories"** and select the repos you need. You can always add more later.

---

### Step 6 — Confirm the Connection

1. You'll be redirected back to Jira
2. You should see your GitHub organization/account listed as **"Connected"**
3. The status will show **"Syncing..."** — this means Jira is importing your GitHub data

> ⏳ The initial sync may take a few minutes depending on how many commits/PRs you have.

---

## Part 3: How to Use the Integration

### Step 7 — Link Commits to Jira Tickets

The magic happens when you include your **Jira ticket ID** in your commit messages, branch names, or PR titles.

**Jira ticket IDs look like:** `PROJ-123`, `CUS-45`, `API-7`

(You can find your ticket ID at the top of any Jira ticket)

#### Example: Commit Message

```bash
git commit -m "CUS-12 add customer search endpoint"
```

#### Example: Branch Name

```bash
git checkout -b CUS-12-add-customer-search
```

#### Example: Pull Request Title

```
CUS-12 Add customer search endpoint
```

> As long as the Jira ticket ID (e.g., `CUS-12`) appears in the commit, branch, or PR — Jira will automatically link them.

---

### Step 8 — View GitHub Activity in Jira

1. Open any Jira ticket (e.g., `CUS-12`)
2. Scroll down to the **"Development"** section on the right panel
3. You'll see:
   - 🔵 **Branches** — any branch with the ticket ID
   - 🟢 **Commits** — any commit with the ticket ID
   - 🟣 **Pull Requests** — any PR with the ticket ID
4. Click on any item to jump directly to GitHub

![Development panel in Jira](asset/Screenshot%202026-07-15%20at%207.46.57AM.png)

![Branches under Development](asset/Screenshot%202026-07-15%20at%207.48.09AM.png)

![Commits under Development](asset/Screenshot%202026-07-15%20at%207.48.26AM.png)

![Pull Requests under Development](asset/Screenshot%202026-07-15%20at%207.48.41AM.png)

---

### Step 9 — View Jira Info in GitHub (Optional)

When you open a Pull Request on GitHub:

1. You'll see the Jira ticket linked at the bottom of the PR description
2. Clicking it takes you directly to the Jira ticket
3. The PR status (open/merged/declined) is reflected in Jira automatically

![GitHub interface of a merged PR](asset/Screenshot%202026-07-15%20at%207.49.05AM.png)

---

## Part 4: Automate Jira Ticket Transitions (Optional)

You can make Jira automatically move tickets between columns when you take actions in GitHub.

### Step 10 — Set Up Automation Rules

1. In Jira, go to **⚙️ Project Settings** (bottom-left of your project board)
2. Click **"Automation"** in the left sidebar
3. Click **"Create rule"**

![Automation tab in Jira](asset/Screenshot%202026-07-15%20at%207.49.20AM.png)

![Automation rule setup](asset/Screenshot%202026-07-15%20at%208.02.21AM.png)

#### Rule 1: Move ticket to "In Progress" when a branch is created

| Field | Value |
|-------|-------|
| Trigger | "Branch created" |
| Action | "Transition issue to: In Progress" |

**Process:**
1. Developer picks up a Jira ticket (e.g., `SCRUM-6`)
2. Developer creates a branch: `git checkout -b feature/SCRUM-6-description`
3. Jira automatically moves `SCRUM-6` from "To Do" → **"In Progress"**

Click **"Save"** and **"Turn on rule"**

#### Rule 2: Move ticket to "In Review" when a PR is opened

| Field | Value |
|-------|-------|
| Trigger | "Pull request created" |
| Action | "Transition issue to: In Review" |

**Process:**
1. Developer finishes coding and pushes the branch
2. Developer opens a Pull Request on GitHub with the ticket ID in the title
3. Jira automatically moves the ticket from "In Progress" → **"In Review"**

#### Rule 3: Move ticket to "Ready for QA/Testing" when a PR is merged

| Field | Value |
|-------|-------|
| Trigger | "Pull request merged" |
| Action | "Transition issue to: Ready for QA/Testing" |

**Process:**
1. Reviewer approves and merges the Pull Request on GitHub
2. Jira automatically moves the ticket from "In Review" → **"Ready for QA/Testing"**
3. QA team sees the ticket in their column and begins testing — no manual handoff needed

> 💡 These rules save time — your board updates automatically based on your GitHub activity.
>
> **Full automated flow:**
> `To Do` → (branch created) → `In Progress` → (PR opened) → `In Review` → (PR merged) → `Ready for QA/Testing`

---

## Part 5: Verify Everything Works

### Step 11 — Test the Integration

1. Create a Jira ticket (note the ID, e.g., `CUS-1`)
2. In your terminal:

```bash
cd ~/Documents/customerAPI

# Create a branch with the ticket ID
git checkout -b CUS-1-test-integration

# Make a small change
echo "test" >> test.txt

# Commit with the ticket ID
git commit -am "CUS-1 test jira github integration"

# Push
git push origin CUS-1-test-integration
```

3. Go back to Jira → open ticket `CUS-1`
4. Check the **"Development"** panel on the right
5. You should see your branch and commit listed

---

## Summary — Quick Reference

| Action | Where | Format |
|--------|-------|--------|
| Commit | Terminal | `git commit -m "CUS-12 your message"` |
| Branch | Terminal | `git checkout -b CUS-12-description` |
| Pull Request | GitHub | Title: `CUS-12 Description` |
| View links | Jira | Ticket → Development panel (right side) |

---

## Troubleshooting

| Problem | Solution |
|---------|----------|
| Don't see "Development" panel in Jira | Enable it: Ticket → **"..."** menu → **"Configure"** → drag "Development" to the layout |
| Commits not showing in Jira | Make sure the ticket ID (e.g., `CUS-12`) is in the commit message exactly as shown in Jira |
| GitHub org not showing during setup | Make sure you're logged into the correct GitHub account that owns the repo |
| Sync seems stuck | Go to **Apps → GitHub for Jira → "..."** next to your org → **"Restart sync"** |
| "Permission denied" during install | You need to be an **admin** of the GitHub organization/account |
| Automation rules not triggering | Check that the ticket status names in your rules match your board column names exactly |

---

## Removing the Integration (If Needed)

### Remove from Jira:
1. Go to **⚙️ Settings → Apps → Manage apps**
2. Find **"GitHub for Jira"**
3. Click **"Uninstall"**

### Remove from GitHub:
1. Go to **GitHub → Settings → Applications → Installed GitHub Apps**
2. Find **"Jira"**
3. Click **"Configure"** → **"Uninstall"**

---

## Need Help?

- [Atlassian Official Docs](https://support.atlassian.com/jira-cloud-administration/docs/integrate-with-github/)
- [GitHub for Jira App Page](https://github.com/marketplace/jira-software-github)
