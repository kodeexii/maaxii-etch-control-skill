# MaaXII Etch Control - AI Reference

This plugin allows programmatic management of Etch pages.

## Primary Abilities

- **`maaxii/build-etch-page`**: Creates or updates a page using JSON blueprint.
- **`maaxii/append-etch-section`**: Adds a new section to an existing page.
- **`maaxii/get-page-blocks`**: Inspects current block structure.
- **`maaxii/delete-pages`**: Deletes pages by search keyword.
- **`maaxii/ping`**: Verifies connectivity.

## Blueprint Schema

The plugin expects a recursive JSON structure:
- `tag`: HTML tag (section, div, h1, p, etc.)
- `name`: Descriptive name for the Etch Navigator.
- `styles`: Array of Etch system styles (must include `etch-section-style` or `etch-container-style` for structural blocks).
- `attrs`: HTML attributes including CSS classes.
- `children`: Nested array of nodes or text objects (`{"text": "..."}`).

## Important Notes

- **Deactivate/Reactivate**: Required after code changes to refresh Ability Registry.
- **wp_slash**: Plugin handles escaping; send clean JSON.
- **Auto-registration**: New classes in `attrs` are automatically registered in Etch.
