# Biome Setup Guide for Angular Projects

This guide documents all steps taken to add, configure, and use Biome for linting and formatting in this Angular project.

---

## 1. Install Biome

Install Biome as a development dependency:

```bash
npm install --save-dev @biomejs/biome
```

---

## 2. Initialize Biome Configuration

Generate a default configuration file:

```bash
npx biome init
```

---

## 3. Configure Biome for Angular

Edit `biome.json` to:
- Restrict linting/formatting to the `src` folder
- Enable strict and recommended rules for TypeScript, JavaScript, JSON, CSS, and HTML (where supported)
- Use only valid, documented Biome configuration keys

Example (see your current `biome.json` for details):

```json
{
  "$schema": "https://biomejs.dev/schemas/2.2.0/schema.json",
  "files": {
    "includes": ["src/**/*"],
    "ignoreUnknown": false
  },
  "linter": {
    "enabled": true,
    "rules": {
      "recommended": true,
      "correctness": { "recommended": true },
      "suspicious": { "recommended": true },
      "style": { "recommended": true },
      "complexity": { "recommended": true }
    }
  },
  "formatter": {
    "enabled": true,
    "indentStyle": "space",
    "indentWidth": 2,
    "lineWidth": 100
  },
  "javascript": {
    "parser": { "unsafeParameterDecoratorsEnabled": true },
    "formatter": { "quoteStyle": "single", "semicolons": "always" }
  },
  "json": { "formatter": { "enabled": true, "indentStyle": "space", "indentWidth": 2 } },
  "css": { "formatter": { "enabled": true, "indentStyle": "space", "indentWidth": 2 } },
  "html": { "parser": { "interpolation": true }, "formatter": { "enabled": true, "indentStyle": "space", "indentWidth": 2 } }
}
```

---

## 4. Update package.json

Add a lint script to `package.json`:

```json
"scripts": {
  ...
  "lint": "biome check --fix --error-on-warnings"
}
```

---

## 5. Install Biome VS Code Extension (Recommended)

- Search for **Biome** in the VS Code Extensions marketplace and install it.
- This provides real-time linting and formatting as you code.

---

## 6. Usage

- **Lint and fix code:**
  ```bash
  npm run lint
  ```
- Biome will only process files in the `src` directory.
- For Angular HTML templates, Biome will attempt to parse interpolation if supported. For advanced Angular template linting, use Angular's own tools.

---

## 7. Notes

- Biome does not fully support Angular template syntax in HTML files. For best results, use Angular's template linter for HTML.
- For CSS and HTML, Biome's support is basic. For advanced linting, consider using stylelint (CSS) and Prettier (HTML) as well.
- All configuration keys used are based on the official Biome documentation.

---

## 8. References
- [Biome Documentation](https://biomejs.dev/)
- [Biome VS Code Extension](https://marketplace.visualstudio.com/items?itemName=biomejs.biome)
- [Angular Template Linter](https://angular.io/guide/linter)
