# VS Code Exclude Expressions

Glob patterns to exclude unwanted directories and build artifacts from VS Code search and the file explorer.

## Glob Pattern
```glob
**/node_modules, **/resources, **/*.spec.ts
```

---

## Configuration in `settings.json`
```json
{
  "files.exclude": {
    "**/node_modules": true,
    "**/resources": true,
    "**/*.spec.ts": true
  },
  "search.exclude": {
    "**/node_modules": true,
    "**/resources": true,
    "**/*.spec.ts": true
  }
}
```
