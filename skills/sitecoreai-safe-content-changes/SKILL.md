---
name: sitecoreai-safe-content-changes
description: Use when the user asks to delete, remove, move or update content items, pages or components in SitecoreAI through the Sitecore Marketer MCP server. Enforces impact checks, explicit confirmation and a no-publish default before any change.
---

# Safe content changes in SitecoreAI (Marketer MCP)

Use this workflow whenever a request would **change** or **remove** existing content or page structure. It applies to these Sitecore Marketer MCP tools:

- `delete_content`
- `remove_component_on_page`
- `move_component_on_page`
- `update_content`
- `update_fields_on_item`
- `set_component_datasource` (when it replaces or clears an existing datasource)

Read-only tools (`get_*`, `list_*`, `search_*`) never need confirmation.

## Core rules

1. **Read before you change.** Always read the current state first, so you can show the user a before/after state.
2. **Impact check before any removal.** Never delete or remove without reviewing what references the target.
3. **Confirm explicitly.** Summarise the exact change and wait for the user to say "confirm" (or equivalent) before calling a mutating tool. A vague earlier request such as "clean up the homepage" is not confirmation.
4. **Never publish.** None of these tools publish. Do not offer to publish unless the user asks. After a change, tell the user it is not live until they publish.
5. **One mutation per confirmation.** Do not retry a failed mutation automatically. Report the error and ask how to proceed.
6. **Stay in scope.** Change only what the user explicitly requested. If the request is ambiguous (several matching pages, components or items), list the candidates with IDs and paths and ask which one.

## Workflows

### Delete a content item (`delete_content`)

1. Identify the item. Use `get_content_item_by_path` or `get_content_item_by_id` and show its name, path and template.
2. Run `get_content_references` and report the pages and components that reference it.
3. Tell the user:
   - The item and **all its child items in all languages,** are deleted. The language parameter is currently ignored, so a single-language delete is not possible.
   - Deleted items go to the recycle bin and can be restored.
   - The tool may ask whether to also remove references and archive related experiments or delete only the item. Present that choice clearly and do not pick for the user.
4. Wait for explicit confirmation, then call `delete_content`.
5. Report what was deleted and what happened to the references and experiments.

### Remove a component from a page (`remove_component_on_page`)

1. Use `get_components_on_page` to find the component instance. Show its name, placeholder and datasource content.
2. If the page has A/B/n tests or personalisation, check `list_page_flows` and warn if the component is part of one. The tool also checks for affected experiments and asks for confirmation.
3. Ask for confirmation, then call the tool.
4. Report the result and any affected experiments.

### Move a component (`move_component_on_page`)

1. Use `get_components_on_page` to confirm the component ID, its current placeholder and the target position.
2. If moving to another placeholder, check `get_allowed_comps_by_ph` to confirm the component is allowed there.
3. State the move in one line (for example: "Move Hero from /headless-main to the sidebar placeholder after component X") and ask for confirmation. The tool also requires explicit confirmation.
4. Call the tool once. Do not retry on failure.

### Update content (`update_content`, `update_fields_on_item`)

1. Fetch the current values with `get_content_item_by_id` or `get_content_item_by_path`.
2. Show a before/after table of the fields being changed. Leave all other fields untouched.
3. Mention that if the item is in a Final or Approved workflow state, `update_content` creates a new version automatically.
4. Ask for confirmation, then apply the change.
5. End with: "Saved, not published."

### Replace or clear a datasource (`set_component_datasource`)

1. Show the current datasource with `get_components_on_page`.
2. If a `variantId` applies (personalisation or A/B/n variant), confirm with the user whether the change is for the default page or a specific variant. Find variant IDs with `list_page_flows`.
3. Confirm, then apply.

## Response format

Before asking for confirmation, present:

- **Target:** name, ID, path, language
- **Change:** exactly what will happen
- **Impact:** references, experiments, child items
- **Reversibility:** for example "recycle bin", "new version created" or "no automatic undo"

After the change, give a one-paragraph phase summary plus "Not published" where relevant.

