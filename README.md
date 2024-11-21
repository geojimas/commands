# Web useful Commands

### Init Project with Vite for Every Framework
```bash
pnpm create vite
```

### Setup Eslint new Way for React & Vite 
// eslint.config.js file
```javascript
import js from "@eslint/js" // Import base ESLint config
import globals from "globals" // Import globals for browser environment
import react from "eslint-plugin-react" // Import the React ESLint plugin
import reactHooks from "eslint-plugin-react-hooks" // Import the React Hooks ESLint plugin
import reactRefresh from "eslint-plugin-react-refresh" // Import the React Refresh plugin

// Export configuration in flat config format
export default [{
  ignores: ["dist"], // Ignore files in the dist folder

  // Configuration for JavaScript and JSX files
  files: ["**/*.{js,jsx}"], // Target all .js and .jsx files

  languageOptions: {
    ecmaVersion: 2020, // Use ECMAScript 2020 features
    globals: globals.browser, // Use browser globals (for web environment)
    parserOptions: {
      ecmaVersion: "latest", // Parse the latest ECMAScript version
      ecmaFeatures: { jsx: true }, // Enable JSX parsing
      sourceType: "module" // Set source type to ES modules
    }
  },

  settings: { react: { version: "18.3" } }, // Specify React version

  // Plugins must be imported and listed as objects
  plugins: {
    react, // Include the React ESLint plugin
    "react-hooks": reactHooks, // Include the React Hooks ESLint plugin
    "react-refresh": reactRefresh // Include the React Refresh ESLint plugin
  },

  // Rules based on the previous 'extends' configuration
  rules: {
    ...js.configs.recommended.rules, // Include ESLint's recommended base rules
    ...react.configs.recommended.rules, // Include the recommended rules for React
    ...react.configs["jsx-runtime"].rules, // Include JSX runtime rules for React 17+ (when JSX Transform is used)
    ...reactHooks.configs.recommended.rules, // Include the recommended rules for React Hooks plugin

    // Custom rules
    "react/jsx-no-target-blank": "off", // Allow usage of target="_blank" without rel="noopener noreferrer"
    "react-refresh/only-export-components": [
      "warn", { allowConstantExport: true }
    ], // Warn when components are not properly exported in React Fast Refresh
    "no-console": "warn", // Warn on console.log statements
    "semi": ["error", "never"], // Enforce no semicolons at the end of statements (fixed 'semi' rule format)
    "no-unused-vars": ["error", { vars: "all", args: "none" }], // Error on unused variables (but allow unused function arguments)
    "react/prop-types": "off", // Turn off PropTypes validation (can be redundant with TypeScript or other methods)
    "react/jsx-key": "error", // Enforce the presence of a 'key' prop in JSX elements

    // Custom Rules for React and JavaScript
    "react/jsx-no-duplicate-props": "warn", // Warn when there are duplicate props in JSX elements
    "react/jsx-closing-bracket-location": ["error", { "location": "line-aligned" }], // Enforce line-aligned closing bracket in JSX
    "react/jsx-uses-vars": "error", // Ensure variables used in JSX are properly declared
    "react-hooks/rules-of-hooks": "error", // Enforce rules of hooks in React (e.g., useEffect, useState)
    "react-hooks/exhaustive-deps": "warn", // Warn if dependency array of useEffect is incorrect or incomplete
    "no-debugger": "warn", // Warn on debugger statements (debugger should not be used in production code)
    "no-var": "error", // Disallow the usage of `var` and encourage `let` and `const`
    "prefer-const": "error", // Suggest using `const` if variables are not reassigned
    "eqeqeq": ["error", "always"], // Enforce the usage of strict equality (`===` and `!==`) over loose equality (`==` and `!=`)
    "no-trailing-spaces": "error", // Disallow trailing whitespace at the end of lines
    "curly": ["error", "all"], // Enforce the usage of curly braces for all control statements (if, for, etc.)
    "arrow-body-style": ["error", "as-needed"], // Enforce the use of the arrow function body style
    "no-magic-numbers": ["warn", { "ignore": [0, 1] }], // Warn on magic numbers but allow 0 and 1
    "prefer-destructuring": "warn", // Encourage the use of destructuring where applicable
    "no-else-return": "error", // Disallow return statements in `else` blocks
    "consistent-return": "error", // Ensure consistent return values (either always return or always don't return in functions)
    "no-shadow": "error" // Disallow variable declarations from shadowing variables declared in the outer scope
  }
}]

```
### Setup Eslint new Way for Vue & Vite 
// eslint.config.js file
```javascript
import pluginJs from '@eslint/js'; // Import the JavaScript plugin for ESLint
import pluginVue from 'eslint-plugin-vue'; // Import the Vue.js plugin for ESLint
import globals from 'globals'; // Import global variables definitions (like `window` or `document`)

export default [
  { files: ['**/*.{js,mjs,cjs,ts,vue}'] }, // Define which files should be linted by ESLint
  { languageOptions: { globals: globals.browser } }, // Specify language options, including global variables for browser environments
  pluginJs.configs.recommended, // Apply the recommended configuration from the JavaScript plugin
  ...pluginVue.configs['flat/recommended'], // Spread the recommended configuration from the Vue plugin for Vue 3
  {
    files: ['**/*.vue'], // Specify additional configuration for `.vue` files
  },
  {
    rules: {
      'vue/multi-word-component-names': 'off', // Disable the rule that requires multi-word component names in Vue
      // Additional Vue 3 specific rules
      'vue/component-api-style': ['error', ['script-setup', 'composition']], // Enforce specific API style for Vue components
      'vue/component-name-in-template-casing': ['error', 'PascalCase'], // Enforce PascalCase for component names in templates
      'vue/component-options-name-casing': ['error', 'PascalCase'], // Enforce PascalCase for component option names
      'vue/custom-event-name-casing': ['error', 'camelCase'], // Enforce camelCase for custom event names
      'vue/define-emits-declaration': ['error', 'type-based'], // Enforce type-based declarations for emits
      'vue/define-props-declaration': ['error', 'type-based'], // Enforce type-based declarations for props
      'vue/no-deprecated-slot-attribute': 'error', // Disallow the use of deprecated `slot` attribute
      'vue/no-deprecated-v-on-native-modifier': 'error', // Disallow the use of deprecated `v-on: native` modifier
      'vue/no-setup-props-destructure': 'error', // Disallow destructuring of props in setup function
      'vue/no-unused-refs': 'error', // Disallow unused template refs
      'vue/prefer-import-from-vue': 'error', // Prefer importing from Vue directly
      'vue/require-explicit-emits': 'error', // Require explicit emits declarations
      'vue/script-indent': ['error', 2, { baseIndent: 1 }], // Enforce consistent indentation for script tags
      'vue/v-on-event-hyphenation': ['error', 'always', { autofix: true }], // Enforce hyphenation for event names in templates
      'vue/valid-define-props': 'error', // Ensure props definitions are valid
      'vue/valid-v-memo': 'error' // Ensure usage of valid v-memo directive
    }
  }
];

```

### Prettier (Not Needed Anymore)
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

### Vscode Format on Save
// create ".vscode" folder and then create settings.json file
```json
{
    "eslint.validate": ["vue", "javascript", "typescript"],
    "editor.codeActionsOnSave": {
        "source.fixAll.eslint": "always",
        "source.fixAll.stylelint": "always"
    },
    "editor.quickSuggestions": {
        "other": true,
        "comments": false,
        "strings": true
    }
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
