# TaskDock Promotion Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Apply the approved TaskDock promotion design to the GitHub project page and create ready-to-publish social and Xianyu promotion materials for Windows Codex users.

**Architecture:** Keep product code untouched. Update the public README for search-oriented positioning, update the remote GitHub description/topics through authenticated GitHub tooling, and store the platform copy and 5-yuan listing as a focused promotion kit under `docs/`.

**Tech Stack:** Markdown, Git, GitHub CLI (`gh`) when authenticated, PowerShell verification commands.

## Global Constraints

- Use “Windows” rather than limiting the product to Windows 11.
- Use `TaskDock — Codex Usage & Quota Monitor for Windows` as the display title.
- Use `A lightweight Windows desktop monitor for Codex usage, quotas, tasks, and local token stats.` as the English project description.
- Keep `TaskDock` as the repository name to avoid breaking existing links.
- Include `TaskDock is an unofficial third-party tool and is not affiliated with or endorsed by OpenAI.` in public-facing GitHub copy.
- Do not claim official OpenAI affiliation, authorization, endorsement, partnership, or access to accounts/quotas.
- Do not add spam automation, fake feedback, paid ads, or account/quota/proxy/crack services.
- The Xianyu item is a ¥5 installation and configuration assistance service, not an official software or account sale.
- Preserve the existing download, privacy, support, license, and security links unless a link is actually broken.

---

### Task 1: Rewrite the GitHub README first screen

**Files:**
- Modify: `README.md`
- Reference: `PRIVACY.md`, `USAGE.md`, `SECURITY.md`, `DONATE.md`

**Interfaces:**
- Consumes: Existing TaskDock feature list, download URL, privacy boundary, and support links.
- Produces: A bilingual, search-oriented README first screen that still links to the existing release and policy documents.

- [ ] **Step 1: Capture the current README sections and links**

Run:

```powershell
Get-Content -Raw -Encoding UTF8 README.md
rg -n "releases/latest|PRIVACY.md|USAGE.md|SECURITY.md|DONATE.md|ko-fi|ifdian" README.md
```

Expected: the current download, privacy, support, and license links are present before editing.

- [ ] **Step 2: Replace the title and opening copy**

Use this exact opening block:

```markdown
# TaskDock — Codex Usage & Quota Monitor for Windows

TaskDock is a lightweight Windows desktop monitor for Codex usage, quotas, tasks, and local token stats.

在 Windows 上查看 Codex 状态、5 小时/7 天额度、多任务进度和本地 Token 统计。

> TaskDock is an unofficial third-party tool and is not affiliated with or endorsed by OpenAI.
>
> TaskDock 是非官方第三方工具，不代表 OpenAI 的授权、认可或合作关系。
```

Keep the existing release download paragraph directly after this block, changing “Windows 11” wording to “Windows” wherever it appears.

- [ ] **Step 3: Make the feature list search-readable without adding unsupported claims**

Use these bullets, retaining only capabilities supported by the current app:

```markdown
- Codex 5-hour and 7-day quota status
- Multiple Codex task running states
- Current task name and local token statistics
- Tray menu, pinning, position lock, and startup launch
- Light and dark visual modes
```

Keep the existing Chinese feature explanation immediately below or beside the English bullets if the final README remains readable.

- [ ] **Step 4: Add the existing product visuals below the feature list**

Use the repository’s existing SVG assets so the first screen shows the actual product context without creating new artwork:

```markdown
![TaskDock status overview](assets/readme-hero.svg)

![TaskDock status strip](assets/readme-status-strip.svg)
```

Keep the visuals after the feature list and before the privacy section. Do not reference files outside `assets/`.

- [ ] **Step 5: Preserve privacy, support, and license sections**

Keep the existing privacy statement and links intact. Ensure the support section still states that sponsorship is voluntary and does not unlock features, and keep links to `LICENSE`, `THIRD_PARTY_NOTICES.md`, `USAGE.md`, and `SECURITY.md`.

- [ ] **Step 6: Verify the README content and links**

Run:

```powershell
rg -n "Codex Usage & Quota Monitor|lightweight Windows desktop monitor|unofficial third-party|5-hour|7-day|releases/latest|PRIVACY.md|USAGE.md|SECURITY.md|DONATE.md" README.md
git diff --check
```

Expected: every required phrase and both asset paths are found, and `git diff --check` produces no whitespace errors.

- [ ] **Step 7: Commit the README change**

```powershell
git add README.md
git commit -m "docs: improve TaskDock GitHub positioning"
```

### Task 2: Add the publish-ready promotion kit

**Files:**
- Create: `docs/promotion-kit.md`
- Reference: `docs/superpowers/specs/2026-07-15-taskdock-promotion-design.md`

**Interfaces:**
- Consumes: Approved platform copy, Xianyu listing, and first-week cadence from the promotion design.
- Produces: One copy source that can be pasted into Douyin, Xiaohongshu, Zhihu, and Xianyu without inventing new claims.

- [ ] **Step 1: Create the promotion kit sections**

Create `docs/promotion-kit.md` with these headings in order:

```markdown
# TaskDock Promotion Kit
## Core Positioning
## GitHub Metadata
## Douyin Comments
## Xiaohongshu Comments
## Zhihu Comments
## Xianyu ¥5 Listing
## First-Week Publishing Checklist
## Measurement Log
## Safety Boundaries
```

- [ ] **Step 2: Add the exact approved copy**

