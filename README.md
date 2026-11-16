# Tracy AI Interviewer

Run AI video or audio interviews from Claude. This plugin bundles the Tracy AI Interviewer connector with four skills to draft interviews, try a practice run, invite people, and read what they said. Tracy AI Interviewer reports answers; it does not score, rank, reject, or decide for you.

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

## Approval and data

Review the draft and tool preview before approving interview creation, invitations, or enabling a public link. Invitations use addresses you provide. A practice run uses an interview result; the first three results are free, with no card needed.

The plugin contains Markdown skills and JSON configuration, with no local scripts or executables. It connects to `https://tracyinterview.ai/mcp`. Depending on your request, Claude sends interview context, questions, settings, participant names and email addresses, and approved actions to Tracy AI Interviewer, and fetches interview lists, participant states, answers, and result links. Those requests operate on your Tracy AI Interviewer account. The plugin itself has no separate data store. See the [Tracy AI Interviewer privacy policy](https://tracyinterview.ai/privacy).

## Local development

```sh
claude plugin validate . --strict
claude plugin validate .claude-plugin/plugin.json --strict --profile directory
claude --plugin-dir .
```

The repository root is the plugin folder. `.claude-plugin/marketplace.json` exposes it with `source: "./"`; `.claude-plugin/plugin.json` registers the four folders under `skills/`, and `.mcp.json` declares the connector.

See Claude's [plugin structure and testing guide](https://claude.com/docs/plugins/build) and [pre-submission checklist](https://claude.com/docs/plugins/pre-submission-checklist). Directory validation and submission are separate owner steps.

## License

[Apache License 2.0](LICENSE).
