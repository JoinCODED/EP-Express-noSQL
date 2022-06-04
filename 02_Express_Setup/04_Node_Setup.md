## Global Setup

- Install [node](https://nodejs.org/en/download/)
  - For Mac users, install node using the [macOS installer](https://nodejs.org/dist/v12.16.3/node-v12.16.3.pkg).
  - For Windows users, install by downloading the [Windows installer](https://nodejs.org/dist/v12.16.3/node-v12.16.3-x64.msi).

## Node Setup

1. `Express` is based on `node`, so we need an environment for `node` to use `Express`. To create a `node` environment, we need a `package.json` file. To create a `package.json` we use the following command:

   ```bash
   $ npm init -y
   ```

   The `-y` will set the default options such as the name of the project and version.

   **NOTE**
   Your folder was empty, but after running the command above, we now have a `package.json` file. This file contains project-relevant data such as the name of the project, its description, the dependencies used in the project, etc. `npm` uses this information to identify the project and handle the dependencies.

2. Next, open Visual Studio Code (type `code .` in your terminal.)

   **NOTE**
   If the Terminal says “command not found” on Mac or "'code' is not recognized ..." on Windows follow the instructions below:

   1. Open Visual Studio Code.
   2. Open the Command Palette from View ❯ Command Palette
   3. Type "shell command" to find `Install 'code' command in PATH command`
   4. Install it and try the command again in the terminal (`code .`)

3. Create a file called `app.js` in your project folder. Open the `package.json` file and change the `main` property value to `app.js` as shown below:

   ```javascript
   "main": "app.js",
   ```

Now `node` knows that our main file is `app.js`.

Your `node` environment is ready.
