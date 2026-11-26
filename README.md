# Maventa agent skills

Agent skills for building and debugging integrations with
[Maventa](https://documentation.maventa.com)'s e-invoicing and e-document
exchange APIs. They follow the open [Agent Skills](https://agentskills.io)
format and work in Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI,
claude.ai and other agents that support skills.

## Skills

| Skill | What it does |
| --- | --- |
| [`maventa-integration`](skills/maventa-integration/SKILL.md) | Helps your coding agent with the Maventa REST and SOAP APIs: authentication, invoice sending and receiving, Peppol, invoice formats, consumer invoicing, printing, scanning, webhooks, receivables and country rules. |

The skill holds the stable basics and an index of every documentation page
with a one-line summary. Your agent picks the relevant pages from the index
and fetches them live from documentation.maventa.com as markdown, so answers
come from the current documentation. The skill only reads public
documentation: it has no access to your Maventa account and needs no API
keys.

## Install

### Claude Code

```text
/plugin marketplace add maventa/agent-skills
/plugin install maventa@maventa
```

### Codex, Cursor, Copilot, Gemini CLI and other agents

With the [skills CLI](https://github.com/vercel-labs/skills):

```sh
npx skills add maventa/agent-skills
```

Add `-a codex`, `-a cursor` or another agent name to choose the agent, and `-g`
to install for your user instead of the current project.

To install by hand, download
[maventa-integration.zip](https://github.com/maventa/agent-skills/releases/latest/download/maventa-integration.zip)
and unzip it into your agent's skills folder, for example
`~/.agents/skills/` for Codex.

### claude.ai

Download
[maventa-integration.zip](https://github.com/maventa/agent-skills/releases/latest/download/maventa-integration.zip),
then go to **Customize > Skills**, select **+ > Create skill > Upload a skill**
and upload the zip.

## Updates

The skill is regenerated from the documentation and released here whenever
the documentation changes. Version numbers are `MAJOR.MINOR.PATCH`: a new
patch version only updates the page index or wording.

- **Claude Code:** third-party marketplaces do not update automatically by
  default. Turn it on in `/plugin` > **Marketplaces** > **maventa** >
  **Enable auto-update**, or update by hand with
  `/plugin marketplace update maventa`.
- **skills CLI:** `npx skills check` shows available updates, and
  `npx skills update` installs them.
- **Zip installs (claude.ai, manual):** download the latest zip again.

## Support

- Documentation: https://documentation.maventa.com
- Machine-readable index: https://documentation.maventa.com/llms.txt
- Integration help: integrations@maventa.com
- Problems with the skill: open an issue in this repository.

This repository is generated from the Maventa documentation source, so pull
requests can't be merged here. Please open an issue instead.

## License

[MIT](LICENSE)
