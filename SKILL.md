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

## 1. Core Mandates (STABILITY & QUALITY FIRST)

- **VERBATIM CONTENT (ABSOLUTE)**: Never summarize or shorten source content (Markdown). Every word of story, bridge, intro, and FAQ must be copied 100% exactly as provided.
- **DATA INTEGRITY (CRITICAL)**: NEVER use PowerShell variables or `ConvertTo-Json` to pipe data to the API. It corrupts data (e.g., converting @layer to filename). ALWAYS write to a physical `.json` file and use `curl.exe -d "@file.json"`.
- **SHARED UI STANDARD**: Use the prefix `serviswp-` for all shared service components (e.g., `.serviswp-hero`, `.serviswp-strategy-card`). Avoid page-specific prefixes unless the component is unique.
- **CLASS-FIRST (NO INLINE STYLES)**: Never use the `style` attribute in HTML layout nodes. All styles must be moved to the `styles` object to register clean CSS classes in Etch.
- **HOVER LOGIC**: Hover effects must be registered as separate style entries (e.g., `.serviswp-card:hover`) and added to the element's `styles` array.
- **LOCAL MEDIA ONLY**: External images (Unsplash, etc.) must be downloaded to the server and imported into the Media Library using `wp media import` before being linked in the blueprint.
- **SEO & ACCESSIBILITY (ALT TEXT)**: Every `img` tag MUST have a descriptive `alt` attribute. This is mandatory for SEO indexing and screen reader accessibility.
- **DNA MATCHING**: Every element in the blueprint MUST have a `"styles": []` array (even if empty) to satisfy Etch rendering requirements.

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
