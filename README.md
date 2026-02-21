# MaaXII Etch Control Skill

This repository contains an AI Skill designed for AI agents (like Gemini, Claude, etc.) to programmatically build and manage WordPress pages using the [MaaXII Etch Control](https://github.com/kodeexii/maaxii-etch-control) plugin and [Etch Page Builder](https://etchwp.com/).

## Overview

This skill provides the necessary context, design standards, and technical blueprints for an AI to:
- Generate production-grade Etch pages.
- Adhere to BEM (Block-Element-Modifier) naming conventions.
- Integrate with Automatic CSS (ACSS) variables.
- Use the WordPress Abilities API for remote content management.

## Contents

- `SKILL.md`: The main instruction set for the AI agent.
- `references/`:
  - `gemini-standards.md`: CSS and design guidelines.
  - `example-blueprint.json`: Sample JSON structure for Etch pages.
  - `plugin-readme.md`: Technical manual for the companion plugin.

## How to Use

If you are using an AI agent with the Gemini CLI or a similar MCP-compatible environment:

1. Clone this repository into your `agent-skills` directory.
2. Activate the skill: `activate_skill(name='maaxii-etch-control-skill')`.
3. Provide your copywriting, and the AI will handle the rest via the `maaxii/*` abilities.

## Requirements

- **MaaXII Etch Control Plugin** (Active on target site).
- **WordPress Abilities API** & **MCP Adapter**.
- **Etch Page Builder**.

## License

This project is licensed under the GPL-2.0-or-later License.
