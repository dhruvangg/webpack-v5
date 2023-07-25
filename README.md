# Webpack v5

## Getting Started

### Step 1: Project Setup
Assuming you have Node.js and npm (Node Package Manager) installed, Download a sample html template and initialize a package.json file by running the following command in your terminal:

```bash
npm init -y
```
### Step 2: Install Webpack
Next, let's install Webpack and its Command Line Interface (CLI) as development dependencies in your project:
```bash 
npm install webpack webpack-cli --save-dev
```
### Step 3: Create a Basic Project Structure
In your project folder, create the following directory structure:
```bash
my-webpack-project
  ├── src
  │   └── index.js
  ├── dist
  │   └── index.html
  └── webpack.config.js
```

- `src` This folder will contain your source JavaScript files and other assets.
- `dist` Webpack will output the bundled and optimized files to this folder.
- `webpack.config.js` This is the configuration file where you define how Webpack should handle your project.

### Step 4: Configure Webpack
Open/create the `webpack.config.js` file and add the following basic configuration:

```js
const path = require('path');

module.exports = {
  entry: './src/index.js',
  output: {
    path: path.resolve(__dirname, 'dist'),
    filename: 'bundle.js',
  },
};
```
This configuration tells Webpack that the entry point of your application is index.js inside the src folder, and the output bundle should be named bundle.js inside the dist folder.

### Step 5: Create a Sample JavaScript File
Now, let's create a sample JavaScript file in the src folder. Open index.js and add the following code:

```js
// src/index.js
const greeting = 'Hello, Webpack!';
console.log(greeting);
```
### Step 6: Build with Webpack
Run the following command in your terminal to build your project using Webpack:

```bash
npx webpack
```
Webpack will bundle your index.js file along with its dependencies into bundle.js inside the dist folder.

### Step 7: View the Output
Finally, open the index.html file in the dist folder with your browser and check the developer console. You should see the output "Hello, Webpack!" logged.




To bundle CSS files in Webpack, you'll need to use appropriate loaders that can process and bundle CSS files alongside your JavaScript code. Here's a step-by-step guide on how to set up Webpack to bundle CSS files:

**Step 1: Install necessary dependencies**

First, make sure you have Webpack and the required loaders installed in your project. Install the following npm packages as dev dependencies:

```bash
npm install webpack webpack-cli style-loader css-loader --save-dev
```

- `style-loader`: Injects CSS into the DOM at runtime.
- `css-loader`: Allows Webpack to process CSS files, resolve imports, and handle url() statements.

**Step 2: Create a basic Webpack configuration**

Next, create a `webpack.config.js` file at the root of your project with the following content:

```javascript
const path = require('path');

module.exports = {
  entry: './src/index.js', // Your main entry file
  output: {
    path: path.resolve(__dirname, 'dist'),
    filename: 'bundle.js',
  },
  module: {
    rules: [
      {
        test: /\.css$/,
        use: ['style-loader', 'css-loader'],
      },
    ],
  },
};
```

In this configuration, we've defined a rule for handling `.css` files using the `style-loader` and `css-loader`.

**Step 3: Create a sample CSS file**

Now, let's create a sample CSS file in your `src` folder. Create a file named `styles.css` and add some CSS rules:

```css
/* src/styles.css */
body {
  font-family: Arial, sans-serif;
  background-color: #f0f0f0;
  color: #333;
}
```

**Step 4: Link the CSS file in your entry JavaScript file**

In your `index.js` (or your main entry JavaScript file), you need to import the CSS file. This will tell Webpack to include the CSS in the bundle:

```javascript
// src/index.js
import './styles.css';

// Your other JavaScript code goes here...
```

**Step 5: Run Webpack to bundle CSS**

Now, run the following command in your terminal:

```bash
npx webpack
```

Webpack will process your JavaScript code, bundle it along with the CSS file, and create the `bundle.js` file in the `dist` folder.

**Step 6: Include the bundle in your HTML file**

Finally, create an HTML file (e.g., `index.html`) in the `dist` folder and include the generated `bundle.js`:

```html
<!DOCTYPE html>
<html>
<head>
  <title>My Webpack App</title>
</head>
<body>
  <!-- Your app content goes here -->

  <script src="bundle.js"></script>
</body>
</html>
```

Now, when you open your `index.html` file in the browser, the CSS styles from `styles.css` will be applied to the page, and your JavaScript code will be executed correctly. Your CSS is now bundled with Webpack!