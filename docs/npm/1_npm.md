---
title: npm
sidebar_position: 1
---

```ts
"workspaces": [
  "packages/*"
]

"workspaces": [
  "./packages/ui",
  "./packages/utils"
]
```

### Checking exports

```bash
npm install --save-dev @arethetypeswrong/cli
```

```json
{
  "scripts": {
    "check-exports": "attw --pack ."
    //"check-exports": "attw --pack . --ignore-rules=cjs-resolves-to-esm"
  }
}
```

```bash
npm run check-exports
```

### Exporting modules

```json
{
  "main": "./dist/cjs/index.js",
  "module": "./dist/esm/index.js",
  "types": "./dist/types/index.d.ts",
  "exports": {
    ".": {
      "require": "./dist/cjs/index.js",
      "import": "./dist/esm/index.js"
    }
  }
}
```

```bash
npm config list
npm config set registry https://registry.npmjs.org/
npm config edit
npm config edit --global
npm config delete registry
```

```bash
npm install react -D --workspace packages/ui
npm install @gnweb/utils --workspace ./packages/core
npm install @gnweb/utils --workspace ./packages/utils
```

```bash
npm run build --workspace ./packages/core
npm run build --workspace ./packages/utils
npm run build --workspace ./packages/ui
```

```bash
npm publish --access public --scope=@paramlabs
```

```json
{
      "type": "module",
      "exports": {
          ".": {
              "import": "./dist/es/index.js",
              "require": "./dist/cjs/index.js",
              "types": "./dist/types/index.d.ts"  ✅
          },
          "module2" {
              "import": "./dist/es/module2.js",
              "require": "./dist/cjs/index.js",
              "types": "./dist/types/module2.ts"  ✅
          }
      }
}
```

### Useful repos

1. [Typescript • React • Package Starter](https://github.com/TimMikeladze/typescript-react-package-starter)
2. [Component library setup with React, TypeScript and Rollup](https://dev.to/siddharthvenkatesh/component-library-setup-with-react-typescript-and-rollup-onj)
3. [tsup multi entrypoint](https://gist.github.com/ixahmedxi/972ebb37c06f2f81513e1834a9457593)

### Useful articles

1. [Matt Pocock](https://www.totaltypescript.com/how-to-create-an-npm-package)
