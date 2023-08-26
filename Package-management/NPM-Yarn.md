## NPM & Yarn

### NPM (Node Package Manager)
NPM is a package manager for JavaScript, initially created for the Node.js runtime environment but now widely used for front-end development as well. NPM provides an online registry where developers can publish and share open-source JavaScript packages. Through the NPM CLI (Command-Line Interface), developers can easily install, update, and manage these packages in their projects.

**Key Features of NPM:**
- **Package Registry**: A vast collection of reusable code packages.
- **Dependency Management**: Manages the versions of the packages your project depends on.
- **Scripts**: Allows the definition of shortcut scripts to automate repetitive tasks.
- **Versioning**: Supports semantic versioning, enabling developers to specify which versions of a dependency their project is compatible with.

The `package.json` file serves as the manifest for a project, specifying its dependencies, scripts, and other metadata. Dependencies are installed into a `node_modules` directory within the project.

### Yarn
Yarn is an alternative package manager to NPM, developed by Facebook. While it also uses the NPM registry for package distribution, Yarn introduced several improvements to the NPM client, including:

**Key Features of Yarn:**
- **Performance**: Faster package installation through parallelization and caching.
- **Deterministic Installs**: Ensures that installing dependencies produces the exact same file structure across all systems, addressed through a `yarn.lock` file.
- **Workspaces**: Native support for monorepo (monolithic repository) management.
- **Improved Security**: Provides additional security features, like license checks and checksum verification.

### Differences between NPM and Yarn
1. **Performance**: Yarn was initially much faster than NPM, although NPM has made significant improvements in speed since then.
2. **Lock File**: While both use a lock file (`package-lock.json` for NPM and `yarn.lock` for Yarn), they are implemented differently. Yarn's `yarn.lock` file tends to be more accurate in ensuring deterministic installs.
3. **CLI Commands**: Although similar, the CLI commands can differ slightly. For example, installing a package globally in NPM is `npm install -g <package_name>` while in Yarn, it is `yarn global add <package_name>`.
4. **Monorepo Support**: Yarn provides native workspaces for better monorepo support, although NPM introduced similar features in later versions.
5. **User Interface**: Yarn offers a cleaner and more concise console interface compared to NPM.
