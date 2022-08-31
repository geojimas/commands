# Web useful Commands

### Vue 3 CLI with Vite by Default
```bash
npm init vue@latest
```

### NextJS with TypeScript & TailwindCSS
```bash
npx create-next-app@latest --ts --example with-tailwindcss <project name>
```

### NuxtJS 3
#### under tsconfig.json file
```json
"compilerOptions": {
    "jsx": "preserve"
  }
```

### Vite Project Starter
```bash
npm create vite@latest
```

### Setup ESLint
```bash
npm install -D eslint
```
```bash
npm init @eslint/config
```
#### usefull eslint rules
```json
"rules": {
    "react/prop-types": "off",
    "space-before-function-paren": ["error", "never"],
    "react/react-in-jsx-scope": "off",  // suppress errors for missing 'import React' in files && 
    "react/jsx-filename-extension": [1, { "extensions": [".js", ".ts", ".tsx", ".jsx"] }] //allow jsx syntax in js files (for next.js project)
  }
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
