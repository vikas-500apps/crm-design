# CRM Design

This template should help get you started developing with Vue 3 in Vite.

## Recommended IDE Setup

[VSCode](https://code.visualstudio.com/) + [Volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar) (and disable Vetur).

## Customize configuration

See [Vite Configuration Reference](https://vite.dev/config/).

## Project Setup

```sh
npm install
```

Frappe UI provides a set of components and utilities for rapid UI development.
Components are built using Vue 3 and Tailwind. Along with components, there are
directives and utilities that make UI development easier.

## Links

- [Documentation](https://frappeui.com)
- [Frappe UI Starter Boilerplate](https://github.com/netchampfaris/frappe-ui-starter)
- [Community](https://github.com/frappe/frappe-ui/discussions)

## Installation

```sh
npm install frappe-ui
# or
yarn add frappe-ui
```

In your `tailwind.config.js` file, include the frappe-ui preset:

```js
import tailwindConfig from "frappe-ui/src/utils/tailwind.config";

module.exports = {
  presets: [tailwindConfig],
  content: [
    "./index.html",
    "./src/**/*.{vue,js,ts,jsx,tsx}",
    "./node_modules/frappe-ui/src/components/**/*.{vue,js,ts,jsx,tsx}",
    "../node_modules/frappe-ui/src/components/**/*.{vue,js,ts,jsx,tsx}",
  ],
  theme: {
    extend: {},
  },
  plugins: [],
};
```

In your `vite.config.js` file, include the frappe-ui optimizeDeps for `FeatherIcon`:

```js
export default defineConfig({
  optimizeDeps: {
    include: ["frappe-ui > feather-icons", "showdown", "engine.io-client"],
  },
});
```

### Compile and Hot-Reload for Development

```sh
npm run dev
```

### Compile and Minify for Production

```sh
npm run build
```

### Lint with [ESLint](https://eslint.org/)

```sh
npm run lint
```
