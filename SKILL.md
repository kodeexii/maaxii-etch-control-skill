---
name: maaxii-etch-control-skill
description: Expert skill for programmatically building WordPress pages using the MaaXII Etch Control plugin and Etch Page Builder. Follows BEM standards and Automatic CSS (ACSS).
---

# MaaXII Etch Control Skill

Use this skill when the user asks to build, update, or manage WordPress pages using the MaaXII Etch Control plugin and Etch Page Builder.

## 0. Prerequisites (Mandatory Check)

Before executing any tasks, the AI Agent must verify:
1. **Plugin Active**: `MaaXII Etch Control` (v1.0.14+) must be installed and active.
2. **Connectivity**: Call `mcp-adapter-discover-abilities` to confirm `maaxii/*` tools are available.
3. **Environment**: Etch Page Builder must be active. Automatic CSS (ACSS) is recommended for full styling support.

## 1. Core Mandates (STABILITY FIRST)

- **Blueprint JSON**: Never send raw HTML. Always use the structured Blueprint JSON.
- **DATA INTEGRITY (CRITICAL)**: NEVER use PowerShell variables or `ConvertTo-Json` to pipe data to the API. It corrupts the object structure (e.g., converting objects to strings like `@{metadata=...}`).
- **FILE-BASED DELIVERY**: ALWAYS write your blueprint to a temporary file (e.g., `payload.json`) and use `curl.exe -d "@payload.json"` to ensure the JSON reaches the server exactly as written.
- **DNA MATCHING**: Every element in the blueprint MUST have a `"styles": []` array (even if empty) to satisfy Etch rendering requirements.
- **SIMPLE HIERARCHY**: Prefer clean text nodes inside tags. Avoid deep nesting like `h1 > span > text` unless necessary for complex styling.

## 2. Technical Workflow

1.  **Analyze Content**: Break down the user's copywriting into sections.
2.  **Generate Blueprint**:
    - Assign `etch-section-style` to sections.
    - Assign `etch-container-style` to containers.
    - Ensure every node has `tag`, `styles`, `attrs`, and `children` (or `text`).
3.  **Deploy**:
    - Write to `payload.json`.
    - Run: `curl.exe -X POST -u "USER:PASS" -H "Content-Type: application/json" -d "@payload.json" https://.../run`

## 3. Reference Material

- **BEM/ACSS**: Refer to `references/gemini-standards.md`.
- **JSON Format**: Refer to `references/example-blueprint.json`.
- **Manual**: Refer to `references/plugin-readme.md`.

## 4. Troubleshooting

- **"@@" or Missing Text**: Usually caused by incorrect `innerContent` whitespace or missing `styles` array in JSON.
- **Empty Elements**: Check if `attrs` was correctly mapped to `attributes` in the payload.
