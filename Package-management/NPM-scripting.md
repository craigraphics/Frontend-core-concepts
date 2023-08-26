## NPM Scripting?

NPM (Node Package Manager) scripting refers to the automation of tasks using the `scripts` property in the `package.json` file of a Node.js project. These scripts are essentially shortcuts that you can define to perform tasks like building, testing, deploying, or any other task relevant to your project. NPM scripting is particularly valuable in front-end development for task automation, build processes, and package management. 

### Where to Create Scripts?

Scripts are defined within the `package.json` file, which is located at the root directory of a Node.js project. The `scripts` property is an object where each key is the name of the script, and the value is the command that the script runs.

Example:
```json
{
  "name": "my-project",
  "version": "1.0.0",
  "scripts": {
    "start": "node index.js",
    "test": "jest",
    "build": "webpack"
  }
}
```

### Why Create Scripts?

1. **Simplification**: Condenses complex or verbose shell commands into a single, easy-to-remember command.
  
2. **Standardization**: Ensures that all developers on a team use the same set of commands, minimizing inconsistencies.
  
3. **Automation**: Allows the automation of repetitive tasks like minification, compilation, unit testing, etc.

4. **Dependency Management**: Easily specify project-level dependencies that should be installed before running certain tasks.

### How to Add Scripts?

You add scripts by editing the `package.json` file manually or through the command line. To add them manually, you open the `package.json` file and add key-value pairs inside the `scripts` object.

Example:
```json
"scripts": {
  "start": "node index.js",
  "new-script": "command for new script"
}
```

### What are Script Hooks?

Script hooks are special predefined names for scripts that get automatically triggered by NPM before or after specific events. For example, the `preinstall` script runs before the package is installed, and the `postinstall` script runs after it's installed. You can also set hooks for custom scripts.

Example:
```json
"scripts": {
  "prestart": "echo 'Preparing to start the app'",
  "start": "node index.js",
  "poststart": "echo 'App started successfully'"
}
```

In this example, running `npm start` would first trigger the `prestart` script, then the `start` script, and finally the `poststart` script.
