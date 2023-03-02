# Install and configure prettier, eslint, husky, and lint-staged with React 

## Installing ESlint

You can install and configure ESLint using this command:

```bash
npm init @eslint/config
```

It asks questions in your terminal about what kind of project you are making and what tools you are using.

After running npm init @eslint/config, you’ll have an .eslintrc.{js,yml,json} file in your directory. In it, you’ll see some rules configured like this:

```json
{
  "env": {
    "browser": true,
    "es2021": true,
    "jest": true
  },
  "extends": [
    "react-app",
    "react-app/jest",
    "plugin:import/typescript",
    "plugin:react/recommended",
    "standard-with-typescript",
    "plugin:prettier/recommended"
  ],
  "overrides": [],
  "parserOptions": {
    "ecmaVersion": "latest",
    "sourceType": "module",
    "project": "./tsconfig.json"
  },
  "plugins": ["react", "@typescript-eslint", "prettier"],
  "rules": {
    "@typescript-eslint/semi": ["error", "always"]
  }
}
```

**Add .eslintignore**

You can configure ESLint to ignore certain files and directories. it Looks like

`node_modules/`

**Run ESLint:**

```bash
npx eslint project-dir/file1.js
```

**Run ESLint --fix**
Not only does ESLint inform us of the issues, it even knows how to fix some of the more basic syntax issues like quotes and semicolons.

```bash
npx eslint project-dir/file1.js --fix
```

## Installing Prettier

You can install and configure prettier using this command:

```bash
npm install prettier eslint-config-prettier eslint-plugin-prettier --save-dev
```

**Add a .prettierrc file**

```json
{
  "tabWidth": 2,
  "useTabs": false,
  "semi": true,
  "singleQuote": false,
  "trailingComma": "all",
  "printWidth": 80
}
```

**Add .prettierignore**

You can configure Prettier to ignore certain files and directories. it Looks like

`node_modules/`

**Add prettier configuration in .eslintrc**

```json
  "extends": [
    "plugin:prettier/recommended"
  ],
  "plugins": ["prettier"],
```

## Installing husky

You can install and configure husky using this command:

```bash
npx husky-init && npm install
```
It will setup husky, modify package.json and create a sample pre-commit hook that you can edit. By default, it will run npm test when you commit.

## Installing lint-staged

You can install and configure lint-staged using this command:

```bash
npm install  -D lint-staged
```

**Modify the pre-commit hook**

npx husky set .husky/pre-commit "npx lint-staged"

pre-commit hook likes

```bash
#!/usr/bin/env sh
. "$(dirname -- "$0")/_/husky.sh"
npx lint-staged
```

**Add lint-staged in package.json**

```json
  "lint-staged": {
    "*.{js,jsx,ts,tsx}": [
      "eslint",
    ],
    "*.{js,jsx,ts,tsx,html,css,md}": "prettier --write"
  }
```
This will run eslint and prettier on your staged files whenever you attempt to create a new commit. So all your new code now will be following the eslint quality and prettier formatting rules.


------------
### Reference Link
[[1] Understanding the Modern Web Stack: ESLint][eslint]: https://dev.to/alexeagleson/understanding-the-modern-web-stack-linters-eslint-59pm

[[2] Getting Started with ESLint][eslint]: https://eslint.org/docs/latest/use/getting-started

[[3] ESLint Tutorial with Examples and All Details!][eslint]: https://www.swtestacademy.com/eslint-tutorial/

[[4] Setting up Prettier and ESlint for JS and React Apps][all]: https://medium.com/dubizzletechblog/setting-up-prettier-and-eslint-for-js-and-react-apps-bbc779d29062

[[5] Husky][husky]: https://typicode.github.io/husky/#/

[[6] ESLint with VSCode, Prettier, Husky and React For Beginners][all]: https://youtu.be/ZXW6Jn6or1w

[[7] Automate Prettier ESLint Your ReactJS App With Lint-Staged And Husky][all]: https://youtu.be/C7D4nMvbdFQ
