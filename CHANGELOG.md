# Changelog

Meevra Code release notes. Every release is on the [Releases](https://github.com/MeevraCode/meevra-code/releases) page, with its installer, its license agreement and its third-party notices.

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
- No account and no telemetry. An anonymous update check at most once a day.

### Coming soon
Bots, TV & second screen, Mobile, more subscription sign-ins, Scout, and Brain's Agent memory, Brain Explorer and Memory savings.
