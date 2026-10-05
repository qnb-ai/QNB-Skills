# QNB Agents

This folder contains Claude Code agent definitions for QNB developers. Each agent is a Markdown file that tells Claude how to handle one kind of task the QNB way.

## Available agents

| Agent | File | What it does |
|-------|------|--------------|
| `qnb-branding` | [qnb-branding.md](qnb-branding.md) | Creates and reviews QNB documents so they match the QNB colours, typography, logo rules, layout and tone of voice. |

## Usage

Claude will pick the agent automatically when a task matches its description, for example when you edit a QNB email template. You can also ask for it by name:

```text
Use the qnb-branding agent to review (document name here)
```

```text
Use the qnb-branding agent to create a new announcement email
```

When **reviewing**, the agent reports issues with file and line references and the on-brand fix. It only changes the file if you ask it to.

When **creating**, it starts from the existing email template structure and checks its own output against the brand rules before returning.

## Brand quick reference

| Element | Value |
|---------|-------|
| Headings | Poppins 600/700, `#011A36` (navy) |
| Body text | Open Sans 14–16px, `#444444` / `#555555` |
| Primary CTA / links | `#006CBC` (blue) |
| Secondary accent | `#B41D52` (maroon) |
| Page background | `#F2F4F7` |
| Email width | 600px max, table-based, mobile breakpoint 620px |

See [qnb-branding.md](qnb-branding.md) for the full rules.

## Adding a new agent

1. Create a new `.md` file in this folder with a short, kebab-case name (e.g. `qnb-email-qa.md`).
2. Start it with frontmatter:

   ```markdown
   ---
   name: qnb-email-qa
   description: One or two sentences on when Claude should use this agent.
   tools: Read, Grep, Glob
   ---
   ```

3. Write the agent's instructions below the frontmatter: what it knows, the rules it follows and how it should work.
4. Only grant the tools the agent needs. Leave out `Edit`/`Write` for review-only agents.
5. Add a row to the **Available agents** table above.
