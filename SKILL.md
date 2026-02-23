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
- **COMMON CLASS ARCHITECTURE**: When components share the same styling across multiple pages, ALWAYS use common, descriptive class names instead of page-specific prefixes (e.g., use `.hero-layered`, `.strategy-card`, or `.process-step` instead of `.binawp-hero` or `.bersihwp-hero`). This ensures a modular design system where global updates can be managed from a single style entry in Etch.
- **CLASS-FIRST (NO INLINE STYLES)**: Never use the `style` attribute in HTML layout nodes. All styles must be moved to the `styles` object to register clean CSS classes in Etch.
- **PSEUDO-STATES & ELEMENTS**: All pseudo-states (e.g., `:hover`, `:active`, `:focus`) and pseudo-elements (e.g., `::before`, `::after`) MUST be registered as separate style entries in the `styles` object and added to the element's `styles` array.
- **LOCAL MEDIA & WEBP FIRST**: External images (Unsplash, etc.) MUST be downloaded to the server and imported into the Media Library using `wp media import` before being linked. Crucially, images MUST be in **WebP format**. Use **ImageMagick (`magick`)** as the standard local tool for conversion (e.g., `magick input.png output.webp`) to ensure high performance since browser-level optimizers are bypassed via API/CLI.
- **SEO & ACCESSIBILITY (ALT TEXT)**: Every `img` tag MUST have a descriptive `alt` attribute. This is mandatory for SEO indexing and screen reader accessibility.
- **DNA MATCHING**: Every element in the blueprint MUST have a `"styles": []` array (even if empty) to satisfy Etch rendering requirements.

## 2. MaaXII Page Building SOP (Platinum Workflow)

1. **Content Creation (Verbatim Mandate)**
   - **Pre-flight Check**: ALWAYS verify if a source Markdown file exists in the specific project directory (e.g., `ServisWP/`, `harumanis/`, `LaLega/`).
   - **If Missing**: YOU MUST create the project folder and the Markdown content first. The structure should be logical and tailored to the specific product/project requirements.
   - **Verbatim Mandate**: Once the structure is defined in Markdown, you MUST copy 100% of that content during construction. NEVER summarize or omit sections defined in the source.

2. **Wireframe Construction (Structure Check)**
   - **No Styling**: Focus purely on HTML hierarchy (Section > Container > Elements).
   - **Etch DNA**: Use `data-etch-element` attributes correctly to verify layout flow.

3. **Design & Visual Implementation (Local Prototypes)**
   - **Local HTMLs**: Develop styling and image integration in a local `.html` file first.
   - **WebP & Local Media**: Download images as WebP, upload to server, and use local URLs.
   - **Class-First (Common Classes)**: Use descriptive, reusable class names (e.g., `.strategy-card`). No inline styles.
   - **SEO**: Descriptive `alt` tags are mandatory.

4. **Server Deployment & Validation (Proper Page Building)**
   - **1:1 Mirroring**: Translate local HTML structure exactly into Blueprint JSON layout.
   - **Data Integrity**: ALWAYS write JSON to a file and use `curl.exe -d "@file.json"`.
   - **Pseudo Registration**: Register `:hover`, `::after`, etc., as separate style entries.
   - **Validation**: Final visual check on server to ensure side-by-side layouts and contrast.

## 3. Reference Material

- **BEM/ACSS**: Refer to `references/gemini-standards.md`.
- **JSON Format**: Refer to `references/example-blueprint.json`.
- **Manual**: Refer to `references/plugin-readme.md`.

## 4. Troubleshooting

- **"@@" or Missing Text**: Usually caused by incorrect `innerContent` whitespace or missing `styles` array in JSON.
- **Empty Elements**: Check if `attrs` was correctly mapped to `attributes` in the payload.
