## Tailwind CSS Installation via the CLI

### Prerequisites

Ensure you have the latest Node.js installed. Download it from [Node.js](https://nodejs.org/).

To check your **Node.js & npm** version:

```bash
node -v  # Should show Node.js version (e.g., v18.x or higher)
npm -v   # Should show npm version (e.g., 9.x or higher)
```

### Create a New Project

Open the terminal and type this command with your project name.

```bash
mkdir my-project && cd my-project
```

Than, below the command type on terminal and open this project folder with vscode editor.

```bash
code .
```

### Initialize Node.js in the Project

```bash
npm init -y
```

This will create a `package.json` file.

### Install TailwindCSS in the Project

```bash
npm install tailwindcss @tailwindcss/cli
```

or install it as a **dev dependency** for a project:

```bash
npm install -D tailwindcss
```

## ⿻⿻⿻ Configure TailwindCSS in the Project

### Create Source & Destination Folders

#### First Folder (Source Directory)

The first folder will contain the `.css` file where TailwindCSS code will be written. For example, if the folder is named src, create a file named input.css inside it and add the following code:

Create a folder (e.g., `src`) and add an `input.css` file inside it:

```css
@import "tailwindcss";
/* When Needed To Create
@import 'tailwindcss/base';
@import 'tailwindcss/components';
@import 'tailwindcss/utilities'; */
```

This allows the file to access all necessary TailwindCSS components and where you will write TailwindCSS custom code snippets. After adding Tailwind CSS snippets and modifying styles in the `.html` file, the file will be compiled and saved in the second folder.

#### Second Folder (Destination Directory)

The second folder will contain the compiled CSS file with the actual CSS code. This final CSS file will be linked to your HTML page.

Create a folder (e.g., `dist`) with an `index.html` file inside it:

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <link href="./style.css" rel="stylesheet" />
  </head>
  <body>
    <h1 class="text-3xl font-bold underline bg-yellow-500">Hello world!</h1>
  </body>
</html>
```

## ⿻⿻⿻ Build Configuration & Run

Update `package.json` scripts:

```json
"scripts": {
    "dev": "npx @tailwindcss/cli -i ./src/input.css -o ./dist/style.css --watch",
    "build": "npx @tailwindcss/cli -i ./src/input.css -o ./dist/style.css --minify"
},
```

Run the following command in the terminal:

```bash
npm run dev   # Development mode (watch)
npm run build # Production mode (minify)
```

## ⿻⿻⿻ VS Code Editor Configuration & Plugin

### Enable Auto Suggestion and Autocomplete Plugin

Install **Tailwind CSS IntelliSense** extension in VS Code.

### Plugin Configuration

Create a `tailwind.config.js` file:

```js
module.exports = {
  content: ["./*.{html,js}"],
  theme: {
    extend: {},
  },
  plugins: [],
};
```

### VS Code Editor Settings

Create `.vscode/settings.json` and add:

```json
{
  "css.validate": false,
  "tailwindCSS.emmetCompletions": true
}
```

### Project Structure

```
tailwind-boilerplate/
├── .vscode/
│   └── settings.json
├── dist/
│   └── style.css
│   └── index.html
├── src/
│   └── input.css
├── tailwind.config.js
├── package.json
```

## 📌 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🤝 Contributing

Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.
