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
