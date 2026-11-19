# Changelog

Meevra Code release notes. Every release is on the [Releases](https://github.com/MeevraCode/meevra-code/releases) page, with its installer, its license agreement and its third-party notices.

## 2.44.1 — Public Preview

A small release for the license agreement. An installed 2.44.0 takes it as a small update (about 0.5 MB).

### License agreement
- **Version 1.6 names the browser pane** in the list of internet connections of its Privacy section: the websites you open in the pane, the pages an agent opens there when you ask it to, that the pane's sign-ins, cookies and site data stay on your computer, and that an agent working there is signed in where you signed in. Meevra Code shows the agreement once more at the next start and asks you to accept it.

### Quota
- **What the API would charge** uses the public list prices of 19 November 2026, for 217 models.

## 2.44.0 — Public Preview

A terminal and a browser beside your work, an agent that can use that browser, and thirteen built-in skills. An installed 2.42.3 takes it as a small update (about 3 MB).

### Side panes
- **A terminal or a browser beside your work.** Two buttons in the title bar open a pane next to the page you are on: Terminal (Ctrl+`) and Browser (Ctrl+Shift+B).
- **The browser pane** has tabs, an address bar that also searches, back, forward and reload. Its session stays on your computer, so a site you sign in to there stays signed in. "Forget sign-ins and site data" clears it.
- **Keep computer awake.** A switch in the title bar's More menu keeps the computer from sleeping while a long task runs, until you turn it off or close the app.

### Agents
- **The agent can work in the browser pane.** Ask for it in a Code task. The agent gets its own Agent tab beside your tabs and opens pages, clicks, types, reads and takes screenshots there. It works in the pane's session, so it is signed in where you signed in, and its approval request says so.

### Skills
- **Thirteen built-in skills** ship with Meevra Code and are on from the first start: video prompting, video editing with ffmpeg, Remotion, image generation, image editing, image upscaling, text in images, logo design in SVG, SVG quality, website design, model comparison, and two that choose the right image or video tool. The agent reads a skill only when the task needs it. Each can be turned off in Marketplace > Skills.

### Quota
- **What the API would charge** uses the public list prices of 19 November 2026, for 217 models.

## 2.42.3 — Public Preview

A small release for Chat. An installed 2.42.2 takes it as a small update (about 2 MB).

### Chat
- **A new Chat never starts on a model you removed.** When you disconnect a connection in Providers, a new Chat no longer opens on a model of that connection. It uses the same model as Code until you choose one. Before this release a new Chat kept the removed model, and nothing could be sent from it.
- A Chat you already used keeps its model: its history stays as it was, and the model is shown as not available until you choose another one.

### Quota
- **What the API would charge** uses the public list prices of 18 November 2026, for 216 models.

## 2.42.2 — Public Preview

A small release that makes the start of the app safer. An installed 2.42.1 takes it as a small update (about 2 MB).

### Start
- **A window that stays blank at start recovers by itself.** If the app's page has not arrived 20 seconds after start, Meevra Code loads it again. If it still has not arrived, Meevra Code makes the window again once, and after that shows the window as it is. Each of these steps is written to the app's log.
- A page that fails to load is written to the log in the installed app too, with the error's code and description.
- Closing a window that Meevra Code had to recover ends the app as usual.

### Quota
- **What the API would charge** uses the public list prices of 17 November 2026, for 216 models.

## 2.42.1 — Public Preview

Reply comes to the public release, with fixes to how a task's changes and its Flow are shown. An installed 2.41.0 takes it as a small update (about 3 MB).

### Reply: answer any message of a thread
- Every message of a thread offers **Reply**, as in a chat app: an answer of the agent, a line it wrote during a task, a notice of Meevra Code itself, a Chat answer that failed. It works with every model, in Code and in Chat.
- Select a part of a message first and only that part is quoted. The quote shows over the prompt until you send or cancel it.
- A reply sent **while a task is running** reaches the running task: the agent gets your words with the quote at its next step, and nothing is restarted.
- The agent's message that answers your reply is marked **Answer to your reply**, with the words you quoted, so it is easy to tell apart from the rest of the task.
- Pressing the quote in a message you sent goes to the message it quotes and lights it. If that message is not on screen, Meevra Code says so.
- The quote reaches the model as quoted text, after your own words: it is never read as an instruction of yours.

### Tasks
- **Files a command wrote are counted.** A file written by a program the task ran (a shell command, a script) is listed with the run that wrote it and counted in the task's changes, in a Git repository and in a folder with no Git.
- In a folder with no Git a task starts at once: no Git process is started that can only answer "not a repository".
- **Task started on** names the model the task's Lead runs on.

### Flow
- A step a stopped task never ran reads **not run**, one that was stopped in the middle reads **stopped**, one you denied reads **denied**. None of them reads "done".
- A task that waits for your answer reads **waiting for you**, not "running".
- An approval that ended with no answer from you (the task was stopped, or the request ran out) reads **not answered** and is not counted as decided.

### Known limits
- Outside a Git repository a task that ran a program ends as **Needs a look**, not Done: without a repository Meevra Code cannot prove what the program changed.
- Sessions made before this version show no **Answer to your reply** mark on their old messages.

## 2.41.0 — Public Preview

The first public release since 2.38.10. It brings everything built in between: six new features, a much faster and cheaper Computer use, and coding tasks that take fewer turns.

### Delivery: from a finished task to a pull request
- A new **Delivery** row under a Code session's task takes the session's change from your computer to a pull request. Meevra Code does it itself; no model is used.
- **Deliver** shows what would be pushed (only the files this session's tasks changed, never other changes in the folder), to which branch and into which branch. Meevra Code asks you to confirm in its own window before anything leaves your computer. Nothing is forced and nothing is merged.
- On GitHub it opens the pull request (the request, the changed files, the test run and the proof are written into it) and then reads the pull request's checks: running, passed, or failed with the failed checks named.
- When a check fails, **Ask the agent to fix it** sends the failed checks, as GitHub reported them, to the session's agent; **Push the fix** then updates the same pull request.
- On other Git services Meevra Code pushes the branch and gives you the link to the page that opens the pull request.
- It uses the sign-in Git already has on your computer. The sign-in is kept in memory only and is sent only to GitHub.
- A push follows nothing the project's own Git settings name (a program, another address, a proxy). In such a project Meevra Code does not push and says why; push from your terminal.

### Quota: where it went
- A new **Where it went** tab on the Quota page: every model turn is recorded, and you see the tokens by model, reasoning effort, who used them (Lead, helpers, summaries), task and day.
- **What the API would charge** for the same tokens, at the public list price, next to your plan's monthly fee.
- A usage line under each task: its turns and tokens, with a link to the tab.

### Proof strength
- After a task's tests pass, Meevra Code checks by itself whether those tests would notice a small mistake in the change: in a temporary copy of your project it makes one small break at a time in the changed lines and runs the tests that reach them.
- The Proof card shows which breaks the tests noticed, which they did not, and which changed files no test reaches. **Ask the agent to cover these** sends them back.
- No model is used; it costs processor time only. On by default: **Settings › Agents › Proof before Done › Check proof strength**.

### Reflexes
- When a finished task was a set of commands that all ended well, Meevra Code offers **Save as a reflex**. The next time, it runs the recorded steps itself: no model and no plan quota.
- If a step ends differently than recorded, the model takes over from there.

### Promise
- A running task shows a promise: the number of turns and the time tasks like it usually finish within, taken from your own record of finished tasks with the same model. No model is asked.
- A task that reaches twice its promise is held and asks you: resume, change the model, or cancel. At the end it says whether the promise was kept.

### Night shift
- **Queue for the night shift** in the Code composer's **+** menu puts a task in a queue. In the hours you set (23:00 to 07:00 by default) Meevra Code runs the queued tasks one at a time.
- It runs only on a plan, a free route or a local model, never on a route that costs money, and it spends only the plan quota that would otherwise be lost before the reset.
- It does not start while you are working in Code. A card on the New task page shows the queue, why a task waits and how each one ended.

### Computer use
- The window of the task comes to the front whatever is open, Meevra Code steps aside while it works, and you see the pointer move.
- Much faster: looks and actions run in one helper process, and the model sends several steps in one turn; Meevra Code holds the rest when a step does not go as predicted.
- On our measured task it used about 59 percent fewer tokens.
- The glow stays on for the whole task, and work inside one window is no longer paused as going in circles.

### Fewer turns, fewer tokens
- A coding task takes fewer turns and uses a lower reasoning effort after finished work. On our two measured coding tasks that was about 43 percent and about 24 percent fewer tokens, with every test passed.
- On a Claude plan the tool list is written compactly and the long entries of rarely used tools come on request: about 8 percent fewer tokens on a coding task.

### Fixes
- **Full access** asks nothing, with every model, and the level you chose stays after a restart.
- A custom OpenAI-compatible provider now receives every tool's parameters.
- A task is no longer paused as going in circles when something new happened after its repeated step, and is no longer blocked by a step that was never attempted.
- The rows at the bottom of Code no longer run into each other.

Good to know: an installed 2.38.10 takes this as a small update (about 3 MB). Older versions download the full installer (about 510 MB).

## 2.38.10 — Public Preview

Five fixes found while testing 2.38.9 with real Claude, ChatGPT and Grok plans.

- A task that ended with an answer and took no step now reads **Answered**, not Done, and says so: nothing was read, changed or run.
- A task sent in the first seconds after the app starts waits for the first provider check (up to 20 seconds) instead of stopping.
- When a model answers in a form Meevra Code cannot read, the model is told what was wrong. After three such answers in a row the task stops and says why, instead of going on.
- A task that has not edited a file yet says "No file edits yet".
- Providers: the number of models on a plan's card now matches the list under "Your models".

Good to know: this update downloads the full installer (about 510 MB).

## 2.38.9 — Public Preview

The first public release since 2.25.2. Most of what earlier previews marked "Coming soon" is now part of the app.

### Use the AI plans you already pay for
- **Claude (Pro or Max).** Claude Code ships inside Meevra Code, unmodified. You sign in on Anthropic's own page, Claude Code keeps the login, and Meevra Code never sees it.
- **ChatGPT.** OpenAI's own sign-in opens in your browser; Meevra Code never sees your password.
- **Coding plans through Claude Code:** Z.ai GLM Coding Plan, MiniMax M Plan, BytePlus ModelArk Coding Plan and StepFun Step Plan. You paste the plan's own key.
- One account per provider in the preview. The Quota page shows each plan's limits exactly as the provider reports them.

### Now included
- **Bots**, **Race** (one task on several models: compare what each did and keep the best), **Scout** (a quick read-only helper for your agents), **Mobile**, **TV & second screen** and the advanced **Brain** pages.

### Tasks
- A task that reaches a plan's limit waits for the reset and then goes on. It never moves to paid usage on its own.
- A task waits out a lost internet connection and continues by itself.
- A task ends as done only when nothing is left to do; a result Meevra Code could not check reads "Needs a look", not "Done".

### Smaller downloads
- The installer is about 510 MB (it was 612 MB).
- From this version on, an update can download only the files that changed instead of the whole installer.
- Your settings, chats and connections are carried over on the first start after the update.

### Good to know
- Meevra Code now opens on Code.
- The license agreement is still version 1.5.
- The installer is still not code-signed, so Windows SmartScreen may ask before it runs.

## 2.25.2 — Public Preview

- Pictures you attach to a Code task now reach models that can see images (OpenAI, Anthropic and Google API keys; such models show the **Vision** mark). A model that cannot see images says so plainly.
- Chat can search the web and read a page when you use an API key, a custom endpoint or OpenRouter. It never does this while the chat holds Brain memory, attached files or Vault notes, and an address that the search did not find and you did not give is always asked first.
- GitHub search covers repositories, issues and users. Code search needs a GitHub sign-in, so it is no longer offered.
- Removed: the photo-to-Excel tool. Meevra Code is a coding app, and it keeps to that.

## 2.25.1 — Public Preview

- OpenAI API keys work with GPT-5 and the o-series models.
- Local models run at the context you chose in the Library (16K by default) instead of a fixed 4K, and Meevra says plainly when a model is too small for a Code task.
- Artifacts (a page, diagram or document an agent makes) are saved as files in your project's artifacts/ folder, never over an existing file.
- The Computer use Stop button works in the public edition.
- With Brain on, a long task's history is never folded to make room for Brain's own notes.
- The license agreement is version 1.5: it names the web connections (the search service, GitHub search and the pages an agent reads). You are asked to accept it once after the update.

## 2.25.0 — Public Preview

### Web search that just works
- Agents can search the web with no setup: free DuckDuckGo search is on by default, and Grok Build, Claude and ChatGPT plans can also use their own search (counted in your plan). Meevra shows what was searched.
- Optional: your own Tavily, Brave or Exa key in **Settings › Web search**.
- New: agents can read a single web page without opening a browser. An address the task did not find and you did not give asks first.

### Browser and errors
- The hidden browser is now called **Use the browser**, never "computer use", and shows no screen glow. Redirects, time limits and errors are reported in plain words; pages on your local network stay closed to it.
- **Caught errors** folds into a list with **Ignore all**, and errors from other websites are no longer caught.

## 2.24.0 — Public Preview

### Usage totals, only if you choose
- A new choice, asked once: **Share anonymous usage totals**. Once a day, Meevra Code sends how many tokens your models used (in and out, per hour and per kind of provider) and how many model turns ran in chats and in other work. Never your text, code, files, project names, keys or anything that identifies you.
- **Off by default.** Turn it on or off at any time in Settings.
- The anonymous update check also marks the first automatic check of each calendar month (UTC), so we can count how many copies are in use each month, still with no identifier. Counts and shared totals are kept for 13 months, then deleted.
- The license agreement is now version 1.4: its Privacy section describes exactly this. You are asked to accept it once after the update.

## 2.23.1 — Public Preview

The first public release of Meevra Code for Windows 10 and 11 (x64). Free to use during the preview. It includes everything listed under 2.23.0 below, plus the fixes from a full review before launch:

### New in the Public Preview
- **Grok Build plan sign-in**: Install & connect in Providers, then xAI's own sign-in. Your tasks and chats can run on the Grok Build plan you already have.

### Safer by default
- Every request from the app's window is checked against the exact fields it may carry; anything else is refused.
- Starting a plugin's program, raising or removing a budget cap, resetting usage, and continuing a task on a paid model each ask you first, in Meevra Code's own dialog.
- Text written by models, web pages, files and programs is always passed to agents as fenced data, never as instructions.

### More reliable
- A crashed background service no longer restarts the whole app; programs Meevra Code started are stopped when it closes or crashes.
- Heavy work (installing tools, checking update signatures) no longer freezes the window.
- "Wait for reset" survives a restart.
- A model whose price is not known is shown as "Not known", never with an invented price; budget messages say "estimated".
- Uninstall says plainly what it removes and what it keeps.
- A screen region that fails shows a plain message instead of a blank window.

### More honest results
- "Tests passed" counts as verified only when Meevra Code saw the test run itself, with the runner's own counts.
- Task steps run only in their own project folder; undo stops before it would overwrite a file it could not back up.

## 2.23.0 — Public Preview (not published)

The feature set the Public Preview is built on. It was not published on its own.

### Work
- **Chat**: conversations with AI, with no access to your files.
- **Code tasks** with a **Lead** and helper roles (Investigator, Implementer, Reviewer, Diagnostician, Tester). Helpers use the Lead's model unless you choose otherwise.
- **Approval levels** (Every step, Balanced, Full access), **rollback of any step**, and an optional **git branch per session**.
- **Proof it works**: Meevra Code runs your tests and build itself before a task counts as done.
- **Test truth**: checks whether the agent's new tests actually fail without its change.
- **Claims checker**: every result the agent reports is shown as verified, not verified or contradicted.
- **Error catcher** with *Fix it*, and a **stuck detector** that pauses a task going in circles.
- **Brain**: project memory and chat history, stored on your computer.
- **Vault**: notes and reference text, encrypted on your computer.

### Overview
- **Mission Control**: who works on what, what waits for you, and your projects.
- **Flow**: the live workflow of every project: agents, models, files and tokens.
- **Activity**: the full audit trail.

### Models, quota and cost
- **Providers**: Anthropic API, OpenAI API, OpenRouter, Xiaomi MiMo (API and Token Plan), a built-in local engine for `.gguf` models, and local servers such as Ollama and LM Studio.
- **Agents**: per-role models, Fixed, Preferred and Auto model choice, named agents, team presets, and review with a different model.
- **Quota**: limits exactly as providers report them, local usage, forecasts, and a **quota line** under the running Code task.
- **Paid-API budget**: Always ask by default, or a cap per task, day or month, or never use a paid API. No silent pay-as-you-go.
- **Pause for quota**: a task that reaches a limit pauses and lets you choose how to continue.

### Tools
- **Tools & MCP**: built-in tools with their rules, MCP servers and tool packages.
- **Computer use**: agents can see the screen and use the apps you allow (off until you turn it on).
- **Terminal** for approved shell commands.

### Updates and privacy
- Updates from a signed update channel, offered in **Settings › Updates**.
- No account, and no telemetry unless you choose to share anonymous usage totals. An anonymous update check at most once a day.

### Coming soon
Bots, TV & second screen, Mobile, more subscription sign-ins, Scout, and Brain's Agent memory, Brain Explorer and Memory savings.
