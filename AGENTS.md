# AGENTS.md - GameBanana API Documentation

This repository contains offline-copied GameBanana API documentation in Markdown format. Agents working here should follow these guidelines.

## Repository Structure

```
Gamebanana API/
├── docs/
│   ├── Complete.API.Documentation.md    # Main comprehensive guide
│   └── endpoints/                       # Individual endpoint docs
│       ├── Core.App.Authenticate.md
│       ├── Core.Item.Data.md
│       ├── Core.List.Section.md
│       ├── WebAPI.Overview.md
│       └── ... (21 endpoint files)
├── docs.json        # Index array with slug, title, url, file_path, headings, outgoing_links
├── README.md        # Site scope, crawl date, selection criteria
└── SUMMARY.md       # Logical index linking all pages by category
```

## File Naming Conventions

- Use dots (`.`) instead of slashes in filenames: `Core.Item.Data.md` not `Core/Item/Data.md`
- Keep filenames lowercase
- Use descriptive names: `WebAPI.Overview.md` not `api_overview.md`

## Documentation Standards

### Markdown Formatting

- Use ATX-style headers (`#`, `##`, `###`)
- Use fenced code blocks with language hints:
  ```markdown
  ```bash
  curl "https://api.example.com/endpoint"
  ```
  ```
- Use tables for parameter lists and comparisons
- Use bullet lists for enumerations

### Content Guidelines

1. **Title**: Use the API endpoint path as the title (e.g., `# Core / Item / Data`)
2. **Description**: 1-2 sentence summary of what the endpoint does
3. **Endpoint URL**: Show the full URL pattern
4. **Parameters**: Table with columns: Parameter, Type, Description
5. **Examples**: Show both success and error examples
6. **Response Fields**: Document key fields returned

### Cross-Referencing

- Link to other docs using relative Markdown links
- Example: `[Core/Item/Data](./Core.Item.Data.md)`
- Update `docs.json` `outgoing_links` array when adding cross-references

## docs.json Index Format

Each entry must have:
```json
{
  "slug": "unique-slug",
  "title": "Display Title",
  "url": "Original source URL",
  "file_path": "Relative path from repo root",
  "headings": ["H1", "H2", "H3"],
  "outgoing_links": ["file1.md", "file2.md"]
}
```

## Updating the Documentation

### Adding a New API Endpoint

1. Create new `.md` file in `docs/endpoints/`
2. Add entry to `docs.json` with all required fields
3. Update `SUMMARY.md` with link in appropriate category
4. Add outgoing links to related docs in `docs.json`

### Crawling New API Pages

When crawling from `https://api.gamebanana.com/` or `https://gamebanana.com/apiv11`:

1. Use `webfetch` tool to get content
2. Extract: title, description, parameters, examples
3. Convert HTML tables to Markdown tables
4. Preserve code block language hints
5. Keep inline links as relative paths where possible
6. Add to `docs.json` index

## What NOT To Do

- Don't modify the JSON structure in docs.json
- Don't break existing relative links
- Don't add generated content (AI summaries, etc.)
- Don't include nav/footers/ads from source pages
- Don't use absolute URLs for internal links

## Quick Reference

| Task | Command/Action |
|------|---------------|
| Add endpoint doc | Create `docs/endpoints/Name.md`, update `docs.json` |
| Update index | Edit `docs.json` array |
| Add to summary | Edit `SUMMARY.md` |
| Check links | Verify relative paths exist |

## External Resources

- **Official API**: https://api.gamebanana.com/
- **Web API Base**: https://gamebanana.com/apiv11
- **Source Repository**: None (static docs)

## Notes

- This is a documentation-only repository (no code, tests, or build)
- All content is Markdown with JSON index
- Crawl date tracked in README.md
- No linting or testing needed for Markdown content
