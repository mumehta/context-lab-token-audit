# Context Lab

Understand what is filling your AI context, identify avoidable work, and leave with a practical next action.

Context Lab combines an eight-question checklist, prioritized fixes, illustrative calculators, source citations, and an editable audit prompt. Investigate long conversations, large tool outputs, persistent instructions, MCP integrations, delegation, model choices, and recurring tasks.

**[Open the hosted site](https://context-lab-token-audit.cybersecuretech101.chatgpt.site/)** · [Run locally](#run-locally) · [Audit your setup](#two-ways-to-audit-your-setup) · [Self-hosting](#host-your-own-copy)

The website does not scan your computer or connect to AI accounts. It makes no model calls and needs no API key. Reports identify potential improvements; they do not guarantee dollar savings or predict subscription resets.

## Quick start

1. Open the hosted site or your local copy.
2. Choose **Your environment**: Claude Code, Codex, or ChatGPT.
3. In **Diagnose waste**, answer what you can verify; leave the rest **Unknown**.
4. Read **Your next steps**, starting with red findings. Use **Find a fix** and **Check the evidence** for explanations and product-specific boundaries.
5. Select **Download audit report** to save your Markdown checklist report.
6. For measured evidence, use **Build an audit prompt** in your own assistant, following the workflow below.
7. Make one targeted change and compare actual usage and quality on similar work.

Answers are separate for each environment during the current page session. Reloading or closing the page clears them. **Reset answers** clears the selected environment. Export before leaving: there is no saved audit history or account dashboard.

## Use the hosted site

Visit [Context Lab](https://context-lab-token-audit.cybersecuretech101.chatgpt.site/) without installing anything. Access depends on the owner's current sharing settings. A public GitHub repository does **not** automatically grant access to the hosted site.

If access is restricted, request a viewer invitation and sign in with the account that received it. Owners can use Sites **Share** controls to invite viewers or allow public access where available. See [official Sites sharing guidance](https://learn.chatgpt.com/docs/sites?surface=app#invite-people-outside-your-workspace).

Any hosting-platform sign-in consent is separate from the checklist. Signing in does not give this static application access to Claude accounts, ChatGPT chat history, Codex configuration, or billing records.

The app keeps answers in browser memory and sends no audit answers to an application backend. The hosting provider may process authentication information, access logs, and site analytics under its own policies. Browser-only answer handling does not mean the hosting service collects no information.

## Run locally

This is plain HTML, CSS, and JavaScript: no build step, package installation, database, or environment file. Use a modern browser with JavaScript enabled.

Download your GitHub repository as a ZIP and extract it, or clone it using its actual URL. Run the commands below from the project directory containing this README and `dist/`.

### Open the file directly

Open `dist/index.html` in your browser. Keep `styles.css` and `app.js` beside it. The checklist, explanations, and calculators work without a server.

Clipboard copying or downloads can be restricted under `file://`. If copying fails, the app selects the prompt for manual copying: Ctrl+C on Windows/Linux or Command+C on macOS. Use a local server if browser restrictions interfere.

### Serve it on your computer

With Python 3 installed, use the appropriate command:

Windows:

```powershell
py -3 -m http.server 8765 --bind 127.0.0.1 --directory dist
```

macOS/Linux:

```bash
python3 -m http.server 8765 --bind 127.0.0.1 --directory dist
```

Open **http://127.0.0.1:8765/**. Keep the terminal running; press Ctrl+C to stop. If that port is busy, choose another and update the browser address.

This is a local deployment for your own computer. The loopback address does not expose it to other devices. The core app works offline; source links and online assistant audits require connectivity. Python's development server is not intended for production internet hosting.

## Two ways to audit your setup

### Manual checklist: quick diagnosis

Answer the eight questions based on your workflow and settings. The app maps those answers to recommendations. It cannot verify loaded MCP tools, inspect tasks, count hidden tokens, or retrieve usage meters.

| Label | Meaning in the website report |
| --- | --- |
| RED | You reported a high-priority practice worth addressing first. |
| AMBER | You reported a plausible source of waste needing investigation. |
| GREEN | You reported a healthy practice; it is not independently verified. |
| UNKNOWN | Evidence is missing; this is not counted as healthy. |

Severity is editorial, not a measured cost ranking. A red finding is a starting point, not proof of a token leak.

### Audit prompt: gather evidence with your assistant

1. Select your environment and open **Build an audit prompt**.
2. Copy the generated prompt. Edit it to name your surface, model, and workflow.
3. Paste it into your own Claude Code, Codex, ChatGPT, or suitable assistant. Prefer a focused audit conversation.
4. Supply relevant settings and usage evidence. A coding agent may inspect files and run read-only diagnostics within its existing permissions; ordinary chat needs you to provide this information.
5. Review the assistant's findings and citations. Require measurements, estimates, and **UNKNOWN** data to be distinguished.
6. Save that evidence report separately and use it to update the manual checklist.

The prompt requests a bounded, read-only audit and no changes. It grants no new permissions and installs nothing. The website has **no built-in agent, MCP audit server, log importer, or assistant-report parser/upload**. Its exported checklist and the assistant's evidence report are separate outputs. The prompt uses stricter evidence requirements for its severity labels than the self-reported checklist.

Running the prompt consumes usage in the AI product you choose. Keep it small: relevant configuration and a bounded log sample, rather than every conversation or file. Never supply API keys, authentication cookies, secret environment values, or unredacted private logs. Evidence sent to an assistant is subject to that product's data handling even if this site runs locally.

## Choose the right environment

The selector currently has three choices. Claude chat and ChatGPT Work have no dedicated selector; adapt the closest prompt and remove unavailable controls.

| Your product | Choice and workflow |
| --- | --- |
| **Claude Code** | Select Claude Code. Record version, model, effort, provider/authentication, `/context`, and `/usage` where supported. Review relevant `CLAUDE.md`, MCP configuration, hooks, workers, and schedules. |
| **Claude web/desktop chat** | Use Claude Code for shared concepts, but edit the prompt before running it. Remove coding slash commands, hooks, local inspection, and gateway assumptions. Supply relevant conversation scope, attachments, project instructions, integrations, and visible limit messages. Keep hidden accounting unknown. |
| **ChatGPT ordinary chat** | Select ChatGPT. Provide custom/project instructions, memory settings, attachments, connected apps, tasks, and visible limit messages as relevant. Chat alone cannot inspect your local setup or reveal hidden token counts. |
| **ChatGPT Work / agentic workflows** | Select ChatGPT and name Work plus its execution environment in the prompt. Include tool activity, recurring work, delegation where available, and visible usage evidence. Inspect only legitimately accessible information; Claude Code commands do not transfer. |
| **Codex app, CLI, IDE, or cloud** | Select Codex and state the surface/authentication. Use CLI `/status` where supported or app usage settings. Review applicable `AGENTS.md`, skills/plugins, MCP controls, workers, and automations. Access differs by surface. |
| **Claude/OpenAI API applications** | Customize the closest prompt. Use actual request usage records and verified model rates. Deduplicate events and separate input, cache, output, and reasoning according to the provider schema. This site is not an API billing calculator. |

A coding agent audits only what its tools and permissions expose. API cache prices and TTLs do not establish Claude, ChatGPT, or Codex subscription accounting. Check [Claude Code cost guidance](https://code.claude.com/docs/en/costs) and [Codex usage guidance](https://help.openai.com/en/articles/11369540-using-codex-with-your-chatgpt-plan), alongside the site's source notebook.

## Turn the report into changes

Use the report as an improvement plan. Add evidence, your chosen action, and the result next to each finding. Keep reports locally or in a private document/issue; redact them before sharing.

| Suspected waste | First action | Validate afterward |
| --- | --- | --- |
| Unrelated work in one long conversation | Save a short handoff and start a new task/chat; use Claude Code `/clear` where appropriate. | Less irrelevant context without losing decisions. Already-used quota is not refunded. |
| Huge logs or repeated reads | Request targeted searches, bounded excerpts, and failure summaries; retain full logs in files. | Less input while failures and exit status remain visible. |
| Bloated instructions | Remove duplication and stale content; scope rules and move occasional workflows to on-demand resources. | Essential rules still apply with less irrelevant material. |
| Unused tools/MCP | Inspect effective loaded tools and deferral; disable irrelevant capabilities for that workflow. | Measured improvement without breaking required tools. Tool count alone is not a measurement. |
| Model/effort mismatch or retries | Match settings to difficulty and define success criteria. | Acceptable quality with lower usage or fewer retries. Switching models is not always a net loss. |
| Duplicate delegation | Give workers distinct bounded tasks, minimal context, and concise returns. | Combined parent-plus-worker usage and useful output. |
| Stale recurring work | Pause obsolete tasks; reduce unnecessary frequency/scope and define a stop condition. | Fewer actual model runs. Muting notifications alone does not stop work. |
| Cache assumptions | Inspect exposed read/write/new-input data and current provider behavior. | Actual reuse. Do not make extra calls merely to keep a cache warm. |

**Change one thing at a time.** Record product/version, model/effort, task, period, usage units, and output quality. Repeat comparable work with the same settings where possible. Compare several similar tasks if results vary; keep changes that reduce avoidable work without harming quality.

Keep context-window occupancy, cumulative tokens, subscription allowance, and API dollars separate. Necessary tool calls, cached input, and useful tasks are not waste simply because they consume tokens. No savings percentage or quota reset prediction is guaranteed.

## Calculator boundaries

**Explore the math** models repeated input exposure:

```text
Total = N × B + G × N × (N − 1) / 2
Avoided = N × removable starting tokens
```

`N` is model requests, `B` starting context, and `G` newly retained context per request. One user message can trigger many requests. This excludes compaction, eviction, truncation, cache discounts, output billing, and context-window ceilings; it is not a real bill.

Recurring-work calculations assume a first run at minute zero, constant input per run, and later runs strictly before the period ends. Missed runs, output, and extra workers are excluded. Use scenarios to understand repetition, then verify against actual usage.

## Host your own copy

Serve the **contents of `dist/`** as your web root on a static host. Keep all three files together. No build command, credentials, model service, or server application is required. Navigation uses fragments such as `#prompt`, so no server-side route rewriting is needed.

In a hosting dashboard, select no framework/no build step where available and use `dist` as the publish/output directory. For folder uploads, upload its contents. For an existing web server, place them in its document root. Use HTTPS for shared internet hosting and configure private access separately: this app includes no self-hosted sign-in or access controls.

### GitHub Pages example

For branch-based Pages publishing, copy the three `dist/` files into a repository `docs/` directory and commit them. Keep this README at the repository root. In **Settings → Pages**, select **Deploy from a branch**, your publishing branch, and `/docs`, then save. Use the deployment URL GitHub reports. Update the `docs/` copy whenever the app changes.

Alternatively, create a Pages Actions workflow that uploads `dist/` as the artifact. No such workflow is included. Availability/access depend on repository and account settings; follow [GitHub's publishing-source documentation](https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site).

`.openai/hosting.json` links the original project to its existing Sites deployment. Other hosts and local use do not need it. For your own Sites deployment, provision a new project identity rather than reuse the original `project_id`; follow the [Sites workflow](https://learn.chatgpt.com/docs/sites?surface=app). These instructions do not change the original deployment or its sharing settings.

## Hosted, local, or self-hosted?

| Option | Benefits | Tradeoffs |
| --- | --- | --- |
| Existing hosted site | Immediate access when shared; no installation; owner maintains a shared version. | Depends on owner access settings, availability, and updates. Platform sign-in/logging may apply; you do not control deployment. |
| Local copy | No hosting account; core app works offline; control the files you run. | Update it yourself. Source links and assistant audits need their services. File sharing is less convenient than a URL. |
| Your hosted copy | Control audience, domain, content, version, and hosting policy; share your own URL. | Maintain updates, hosting, and access controls. Costs/logs may apply; documentation in a fork can become stale. |

All options use the same browser-only checklist. Self-hosting adds no automatic scanner, better measurements, persistence, or agent integration. Opening the app makes no LLM requests; running its prompt separately can consume plan usage or API spend.

## Files, maintenance, and publishing

```text
README.md               User guide
dist/index.html         Application structure
dist/styles.css         Responsive styling
dist/app.js             Checklist, calculators, recommendations, citations, prompts, export
PRODUCT.md              Product intent
DESIGN.md               Design decisions
.openai/hosting.json     Original Sites linkage
```

Edit `dist/app.js` to change questions, advice, sources, or prompts. Verify current documentation before changing claims. Check environment switching, unknown answers, report export, copying, calculator boundaries, and mobile layout after changes. Update privacy guidance if adding persistence or account access.

Research snapshot: **7 October 2026**. **Check the evidence** contains claim-level citations and comparisons. Research began with [Sharbel A.'s video and description prompt](https://www.youtube.com/watch?v=kHtOSJRUkLs); official documentation qualifies or corrects several rules of thumb. Commands, features, plan limits, and provider behavior can change.

Publish the intended project files, not private reports, login screenshots, credentials, or scratch research. This package has no explicit software license; the repository owner should choose one before presenting it as licensed open-source software.

## Troubleshooting

- **Hosted access denied:** request a viewer invitation or run locally. Cloning GitHub does not grant hosted access.
- **Google login errors:** retry with the invited account. Persistent authentication issues belong to the hosting/login service; see [OpenAI login troubleshooting](https://help.openai.com/en/articles/7426629-why-cant-i-log-in-to-chatgpt).
- **Blank/unstyled page:** enable JavaScript and keep all three app files together; verify the serving directory.
- **Copy/download fails:** manually copy the selected prompt or use localhost; check browser permissions.
- **Answers disappeared:** reload clears browser memory. Export before leaving.
- **Assistant claims exact hidden costs:** ask for its source and measurement; keep unavailable data unknown.
- **Unanswered items are not green:** unknown is deliberate. Answer only what you can verify.

## Research resources

The application presents documentation-based guidance. Video attribution is kept here rather than in the application pages. The research input was [Sharbel A.’s video and description audit prompt](https://www.youtube.com/watch?v=kHtOSJRUkLs). The following official resources informed the mechanisms, comparisons, and fixes:

- [Anthropic · How Claude Code works](https://code.claude.com/docs/en/how-claude-code-works) — Context, compaction, tools and session boundaries.
- [Anthropic · Manage costs effectively](https://code.claude.com/docs/en/costs) — Usage diagnostics, preprocessing and model selection.
- [Anthropic · Claude Code prompt caching](https://code.claude.com/docs/en/prompt-caching) — Version-sensitive cache behavior and request-specific TTLs.
- [Anthropic · API prompt caching](https://platform.claude.com/docs/en/build-with-claude/prompt-caching) — Cache accounting and model-dependent rates.
- [Anthropic · MCP tools & tool search](https://code.claude.com/docs/en/mcp) — Deferral, gateway fallback and output limits.
- [Anthropic · Subagents](https://code.claude.com/docs/en/sub-agents) — Separate requests and context isolation.
- [Anthropic · Scheduled prompts](https://code.claude.com/docs/en/scheduled-tasks) — Session loops differ from cloud and desktop schedules.
- [OpenAI · MCP configuration](https://learn.chatgpt.com/docs/extend/mcp?surface=cli) — Server enablement and tool allow/deny lists.
- [OpenAI · Subagents](https://learn.chatgpt.com/docs/agent-configuration/subagents) — Codex delegation controls and context management.
- [OpenAI · AGENTS.md](https://learn.chatgpt.com/docs/agent-configuration/agents-md) — Instruction discovery and scope.
- [OpenAI · Codex with your ChatGPT plan](https://help.openai.com/en/articles/11369540-using-codex-with-your-chatgpt-plan) — Usage factors, shared allowances and diagnostics.
- [OpenAI · API prompt caching](https://developers.openai.com/api/docs/guides/prompt-caching) — Reusable prefixes; API rates do not establish subscription quotas.
- [OpenAI · Conversation state](https://developers.openai.com/api/docs/guides/conversation-state) — Context windows and billing for API continuation.
- [OpenAI · Scheduled tasks](https://learn.chatgpt.com/docs/automations?surface=app) — Standalone and in-chat schedules; environment requirements.
- [OpenAI · ChatGPT memory](https://help.openai.com/en/articles/8590148-memory-in-chatgpt) — New chats and personalization controls.
- [Anthropic · PDF support](https://platform.claude.com/docs/en/build-with-claude/pdf-support) — PDF text and visual processing.
- [OpenAI · File inputs](https://developers.openai.com/api/docs/guides/file-inputs) — PDF text and page images in API inputs.
