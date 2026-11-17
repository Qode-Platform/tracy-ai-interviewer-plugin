# Tracy AI Interviewer

Run AI video or audio interviews from Claude, ChatGPT, Codex, Gemini, Cursor and Mistral. This repository bundles the Tracy AI Interviewer connector (`https://tracyinterview.ai/mcp`) with four skills to draft interviews, try a practice run, invite people, and read what they said. Tracy AI Interviewer reports answers; it does not score, rank, reject, or decide for you.

Every app below uses the same server address and the same four skill folders under `skills/`. Only the manifest each app reads differs. Jump to [Other AI apps](#other-ai-apps) for ChatGPT, Codex, Gemini, Cursor and Mistral.

| Skill | What it does |
| --- | --- |
| `tracy-suggest-interview` | Draft an interview from who you want to interview and what you want to learn. |
| `tracy-practice-run` | Try your own interview before inviting participants. |
| `tracy-invite-people` | Preview invitations to addresses you supply, or manage the public link. |
| `tracy-read-results` | Read participants' answers and completion states. |

## Install in Claude chat and Cowork

1. Open **Customize > Plugins** in Claude on the web or in the desktop app.
2. Choose **Add > Add marketplace** and enter `https://github.com/Qode-Platform/tracy-ai-interviewer-plugin`.
3. Install **Tracy AI Interviewer** from that marketplace.
4. Open the plugin's **Connectors** tab, connect **Tracy AI Interviewer**, and sign in when prompted. On Team and Enterprise plans, an organization Owner may need to add the connector first.
5. Start a new chat or Cowork task. Ask, for example: “Help me draft a customer research interview about onboarding.” Use the skill picker or slash menu where available; Claude can also apply the skills from your request.

The repository is currently private, so GitHub access is required. A public directory listing is not live yet. Once the owner publishes the plugin to Anthropic's directory, you can find and install **Tracy AI Interviewer** from **Customize > Plugins** directly. Installing only the existing connector does not install these skills.

## Install in Claude Code

Run these commands in a Claude Code session:

```text
/plugin marketplace add Qode-Platform/tracy-ai-interviewer-plugin
/plugin install tracy-ai-interviewer@tracy-ai-interviewer-plugins
```

Start a new session, use `/mcp` to connect and authenticate if prompted, then type `/tracy-ai-interviewer:` to see the four skills:

```text
/tracy-ai-interviewer:tracy-suggest-interview
/tracy-ai-interviewer:tracy-practice-run
/tracy-ai-interviewer:tracy-invite-people
/tracy-ai-interviewer:tracy-read-results
```

To refresh an existing marketplace, run `/plugin marketplace update tracy-ai-interviewer-plugins`.

## Other AI apps

Each app reads its own manifest from the repository root, next to the Claude files:

| File | Read by |
| --- | --- |
| `plugin.json` + `mcp.json` | [Agent Plugins](https://agent-plugins.org) standard: ChatGPT and Codex, Cursor, Mistral Vibe Code |
| `.agents/plugins/marketplace.json` | Codex and the ChatGPT desktop app (repo marketplace) |
| `.cursor-plugin/plugin.json` + `.cursor-plugin/marketplace.json` | Cursor |
| `gemini-extension.json` | Gemini CLI |
| `.claude-plugin/` + `.mcp.json` | Claude (unchanged) |

Every app signs in to Tracy AI Interviewer with OAuth the first time a tool is used; no keys are stored in this repository. While the repository is private, installing from GitHub needs read access to it. Formats were checked against each vendor's documentation on 2026-11-17.

### ChatGPT and Codex

Status: package added. Tested with Codex CLI 0.163.0 (marketplace add, plugin install, MCP server registered). Not yet tested in the ChatGPT app.

In Codex (CLI, or Codex in the ChatGPT desktop app):

```sh
codex plugin marketplace add Qode-Platform/tracy-ai-interviewer-plugin
codex plugin add tracy-ai-interviewer@tracy-ai-interviewer-plugins
codex mcp login tracy-ai-interviewer
```

Or open `/plugins` inside Codex and install **Tracy AI Interviewer**. Start a new session afterwards. In the ChatGPT desktop app, add the same marketplace, restart the app and install from the Plugins directory. A ChatGPT workspace admin can also import the repository under **Admin > Plugins > Add > Import marketplace**.

The Codex IDE extension does not load plugins. There, add the connector with `codex mcp add tracy-ai-interviewer --url https://tracyinterview.ai/mcp` and copy the folders under `skills/` into `.agents/skills/` or `~/.agents/skills/`.

Remaining steps:
- **ChatGPT on the web and on mobile.** OpenAI marks an imported plugin that declares an MCP server as *Desktop only*. To reach web and mobile users, the Qode OpenAI organization owner (or a member with Apps Management Write) submits the plugin at `platform.openai.com/plugins`: developer verification, domain verification of `tracyinterview.ai` (a token served at `/.well-known/openai-apps-challenge`, done by the Tracy AI Interviewer server team), test cases, a demo video, reviewer test credentials, then OpenAI review. Until then, a ChatGPT Business or Enterprise admin can add `https://tracyinterview.ai/mcp` as a custom MCP server for their own workspace.

Docs: [Build plugins](https://developers.openai.com/plugins/build/plugins), [Plugins](https://developers.openai.com/codex/plugins), [Skills](https://developers.openai.com/codex/build-skills), [Submission](https://developers.openai.com/plugins/deploy/submission), [Custom MCP servers in ChatGPT](https://help.openai.com/en/articles/12584461), [Codex MCP](https://learn.chatgpt.com/docs/extend/mcp?surface=cli). Read 2026-11-17.

### Gemini CLI

Status: package added. Tested with Gemini CLI (`extensions validate` and `extensions link` load the MCP server and all four skills).

```sh
gemini extensions install https://github.com/Qode-Platform/tracy-ai-interviewer-plugin
```

Run it outside an interactive Gemini session, then restart Gemini CLI. Gemini CLI opens a browser to sign in the first time a Tracy AI Interviewer tool is used; `/mcp auth tracy-ai-interviewer` signs in again.

Remaining steps:
- **Gallery listing on geminicli.com/extensions.** No submission: once the repository is public, the repository owner adds the GitHub topic `gemini-cli-extension`. Google's crawler picks it up within a day or two.

Docs: [Extensions reference](https://github.com/google-gemini/gemini-cli/blob/main/docs/extensions/reference.md), [Releasing extensions](https://github.com/google-gemini/gemini-cli/blob/main/docs/extensions/releasing.md), [MCP servers](https://github.com/google-gemini/gemini-cli/blob/main/docs/tools/mcp-server.md), [Skills](https://github.com/google-gemini/gemini-cli/blob/main/docs/cli/skills.md). Read 2026-11-17.

### Gemini app (gemini.google.com)

Status: not possible from this repository. The Gemini app has no package a repository can ship; each user sets it up by hand.

Steps for the user:
1. On the web, open **Settings > Connected Apps > Custom apps**, add a custom app and paste `https://tracyinterview.ai/mcp`. Google currently limits custom apps to signed-in personal Google Accounts of people 18 or over in the US.
2. To add the skills, upload each folder under `skills/` (or a .zip of it, with `SKILL.md` at its root) under skills in Gemini.

Remaining steps:
- **Listing.** Google describes no directory or submission process for custom apps. Nothing for Qode to do until one exists.
- **Check before announcing.** The Tracy AI Interviewer server team should test sign-in from the Gemini app once, since Google's page does not state the plan requirement or transport details.
- **Gemini Enterprise.** A Google Cloud admin of the customer's organization can add `https://tracyinterview.ai/mcp` as a custom MCP server data store.

Docs: [Connect & manage custom apps](https://support.google.com/gemini/answer/17209137), [Create & manage skills](https://support.google.com/gemini/answer/17094296), [Gemini Enterprise custom MCP server](https://docs.cloud.google.com/gemini/enterprise/docs/connectors/custom-mcp-server/set-up-custom-mcp-server). Read 2026-11-17.

### Cursor

Status: package added. Manifests follow Cursor's reference; not yet tested inside Cursor.

- **Team marketplace (Teams and Enterprise plans).** A Cursor admin opens **Dashboard > Plugins & MCPs > Add Marketplace > Import from Repo** and pastes `https://github.com/Qode-Platform/tracy-ai-interviewer-plugin`. Members then install **Tracy AI Interviewer** from **Customize**.
- **Local install.** Clone this repository into `~/.cursor/plugins/local/tracy-ai-interviewer`, then run **Developer: Reload Window**.
- **Connector only, without the skills.** Use the install link `cursor://anysphere.cursor-deeplink/mcp/install?name=tracy-ai-interviewer&config=eyJ1cmwiOiJodHRwczovL3RyYWN5aW50ZXJ2aWV3LmFpL21jcCJ9`.

Cursor signs in with OAuth when the server is first used.

Remaining steps:
- **Public Cursor Marketplace.** Once the repository is public, the repository owner submits its link at `cursor.com/marketplace/publish`. The Cursor team reviews it, and reviews each later update.

Docs: [Plugins](https://cursor.com/docs/plugins), [Plugins reference](https://cursor.com/docs/reference/plugins), [MCP](https://cursor.com/docs/mcp), [MCP install links](https://cursor.com/docs/mcp/install-links). Read 2026-11-17.

### Mistral Vibe Code (CLI)

Status: package added. The root `plugin.json` and `mcp.json` are the Agent Plugins format Vibe Code loads; not yet tested in Vibe Code. Mistral marks plugin support as experimental.

Vibe Code has no install command for plugins. Clone this repository into `~/.vibe/plugins/tracy-ai-interviewer` (or `./.vibe/plugins/tracy-ai-interviewer` in a trusted project), run `/reload-plugins`, then sign in with `/mcp login tracy-ai-interviewer`. The skills appear as `/tracy-ai-interviewer:<skill>`.

Without the plugin: `vibe mcp add tracy-ai-interviewer --url https://tracyinterview.ai/mcp`, and copy the folders under `skills/` into `~/.vibe/skills/`.

Docs: [Plugins](https://docs.mistral.ai/vibe/code/cli/plugins), [MCP servers](https://docs.mistral.ai/vibe/code/cli/mcp-servers), [Skills](https://docs.mistral.ai/vibe/code/cli/skills). Read 2026-11-17.

### Le Chat (Mistral Vibe Work)

Status: not possible from this repository. Le Chat, now Mistral Vibe Work, has no package a repository can ship.

Steps for the account administrator (the account owner on Free, Pro and Student plans):
1. Open **Connectors**, click **+ Add Connector**, switch to **Custom MCP Connector**, name it `tracyaiinterviewer`, enter `https://tracyinterview.ai/mcp`, click **Connect** and sign in.
2. To add the skills, open **Context > Skills > New Skill** once per folder under `skills/`, and paste the title, description and body of its `SKILL.md`.

Users then turn the connector on per task under **Tools**.

Remaining steps:
- **Connector directory listing.** Mistral publishes no submission process for its connector directory. The only route is Qode's business owner contacting Mistral through the partner form at `mistral.ai/partners`.

Docs: [Custom MCP connectors](https://docs.mistral.ai/vibe/work/connectors/mcp-connectors), [Connectors](https://docs.mistral.ai/vibe/work/connectors), [Skills](https://docs.mistral.ai/vibe/work/skills). Read 2026-11-17.

## Approval and data

Review the draft and tool preview before approving interview creation, invitations, or enabling a public link. Invitations use addresses you provide. A practice run uses an interview result; the first three results are free, with no card needed.

The plugin contains Markdown skills and JSON configuration, with no local scripts or executables. It connects to `https://tracyinterview.ai/mcp`. Depending on your request, the AI app you use sends interview context, questions, settings, participant names and email addresses, and approved actions to Tracy AI Interviewer, and fetches interview lists, participant states, answers, and result links. Those requests operate on your Tracy AI Interviewer account. The plugin itself has no separate data store. See the [Tracy AI Interviewer privacy policy](https://tracyinterview.ai/privacy).

## Local development

```sh
claude plugin validate . --strict
claude plugin validate .claude-plugin/plugin.json --strict --profile directory
claude --plugin-dir .
```

For the other apps' manifests:

```sh
gemini extensions validate .                                    # Gemini CLI
codex plugin marketplace add . && codex plugin list             # Codex (use a throwaway CODEX_HOME)
```

The root `plugin.json` and `mcp.json` follow the [Agent Plugins 1.0 schemas](https://agent-plugins.org/schemas/1.0.0/plugin.schema.json); validate them against `plugin.schema.json` and `mcp.schema.json` with any JSON Schema (draft 2020-12) validator.

The repository root is the plugin folder. `.claude-plugin/marketplace.json` exposes it with `source: "./"`; `.claude-plugin/plugin.json` registers the four folders under `skills/`, and `.mcp.json` declares the connector.

See Claude's [plugin structure and testing guide](https://claude.com/docs/plugins/build) and [pre-submission checklist](https://claude.com/docs/plugins/pre-submission-checklist). Directory validation and submission are separate owner steps.

## License

[Apache License 2.0](LICENSE).
