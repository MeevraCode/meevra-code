# Meevra Code

**An AI coding workspace for Windows that works with the AI accounts you already have, keeps your work on your computer, and checks what its agents say they did.**

Meevra Code is a desktop app. You open a project folder, describe what you want built, fixed or changed, and a team of AI agents does the work under your rules: a **Lead** plans and integrates, helper roles investigate, implement, review and test, and Meevra Code itself checks the result with real test runs before it calls anything done. You see every step, every approval and every token, and you decide how much paid usage is allowed.

This repository holds the **releases** of Meevra Code: the Windows installer, the End User License Agreement and the third-party notices. The source code is private. Bug reports, ideas and questions are very welcome here in [Issues](../../issues).

- Website: <https://meevra.si>
- Download: [Latest release](../../releases/latest)
- Contact: [founder@meevra.si](mailto:founder@meevra.si)

> **Status: Public Preview.** Meevra Code is free to use during the preview. Features can still change, and some parts of the app are marked "Coming soon". Please read [What the Public Preview includes](#what-the-public-preview-includes) before you start.

---

## Contents

- [Why Meevra Code exists](#why-meevra-code-exists)
- [Download and install](#download-and-install)
- [Your first task](#your-first-task)
- [Features](#features)
  - [Chat](#chat)
  - [Code tasks: a Lead and helper roles](#code-tasks-a-lead-and-helper-roles)
  - [Approvals, checkpoints and session branches](#approvals-checkpoints-and-session-branches)
  - [Proof, Test truth and the Claims checker](#proof-test-truth-and-the-claims-checker)
  - [The error catcher and the stuck detector](#the-error-catcher-and-the-stuck-detector)
  - [Mission Control](#mission-control)
  - [Flow](#flow)
  - [Projects](#projects)
  - [Brain](#brain)
  - [Vault](#vault)
  - [Agents and roles](#agents-and-roles)
  - [Providers](#providers)
  - [Quota and the live quota line](#quota-and-the-live-quota-line)
  - [Tools & MCP](#tools--mcp)
  - [Computer use](#computer-use)
  - [Terminal](#terminal)
  - [Activity](#activity)
  - [Settings](#settings)
- [How Meevra Code saves quota and money](#how-meevra-code-saves-quota-and-money)
- [What the Public Preview includes](#what-the-public-preview-includes)
- [Privacy and security in short](#privacy-and-security-in-short)
- [What's next](#whats-next)
- [Feedback and bug reports](#feedback-and-bug-reports)
- [Support the project](#support-the-project)
- [License](#license)

---

## Why Meevra Code exists

AI coding agents are powerful, but working with them day to day has three recurring problems:

1. **Usage disappears without warning.** An agent loop can burn through a plan's limit or an API budget in minutes, often while going in circles, and you only find out when the bill arrives or the limit is hit.
2. **"Done" is not always done.** Agents report that tests pass, that a bug is fixed, that nothing is left, and sometimes that is not true. Checking it yourself takes as long as doing the work.
3. **Your tools are scattered.** Different providers, different apps, different limits, and no single place that shows who is doing what, on which model, at what cost.

Meevra Code was built to answer those problems in one place:

- **It treats your quota and your money as yours.** Limits are shown as the provider reports them, paid usage happens only within a budget you set or after you confirm it, and a task pauses and asks instead of quietly switching to something that costs more.
- **It checks instead of trusting.** Meevra Code runs your tests and build itself, checks whether the agent's new tests actually test the change, and marks every claim the agent makes as verified, not verified or contradicted.
- **It keeps you in control.** Approvals, per-step rollback, a separate branch per session if you want one, and a full activity trail. Your projects, chats, settings and memory stay on your computer.

Meevra Code does not include access to any AI model. You connect your own provider accounts and API keys, or run models on your own computer. Meevra Code does not resell model access and adds nothing to what your provider charges.

---

## Download and install

### System requirements

- **Windows 10 or Windows 11, 64-bit (x64).**
- An internet connection for cloud AI providers and updates. Local models work without one.
- At least one AI connection: an API key from a supported provider, or a local model (see [Providers](#providers)).

### Install

1. Open the [latest release](../../releases/latest).
2. Download **`MeevraCode.exe`**.
3. Run it, read the license agreement, and choose **I Agree** to install.

**Windows SmartScreen.** The preview installer is not yet code-signed, so Windows may show *"Windows protected your PC"* and *"Unknown publisher"*. If you downloaded the installer from this repository's Releases page, choose **More info**, then **Run anyway**. Signed installers are on the [roadmap](#whats-next).

Each release also carries the **EULA** (`EULA-en.txt`) and the **third-party notices** (`THIRD-PARTY-NOTICES.txt`) as separate files, so you can read them before you install.

### Updates

You only need the installer once. An installed Meevra Code checks Meevra's update service for new versions, and **Settings › Updates** offers each one: it downloads when you choose **Update** and installs when you choose **Restart**. Every update package comes from a **signed update channel** and is verified before it is installed. Your projects, chats and settings are kept across updates.

Your installed version is shown in **Settings › Updates**. Please include it when you report a bug.

---

## Your first task

1. **Connect a provider.** Open **Providers** and add an API key (Anthropic, OpenAI, OpenRouter or Xiaomi MiMo), or set up a local model. Keys are stored encrypted on your computer.
2. **Open a project.** Choose a folder on your computer. A git repository works best (it unlocks session branches and the test checks), but any folder works.
3. **Describe the task.** In **Code**, write what you want built, fixed or changed, and press send. The Lead plans, works, and asks for approval where your approval level says it should.
4. **Review the result.** When the task ends you see the files that changed, the tests and build Meevra Code ran itself, and a check of every claim the agent made.

Use **Chat** for questions and discussion with no access to your files.

---

## Features

Everything below describes what Meevra Code does today. Where a part of the app is "Coming soon" in the Public Preview, it says so.

### Chat

A clean conversation with an AI model, **with no project access**: Chat cannot read or change your files or run commands. Use it to ask questions, think through a design, or get an explanation, without any risk to your work. You can add notes from your [Vault](#vault) as reference text.

### Code tasks: a Lead and helper roles

**Code** is where work happens. You describe the task once, and a small team of agents takes it on:

| Role | What it does | What it may do |
|---|---|---|
| **Lead** | Owns the task: plans, hands scoped work to helpers, integrates the results and decides the next step. | All task tools, within your approval level. Cannot be turned off. |
| **Investigator** | Read-only fact finding: traces code and architecture and reports findings with file references. | Read and search only. |
| **Implementer** | Makes scoped changes that follow the existing architecture and runs targeted checks. | Writes only inside the task's scope; concurrent writers use isolated worktrees. |
| **Reviewer** | Independent review of the result against the acceptance criteria and the evidence. A malformed verdict never counts as a pass. | Read only. |
| **Diagnostician** | Analyses repeated failures, finds the likely root cause and proposes the next experiment. | Read tools plus running tests. |
| **Tester** | Designs and runs verification, hunts for false passes and edge cases. | Read tools plus running tests. |

**Why it matters.** Each helper gets only what it needs (the objective, scope and criteria, never the Lead's whole conversation), and its permissions are fixed by its role: a prompt or a setting can never give a read-only reviewer the right to write. The Lead does not decide on its own that a task is complete: Meevra Code checks the evidence.

By default **every helper uses the same model as the Lead**, so nobody is opted into spending on several providers without choosing it. You can give each role its own model, reasoning effort and prompt on the [Agents](#agents-and-roles) page.

### Approvals, checkpoints and session branches

- **Approval levels.** *Every step* asks before anything that changes something (reads run freely). *Balanced* lets everyday development run without asking (reads, edits in the workspace, tests, builds, local commands) and still asks for network access, installs, screen control and changes outside the workspace. *Full access* runs every action without asking, but still asks before paid usage beyond your budget and still pauses a task that goes in circles.
- **Roll back any step.** Every step that changes files is saved as a checkpoint, labelled with what it did. You can rewind a session to any step. Checkpoints are stored locally, in Meevra Code's own data folder.
- **A branch per session (optional).** A Code session can work in its own git worktree on its own branch, so your checkout stays untouched while the agents work. When you are happy, the session's changes are merged into your branch (never forced, never pushed); a conflict is aborted and reported. You can also discard the session.

### Proof, Test truth and the Claims checker

These three checks are why "done" in Meevra Code means something. **None of them uses an AI model, so they cost no tokens** (unless you press *Fix it* to send a failure back to the Lead).

- **Proof it works.** Before a task may end as done, Meevra Code gathers evidence it observed itself: your project's tests with the real pass and fail counts, your typecheck or build script and its exit status, optionally the app started, checked and stopped, and the files that changed with their line counts. Each check shows the exact command it ran.
- **Test truth.** Agents often write a test that passes whether or not their change exists, so the test proves nothing. When a task changes both tests and source files, Meevra Code checks this itself: in a temporary copy of your project (never your working folder), it runs each new test with the change, then puts the source files back as they were before the task and runs the tests again. A test that still passes is marked **"Doesn't check the change"**; a test that now fails is marked **"Checks the change"**.
- **Claims checker.** When the agent finishes, it reports its results as structured claims: tests passed, build OK, files changed, bug fixed, nothing left. Meevra Code compares each claim with its own records of the task (the commands it ran with their exit codes, the files that really changed, the proof runs, the plan's open steps) and shows each one as **✓ verified**, **? not verified** or **✗ contradicted**, with the record that decided it.

### The error catcher and the stuck detector

- **Error catcher.** Meevra Code watches the processes it starts (Terminal commands, a task's commands and test runs, pages in its own browser) and catches their errors: stack traces, failing test runs, non-zero exits, page errors. Each becomes a card mapped to your project's files, with *Fix it* to send it to a Code session. You never have to copy an error into a chat by hand.
- **Stuck detector.** A task that goes in circles burns quota. Meevra Code notices it from structured signals (the same step repeated with the same result, the same failure after each fix, edits that undo earlier edits, rounds with no progress, tokens spent with nothing new happening) and pauses the task early with a plain explanation. You choose what happens next. It never judges what the model wrote.

### Mission Control

The overview page: **who works on what right now**, the latest activity, **what waits for you** (approvals and questions), and your projects. The command bar at the bottom ("Ask Meevra…") starts a new chat or a new Code task from anywhere.

### Flow

The whole workflow of every project at work, drawn live: each agent, its model and speed, where it works, the file it is working on and the tokens it uses. Useful when several tasks run at once and you want to see them side by side.

### Projects

The active project at a glance: its folder, its branch and the files that changed.

### Brain

**Brain** is what Meevra Code remembers about your projects and chats, **stored on your computer**. It learns from what actually happened, not from what a model said: a test command that really ran and passed becomes a verified fact about your project; a script that fails becomes a known issue; a finished task leaves a short record of what it did and whether its tests ran.

When an agent starts work, Meevra Code gives it a small, bounded capsule of the memory relevant to this task (only from this project, never another one), so agents do not rediscover the same facts on every task. Memory is passed to the model as reference data, never as instructions, and secrets are filtered out before anything is stored or sent. Brain makes no network calls of its own.

In the Public Preview, project memory is read-only and chat history is kept. **Agent memory** (what each agent remembers), the **Brain Explorer** (browse, search and edit everything) and **Memory savings** are *Coming soon*.

### Vault

Notes and reference text, **encrypted on your computer**, that you can add to a chat or a Code task: coding conventions, product notes, documentation, prompts. The Vault is used only when you add an item. It is not a password store: keys and credentials stay in Providers.

### Agents and roles

The **Agents** page is where you decide who does what, on which model:

- **Per role:** the model, the reasoning effort, the prompt, and whether the role is on.
- **How the model is chosen** (per role or per agent):
  - **Fixed** — always this exact model and connection. Meevra Code never changes it without you.
  - **Preferred** — your ordered list: the first model that can run and has not reached its limit. Same-or-cheaper switches happen on their own; costlier or paid ones are offered to you.
  - **Auto** — Meevra Code picks by the task, quota health and cost: plans and free routes first, paid only within your budget.
- **Own budget per agent:** each role or agent can follow the global paid-usage budget or have its own.
- **Review with a different model:** the Reviewer can check work on a different model than the one that wrote it. An automatic pick only uses models that cost nothing extra (plans, free or local routes), never a pay-as-you-go one.
- **Named agents** with their own prompt, model and budget.
- **Team presets:** save the bindings of every role and agent under a name, switch between them, and export or import them as JSON with no secrets inside.

### Providers

**Providers** is the one page for connecting AI services: add or remove API keys, connect local models, and see each connection's models and status. API keys are stored in Meevra Code's encrypted key store on your computer, are never shown again after you save them, and are never sent to Meevra.

See [What the Public Preview includes](#what-the-public-preview-includes) for the exact list of providers.

### Quota and the live quota line

**Quota** shows plan limits and usage **exactly as providers report them**. The rule is strict: an unknown value stays unknown (never shown as 0 or as an empty bar), a percentage is shown only when the provider reported it or reported exact numbers, and Meevra Code's own token counts are never presented as your remaining plan quota. A provider that reports no limits says so, with a link to where the provider shows them.

The Quota page also includes:

- **Paid-API budget** — *Always ask* (the default), a cap **per task, per day or per month** in USD, or *Never use a paid API*.
- **Local usage** — Meevra Code's own ledger of tokens per day and estimated costs, labelled as estimates, never as provider bills.
- **Forecast** — for windows a provider reports, the burn rate and when the limit would run out before its reset. With fewer than two readings it says there is not enough data instead of guessing.
- **Who uses it** — which agent used how much of a window.

The **quota line** is a thin line on the Code page, under the running task, that shows the limits of the provider at work **right now**. When Meevra Code switches connection mid-task, the line follows it. It shows only provider-reported numbers.

### Tools & MCP

- **Tools** lists the built-in tools agents can use and the rules that limit them (your approval level and permissions).
- **MCP** connects Model Context Protocol servers and tool packages, and can import servers you have configured in other apps.

### Computer use

Agents can see the screen and use the apps you allow. In the Public Preview, **Computer use is off until you turn it on**. Reading the screen needs the switch; controlling an app (focus, click, type) needs the switch and that app being on your allowed list. While a task uses the computer, the edges of the screen glow, and **Stop** works at any moment. Screen control still asks for approval under *Every step* and *Balanced*.

### Terminal

A terminal inside Meevra Code for running approved shell commands. Errors from commands run here are caught by the error catcher.

### Activity

The audit trail: Code tasks, approvals, tests, provider events. When you want to know what happened and why, it is here.

### Settings

**Settings** holds preferences, approval levels, permissions, updates, and **About** (the license agreement and the open-source licenses).

---

## How Meevra Code saves quota and money

This section lists the mechanisms that exist in the app. Each one is marked with what is available in the Public Preview.

**Available in the Public Preview**

1. **You pay your provider directly, with no markup.** Meevra Code does not resell model access. You use your own API keys or local models, and the provider's own prices apply.
2. **No silent pay-as-you-go.** Automatic model choice never moves work onto a usage-billed API on its own. A fallback to pay-as-you-go happens only if you turn on *Allow API fallback*. A model you chose yourself is always respected.
3. **A budget you set.** Paid usage is *Always ask* by default. You can set a cap per task, per day or per month, or forbid paid APIs entirely, globally or per agent. Spend is counted from the prices and costs providers report. A model whose price is not reported is never assumed to be inside your budget: Meevra Code asks.
4. **Pause instead of paying.** When a model reaches a limit its provider reported, or your budget for a paid run is used up, the task **pauses for quota** and shows its choices: continue on another connection, continue on a paid model (with a cost range from the reported price), **wait for the reset** (when the provider reported when it resets), or stop. The same task continues with a hand-off, so nothing is lost.
5. **Limits shown as the provider reports them.** The Quota page and the live quota line show provider-reported numbers only, so you see a limit coming instead of hitting it. (In the Public Preview this covers, for example, your OpenRouter credit balance; pay-as-you-go API keys have no plan limits, and your spend there is governed by your budget.)
6. **Helpers inherit the Lead's model.** Nobody is opted into spending on several providers without choosing it.
7. **The stuck detector.** A task going in circles pauses early, before it burns your quota, even under Full access.
8. **Free-tier guard.** When a free API key gets a real rate-limit reply, Meevra Code freezes that key instead of retrying blindly and burning it again.
9. **Project memory instead of rediscovery.** Brain gives agents a small, bounded capsule of what is already known about the project (working test command, known issues, what earlier tasks did), so they spend fewer turns finding the same things again.
10. **`read_output` instead of re-running commands.** Long command and test outputs are shortened in the agent's context, and the full text is saved. The agent reads the part it needs with `read_output`, instead of running a slow or expensive command again just to see more of its output.
11. **Context compaction without an extra API call.** When a conversation grows too long for the model, Meevra Code compacts older turns deterministically to fit the model's window, without paying for a summary call. Pinned task memory is kept every turn.
12. **Checks that cost no tokens.** Proof, Test truth and the Claims checker run without any model.
13. **Cross-model review on included models only.** An automatic switch to a different reviewer model never picks a pay-as-you-go route.
14. **Local models.** Run models on your own computer with the built-in engine, Ollama or LM Studio, at no per-token cost.
15. **Use the Grok Build plan you already have.** Sign in to Grok Build with xAI's own sign-in, and your tasks and chats run on that plan instead of a pay-as-you-go key. When the plan reaches its limit, the task pauses for quota; it never moves to paid usage on its own.

**Coming soon in the Public Preview** (already part of Meevra Code, not yet in this edition)

- **More AI plans you already pay for.** Sign-in for other subscription plans, so a coding plan you already have can do the work instead of a pay-as-you-go key.
- **Scout.** A small, quick helper model that reads files for your agents, so the Lead does not spend its own (larger) model's turns on reading.
- **Agent memory.** Each agent keeps what it learned about the project, so its next task does not start from zero.
- **Memory savings.** A view of how much memory saves on every model call.

---

## What the Public Preview includes

### Supported providers

| Connection | How you connect | Notes |
|---|---|---|
| **Anthropic API** | API key | Pay-as-you-go, billed by Anthropic. |
| **OpenAI API** | API key | Pay-as-you-go, billed by OpenAI. |
| **OpenRouter** | Sign in with OpenRouter, or paste an OpenRouter key | One account for models from many labs, billed to your OpenRouter credits. The Quota page shows your credit balance. |
| **Xiaomi MiMo API** | API key | Pay-as-you-go. |
| **Grok Build (xAI)** | *Install & connect* in Providers, then xAI's own sign-in | Uses the xAI plan that includes Grok Build. Meevra Code downloads its own copy of Grok Build; xAI's sign-in opens in your browser, Grok Build keeps the login, and Meevra Code never sees it. Grok Build's own tools stay off: every action goes through your approvals. The Quota page shows the plan usage Grok Build reports. |
| **Xiaomi MiMo Token Plan** | Token Plan key | Xiaomi allows Token Plan quota only in programming tools. Meevra Code uses it for your own coding tasks and chats, and when the plan runs out, never moves the work to pay-as-you-go on its own. Xiaomi shows the remaining credits on its own console. |
| **Built-in local engine** | A `.gguf` model file on your computer | Runs inside Meevra Code. No separate server needed. |
| **Local model servers** | Ollama, LM Studio, or any OpenAI-compatible server **running on your computer** | In the Public Preview, custom endpoints must be on this computer (localhost). |

When you have not picked a model yet, Meevra Code uses the first connected one in this order: Anthropic API, OpenAI API, OpenRouter, Xiaomi MiMo Token Plan, Xiaomi MiMo API, a signed-in Grok Build, the built-in engine, then a local server. Your own choice always replaces this default.

Provider names are used only to identify the services Meevra Code can connect to. Meevra is not affiliated with or endorsed by these providers. Your use of each provider is governed by your agreement with that provider.

### Coming soon

These parts of the app show a quiet **"Soon"** badge or a *Coming soon* card in the Public Preview:

- **Bots** — bots that tidy, summarise or digest your folders, with your approval.
- **TV & second screen** — show Meevra Code on a TV or a second screen.
- **Mobile** — follow and control Meevra Code from your phone.
- **More subscription sign-ins** — use other AI plans you already pay for, each with its own sign-in.
- **Scout** — a quick helper that reads files for your agents, so they save time.
- **Brain: Agent memory, Brain Explorer and Memory savings.**

As the license agreement says, showing a feature as "Coming soon" is not a promise that it will be released at a given time, or at all. We will be honest about what ships and when.

---

## Privacy and security in short

This is a summary. The full text is the **EULA**, attached to every release as `EULA-en.txt` and shown in the app under **Settings › About**.

- **No account.** Meevra Code does not require an account with us.
- **No telemetry unless you choose it.** Meevra Code sends us no usage analytics. You can choose to share **anonymous usage totals** once a day: how many tokens your models used (in and out, per hour and per kind of provider) and how many model turns ran in chats and in other work. Never your text, code, files, project names, keys or anything that identifies you. It is off until you turn it on, and you can turn it off at any time in Settings.
- **Your work stays on your computer.** Projects, chats, settings, Brain memory and the Vault are stored locally.
- **Your keys stay on your computer.** API keys are stored encrypted locally and are never sent to us.
- **Your content goes only where you send it.** When you use a provider, the prompts and files you choose go directly from your computer to that provider.
- **The update check is anonymous.** When Meevra Code checks for updates, it tells the update service only its version and edition, with no identifier, and marks the first automatic check of each day (and of each calendar month, UTC). We count only those marked checks, by hour (UTC), day, month, version and edition, with no IP address or other personal data stored with the count, and keep the counts for 13 months. The update service (Cloudflare, with update files possibly downloaded from GitHub) receives normal technical data such as your IP address, kept only in their service logs.
- **Logs stay local.** Diagnostic logs are shared only if you export them yourself and choose to send them to us.
- **Verified updates.** Every update is verified before it is installed.
- **Protected by default.** Approval levels, per-role permissions that a prompt cannot widen, Computer use off until you turn it on, and secrets filtered out of anything Meevra Code stores or shows.

Found a security issue? Please report it privately: see [SECURITY.md](SECURITY.md).

---

## What's next

These are **plans, not promises**. Priorities may change with your feedback.

- **Meevra Bots for everyone.** Supervised bots that look after your folders (tidy, summarise, digest), each with its own goal and memory, reviewed by a supervisor model and working with your approval.
- **TV & second screen leaves Experimental.** Extending or mirroring Meevra Code to a TV or a second screen, after it has been tested on real devices.
- **Meevra Mobile.** Pair your phone by scanning a QR code, follow your tasks live, and answer approvals on the go.
- **Meevra Link.** Several computers working together, so you can start a task on one and resume it on another.
- **Signed installers.** A code-signed installer, so Windows no longer shows "Unknown publisher".
- **More of what is "Coming soon"** in the app today, as each part is ready for everyone.
- **Optional paid plans, later.** Some advanced features or services may one day need a paid plan. The core of Meevra Code is meant to stay useful for free, nothing is ever charged without your explicit purchase, and the features of a version you have installed stay available to you under the terms you accepted.

---

## Feedback and bug reports

Your feedback shapes the preview. Please use [Issues](../../issues/new/choose):

- **Bug report** — something does not work as it should.
- **Feature request** — an idea or an improvement.

Please include your Meevra Code version (**Settings › Updates**), your Windows version, and the steps that lead to the problem. Do not paste API keys, passwords or private code into an issue.

---

## Support the project

Meevra Code is built by an independent founder. The source code is private, so contributing does not mean pull requests here. It means something just as valuable:

- **Use the preview and tell us what you think.** Every bug report and idea is read.
- **Test new versions** and report what breaks.
- **Sponsor the project** through **GitHub Sponsors** (the *Sponsor* button on this repository, once GitHub Sponsors is enabled for it). Sponsorship pays for development time, test hardware and the infrastructure behind updates.
- **Work with us.** For collaboration, partnerships, integrations or further development of Meevra Code, write to **[founder@meevra.si](mailto:founder@meevra.si)**. Every serious message gets a reply.

If Meevra Code saves you time or quota, telling another developer about it helps too. Thank you.

### Supporters

Sponsors who choose to be listed will be thanked here.

---

## License

Meevra Code is proprietary software, **free to use during the Public Preview** under the **Meevra Code End User License Agreement**. The EULA (`EULA-en.txt`) is attached to every release and shown in the app. Open-source components are listed with their licenses in `THIRD-PARTY-NOTICES.txt` and in **Settings › About › Licenses**.

Licensor: Dainius (Meevra), Lithuania. Contact: [founder@meevra.si](mailto:founder@meevra.si).

"Meevra" and "Meevra Code" are names used by the licensor. Other names are trademarks of their owners and are used only to identify their products and services.
