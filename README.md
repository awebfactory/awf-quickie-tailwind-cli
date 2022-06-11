# Tailwind CLI Environment

- The whole team needs to be able to run the html prototype file in VSCode with Live Server
- So the html file needs a kind of public directory, which includes assets; and so tailwind output css file needs to go where that html file can see it.
- What I came up with, based on review of:
  - [Installation: Tailwind CLI](https://tailwindcss.com/docs/installation)
  - [Install Tailwind CSS v3 - CDN vs CLI vs PostCSS](https://youtu.be/h9Zun41-Ozc)

## Usage

[![Open in StackBlitz](https://developer.stackblitz.com/img/open_in_stackblitz.svg)](https://stackblitz.com/github/awebfactory/awf-quickie-tailwind-cli/tree/daisyui?file=README.md&start)

### Install dependencies in package.json

```bash
npm install
```

### Run watch script

```bash
npm run watch
```

- Tailwind output goes to `./html/css/style.css`

### Work in VSCode

```bash
code .
```

- Then edit `./html/index.html`
  - It is looking at `./html/css/style.css`
- View in Live Server or wherever to visualize changes

### Or run build if you're just going to look without making changes

```bash
npm run build
```

## Created roughly like this

### Install Tailwind CSS

```bash
npm init
npm install -D tailwindcss
npx tailwindcss init
```

### Configure template paths in `tailwind.config.js`

```json
module.exports = {
  content: ["./html/**/*.{html,js}"],
  theme: {
    extend: {},
  },
  plugins: [],
}
```

### Add the Tailwind directives to your CSS (`./tailwind.css`)

```js
@tailwind base;
@tailwind components;
@tailwind utilities;
```

### Add watch and build scripts to `package.json`

```json
  "scripts": {
    "watch": "tailwindcss -i ./tailwind.css -o ./html/css/style.css --watch",
    "build": "tailwindcss -i ./tailwind.css -o ./html/css/style.css"
  },
```

### Start using Tailwind in your HTML

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <link href="css/output.css" rel="stylesheet" />
  </head>
  <body>
    <h1 class="text-3xl font-bold underline">Hello world!</h1>
  </body>
</html>
```

## Run watch script

```bash
npm run watch
```

## Run build

```bash
npm run build
```