Copy the approved English description, Chinese positioning line, Topics list, three platform-specific comment variants, Xianyu title/description/main-image text, and the non-official service boundary from the design spec. Do not add claims about automatic alerts, official access, guaranteed quota, or network services unless the product documentation already supports them.

- [ ] **Step 3: Add an executable first-week checklist**

Use these checkboxes:

```markdown
- [ ] Day 1: update GitHub display title, description, README first screen, and Topics
- [ ] Day 1: verify release, privacy, security, and usage links
- [ ] Day 2: publish the Xianyu ¥5 installation/configuration listing
- [ ] Days 3–7: leave 5–10 relevant comments per day across the three platforms
- [ ] Daily: record GitHub visits/downloads, comment response, and Xianyu inquiries
- [ ] Day 7: keep the best-performing wording and record the baseline for week two
```

- [ ] **Step 4: Verify the kit contains no placeholders or risky wording**

Run:

```powershell
if (rg -n "TBD|TODO" docs/promotion-kit.md) { throw "Placeholder found" }
rg -n "官方授权|内部渠道|永久额度|账号出售|代充|破解|代理" docs/promotion-kit.md
git diff --check
```

Expected: the first command finds no placeholders. Any matches from the second command appear only inside explicit negative statements such as “不提供代充、破解或代理服务”; no positive sales claim is allowed. The term “非官方” is allowed and should remain in the safety section.

- [ ] **Step 5: Commit the promotion kit**

```powershell
git add docs/promotion-kit.md
git commit -m "docs: add TaskDock promotion kit"
```

### Task 3: Apply the remote GitHub description and Topics

**Files:**
- Remote metadata: `https://github.com/kc0577/TaskDock`
- Local reference: `docs/promotion-kit.md` (`## GitHub Metadata`)

**Interfaces:**
- Consumes: The exact title, description, and Topics from Tasks 1–2.
- Produces: GitHub repository metadata that matches the README without changing the repository name.

- [ ] **Step 1: Verify GitHub CLI authentication and repository identity**

Run:

```powershell
gh auth status
gh repo view kc0577/TaskDock --json name,description,url
```

Expected: the authenticated account can view `kc0577/TaskDock` and the repository URL is the expected public project.

- [ ] **Step 2: Update the repository description**

Run:

```powershell
gh repo edit kc0577/TaskDock --description "A lightweight Windows desktop monitor for Codex usage, quotas, tasks, and local token stats."
```

Expected: the command completes successfully and the returned repository metadata contains the new description.

- [ ] **Step 3: Add the approved Topics**

Run:

```powershell
gh repo edit kc0577/TaskDock `
  --add-topic codex `
  --add-topic windows `
  --add-topic desktop-app `
  --add-topic quota-monitor `
  --add-topic usage-monitor `
  --add-topic token-usage `
  --add-topic taskbar `
  --add-topic wpf `
  --add-topic csharp
```

Expected: the repository Topics include all nine approved terms; no unrelated or misleading topic is added.

- [ ] **Step 4: Re-read remote metadata**

Run:

```powershell
gh repo view kc0577/TaskDock --json name,description,repositoryTopics,url
```

Expected: name remains `TaskDock`, description matches the approved English sentence, and Topics match the approved list.

- [ ] **Step 5: Record a manual fallback if GitHub CLI authentication is unavailable**

If `gh auth status` fails, do not guess or edit unrelated settings. Open the repository’s GitHub **Settings → General** page and apply the exact description and Topics from `docs/promotion-kit.md`, then re-run the metadata read command when authenticated.

### Task 4: Run the final content and link verification

**Files:**
- Verify: `README.md`, `docs/promotion-kit.md`, `PRIVACY.md`, `USAGE.md`, `SECURITY.md`, `DONATE.md`

**Interfaces:**
- Consumes: Completed local documentation and remote metadata.
- Produces: Evidence that every approved promotion surface is consistent and links resolve locally.

- [ ] **Step 1: Check local links exist**

Run:

```powershell
@('PRIVACY.md','USAGE.md','SECURITY.md','DONATE.md','LICENSE','THIRD_PARTY_NOTICES.md') |
  ForEach-Object { if (-not (Test-Path $_)) { throw "Missing $_" } }
```

Expected: the command exits successfully without a missing-file error.

- [ ] **Step 2: Check consistency of the core positioning**

Run:

```powershell
rg -n "TaskDock.*Codex|Windows|Codex quota|Codex usage|unofficial|非官方|¥5|5 元" README.md docs/promotion-kit.md
```

Expected: the README and promotion kit use the same Windows/Codex positioning and consistently mark the tool as unofficial.

- [ ] **Step 3: Run repository whitespace and status checks**

```powershell
git diff --check
git status --short
git log -3 --oneline
```

Expected: no whitespace errors, only intended documentation changes are present, and the last commits correspond to the README and promotion kit work.

- [ ] **Step 4: Record completion evidence**

Save the final remote metadata output and the local verification results in the task handoff. Do not claim the promotion is live until the GitHub metadata and local docs both pass these checks.

## Self-Review Checklist

- Spec coverage: GitHub positioning, README structure, three platform comment sets, Xianyu ¥5 listing, first-week cadence, metrics, and safety boundaries are each covered by Tasks 1–4.
- Placeholder scan: no `TBD`, `TODO`, or vague implementation step is used.
- Type/format consistency: all paths, commands, topic names, and exact copy strings match the approved design spec.
