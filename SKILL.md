---
name: maaxii-etch-control-skill
description: Expert skill for programmatically building WordPress pages using the MaaXII Etch Control plugin and Etch Page Builder. Follows BEM standards and Automatic CSS (ACSS).
---

# MaaXII Etch Control Skill

Use this skill when the user asks to build, update, or manage WordPress pages using the MaaXII Etch Control plugin and Etch Page Builder.

## 0. Prerequisites (Mandatory Check)

Before executing any tasks, the AI Agent must verify:
1. **Plugin Active**: `MaaXII Etch Control` (v1.0.0+) must be installed and active on the WordPress site.
2. **Connectivity**: Call `mcp-adapter-discover-abilities` to confirm `maaxii/*` tools are available.
3. **Infrastructure**: `mcp-adapter` and `Abilities API` must be running in the WordPress environment.
4. **Etch Page Builder**: Must be active for block rendering.
5. **Automatic CSS (ACSS)**: **Recommended but NOT required.** 
   - *Note: If ACSS is missing, the content, structure, and CSS classes will still be generated correctly, but the visual styling (variables for spacing/colors) will not be applied as intended.*

*Note: If abilities are not found, prompt the user to deactivate and reactivate the MaaXII Etch Control plugin.*

## 1. Core Mandates

- **Abilities First**: Always use `maaxii/build-etch-page` or `maaxii/append-etch-section` to modify pages.
- **Blueprint JSON**: Never send raw HTML. Always generate a structured Blueprint JSON.
- **Etch Hierarchy**: Follow the mandatory structure: `Section > Container > [Elements]`.
- **BEM Standard**: Use Class-first approach. Every element must have a BEM class.
- **ACSS Integration**: Use Automatic CSS variables (if ACSS is present).

## 2. Technical Workflow

1.  **Analyze Content**: Break down the user's copywriting into logical sections.
2.  **Map to BEM**: Define block names (e.g., `hero-section`, `strategy-grid`).
3.  **Generate Blueprint**:
    - Assign `etch-section-style` to sections.
    - Assign `etch-container-style` to containers.
    - Place content in `children`.
4.  **Execute**: Call the `maaxii/build-etch-page` ability.

## 3. Reference Material

- **Design Standards**: Refer to `references/gemini-standards.md`.
- **Example Blueprint**: Refer to `references/example-blueprint.json`.
- **Plugin Manual**: Refer to `references/plugin-readme.md`.

## 4. Troubleshooting for AI

- If "Ability not found", ask the user to deactivate and reactivate the plugin.
- If styles aren't appearing, ensure the class is included in the `attrs` of the node.
- Always ensure special characters in JSON are correctly escaped.
