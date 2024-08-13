# electron-react-tailwind

- A simple boilerplate for creating desktop applications using Electron, React and Tailwind CSS.

- `npm install` to install all the dependencies.
- `npm start` to start the development server.

## To start a project similar to this boilerplate...

1. `npm init electron-app@latest my-electron-app -- --template=webpack`
2. `npm install --save-dev @babel/preset-react babel-loader @babel/core`
3. Add the following to the `webpack.rules.js` file:
```js
{
  test: /\.jsx$/,
  use: {
    loader: "babel-loader",
    options: {
      exclude: /node_modules/,
      presets: ["@babel/preset-react"],
    },
  },
},
```

4. `npm install --save react react-dom`
5. Create `index.jsx` and `App.jsx` file in the src folder and add the following code:
```jsx
// Inside index.jsx
import * as React from "react";
import { createRoot } from "react-dom/client";
import App from "./App.jsx";
import "./index.css";

const root = createRoot(document.body);
root.render(<App />);
```
```jsx
// Inside App.jsx
import React from "react";

export default function App() {
  return (
    <div className="min-h-screen max-h-full bg-zinc-950">
      <div className="font-bold text-white">App</div>
    </div>
  );
}
```

6. To display or undisplay the DevTools, uncomment or comment the following code in the `main.js` file:
```js
// Open the DevTools.
mainWindow.webContents.openDevTools();
```

7. For the built-in menu, set the following code in the `main.js` file:
```js
autoHideMenuBar: true, // hides the menu bar
```

8. `npm install --save-dev tailwindcss postcss autoprefixer`

9. `npx tailwindcss init`

10. Add the following to the `tailwind.config.js` file:
```js
content: ["./src/**/*.{html,js,jsx}"],
```

11. Add the postcss-loader in `webpack.renderer.config.js`:
```js
{
  loader: "postcss-loader",
  options: {
    postcssOptions: {
      plugins: [require("tailwindcss"), require("autoprefixer")],
    },
  },
},
```

12. Add the following to `webpack.rules.js`
```js
const path = require("path");
// ...other code
{
  test: /\.css$/,
  include: [path.resolve(__dirname, "app/src")],
  use: ["style-loader", "css-loader", "postcss-loader"],
},
```

13. Replace the `index.css` with the Tailwind CSS code:
```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

14. Import `index.css` in the `index.jsx` file:
15. Run `npm start` to start the development server.
