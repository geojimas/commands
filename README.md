# Web useful Commands

### Vue 3 CLI
```bash
npm init vue@latest
```

### NextJS with TypeScript & TailwindCSS
```bash
npx create-next-app --example with-tailwindcss <project name>
```

### Prettier
 ```json
 {
  "printWidth": 100,
  "tabWidth": 2,
  "useTabs": false,
  "semi": false,
  "singleQuote": true,
  "trailingComma": "none",
  "bracketSpacing": true,
  "bracketSameLine": true,
  "jsxBracketSameLine": false,
  "arrowParens": "avoid",
  "proseWrap": "always"
}
```

### Netlify redirects: netlify.toml
```shell

[build.environment]
  # bypass npm auto install
  NPM_FLAGS = "--version"
  NODE_VERSION = "16"

[build]
  publish = "dist"
  command = "npm install && npm run build"

[[redirects]]
  from = "/*"
  to = "/index.html"
  status = 200

[[headers]]
  for = "/manifest.webmanifest"
  [headers.values]
    Content-Type = "application/manifest+json"

```
