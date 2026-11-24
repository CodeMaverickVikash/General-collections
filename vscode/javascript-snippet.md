# VS Code JavaScript Snippets

Custom user snippets for JavaScript development.

## Setup
In VS Code, open **File → Preferences → Configure User Snippets** (or press <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> → `Preferences: Configure User Snippets`), select `javascript.json`, and paste the configuration below:

```json
{
  "Print to console": {
    "prefix": "clg",
    "body": [
      "console.log($0);"
    ],
    "description": "Log output to console"
  },
  "arrow function": {
    "prefix": "function",
    "body": [
      "const $1 = ($2) => {",
      "  $3",
      "};$0"
    ],
    "description": "Create arrow function"
  },
  "function with default export": {
    "prefix": "function",
    "body": [
      "const $1 = ($2) => {",
      "  $3",
      "};",
      "",
      "export default $0;"
    ],
    "description": "Create a function with default export"
  }
}
```
