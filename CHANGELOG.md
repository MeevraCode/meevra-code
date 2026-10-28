# Changelog

Meevra Code release notes. Every release is on the [Releases](https://github.com/MeevraCode/meevra-code/releases) page, with its installer, its license agreement and its third-party notices.

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
