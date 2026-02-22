# @upbiit/prettier-config

Prettier configuration for TypeScript, Angular, and Node.js projects. Fully compatible with [@upbiit/eslint-config](https://github.com/upbiit/eslint-config).

## Features

- ✅ **Strict formatting rules** with 125 character line length
- ✅ **Single quotes** throughout
- ✅ **Trailing commas** on all multi-line structures
- ✅ **Semicolons required** on all statements
- ✅ **2-space indentation** (tabs disabled)
- ✅ **LF line endings** (Unix standard, cross-platform safe)
- ✅ **Full language support**: TypeScript, JavaScript, HTML, SCSS, Markdown, JSON
- ✅ **Angular template support** (built-in)
- ✅ **Prose wrapping** for documentation and comments
- ✅ **ESLint integration** - no conflicts with @upbiit/eslint-config

## Requirements

- Prettier 3.0+
- Node.js 16+

## Installation

### Option 1: Use as a Shareable Config (Recommended)

```bash
npm install --save-dev @upbiit/prettier-config prettier
```

Create `.prettierrc.json` in your project root:

```json
{
  "extends": ["@upbiit/prettier-config"]
}
```

### Option 2: Direct Installation

```bash
npm install --save-dev prettier
```

Copy `.prettierrc` and `.prettierignore` directly into your project root.

## Configuration

The configuration enforces:

### Code Style

- **Quotes**: Single quotes (`'`) for all strings
- **Semicolons**: Required at end of all statements
- **Indentation**: 2 spaces (no tabs)
- **Line Length**: 125 characters
- **Trailing Commas**: On all multi-line structures
- **Arrow Functions**: Always wrapped in parentheses `(x) => x`

### File Types

Prettier automatically handles:

- **TypeScript** (`.ts`, `.tsx`)
- **JavaScript** (`.js`, `.jsx`)
- **HTML** (`.html`, `.template`, Angular templates)
- **SCSS/SASS** (`.scss`, `.sass`)
- **JSON** (`.json`, `.jsonc`)
- **Markdown** (`.md`, `.markdown`)
- **YAML** (`.yaml`, `.yml`)

### Ignored Files

The following are not formatted:

```
node_modules/
dist/
build/
coverage/
**/*.min.js
**/*.min.css
```

## Usage

### Add to package.json Scripts

```json
{
  "scripts": {
    "format": "prettier --write .",
    "format:check": "prettier --check .",
    "lint": "eslint src --ext .ts,.html",
    "lint:fix": "eslint src --ext .ts,.html --fix && prettier --write ."
  }
}
```

### Command Line

```bash
# Format all files
npm run format

# Check if files are formatted
npm run format:check

# Format specific file
npx prettier --write src/app.ts

# Format specific directory
npx prettier --write src/services
```

### IDE Integration

#### VSCode

Install the [Prettier - Code formatter](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode) extension.

Create `.vscode/settings.json`:

```json
{
  "[typescript]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode",
    "editor.formatOnSave": true
  },
  "[html]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode",
    "editor.formatOnSave": true
  },
  "[scss]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode",
    "editor.formatOnSave": true
  },
  "[json]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode",
    "editor.formatOnSave": true
  },
  "[markdown]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode",
    "editor.formatOnSave": true
  }
}
```

#### WebStorm / IntelliJ IDEA

1. Go to **Settings** → **Languages & Frameworks** → **JavaScript** → **Prettier**
2. Enable **Run for files on Save**
3. Prettier will auto-detect `.prettierrc`

### Git Hooks (Pre-commit)

Use [husky](https://typicode.io/husky) to format before commits:

```bash
npm install --save-dev husky lint-staged

npx husky install
npx husky add .husky/pre-commit "npx lint-staged"
```

Update `package.json`:

```json
{
  "lint-staged": {
    "*.{ts,tsx,js}": "prettier --write",
    "*.html": "prettier --write",
    "*.scss": "prettier --write",
    "*.json": "prettier --write",
    "*.md": "prettier --write"
  }
}
```

## Examples

### TypeScript

Before:

```typescript
const user={name:'John',email:'john@example.com'}
function getUserName(){return 'John'}
const square=x=>x*x
```

After:

```typescript
const user = { name: 'John', email: 'john@example.com' };
function getUserName(): string {
  return 'John';
}
const square = (x) => x * x;
```

### HTML / Angular Templates

Before:

```html
<div class="container"><span>Hello</span><span>World</span></div>
```

After:

```html
<div class="container">
  <span>Hello</span>
  <span>World</span>
</div>
```

### SCSS

Before:

```scss
$colors={primary:'#007bff',secondary:'#6c757d'}
.button{color:$colors.primary;padding:8px 16px;}
```

After:

```scss
$colors: {
  primary: '#007bff',
  secondary: '#6c757d',
};
.button {
  color: $colors.primary;
  padding: 8px 16px;
}
```

### JSON

Before:

```json
{"name":"project","version":"1.0.0","author":"John","keywords":["typescript","angular"]}
```

After:

```json
{
  "name": "project",
  "version": "1.0.0",
  "author": "John",
  "keywords": [
    "typescript",
    "angular"
  ]
}
```

### Markdown

Before:

```markdown
# My Project
This is a very long description that exceeds the print width limit and should be wrapped to the configured line length for better readability in editors and documentation files.
```

After:

````markdown
# My Project

This is a very long description that exceeds the print width limit and should be wrapped to
the configured line length for better readability in editors and documentation files.