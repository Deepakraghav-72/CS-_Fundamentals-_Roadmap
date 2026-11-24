# Git and Development Tools – Complete Notes

## 1. What is Git?

**Definition:** Git is a free and open-source distributed version control system used to track changes in source code.

Simple words: Git ki help se hum apne code ke different versions track, manage aur restore kar sakte hain.

### Features of Git

- Tracks code changes.
- Maintains project history.
- Supports branching and merging.
- Enables team collaboration.
- Allows recovery of previous versions.
- Works locally without an internet connection.

### Why Git is Important?

1. Code history maintain karna.
2. Multiple developers ke saath kaam karna.
3. Changes compare karna.
4. Previous code restore karna.
5. Different features independently develop karna.

---

## 2. What is Version Control System (VCS)?

**Definition:** A Version Control System is a tool that records and manages changes made to files over time.

### Types of VCS

**1. Local Version Control System**

- Changes local computer par track hote hain.
- Example: RCS.

**2. Centralized Version Control System (CVCS)**

- Ek central server par repository maintain hoti hai.
- Example: SVN, Perforce.

**3. Distributed Version Control System (DVCS)**

- Har developer ke paas complete repository history ki copy ho sakti hai.
- Example: Git, Mercurial.

### Comparison

| Type        | Storage                            |
| ----------- | ---------------------------------- |
| Local       | Local computer                     |
| Centralized | Central server                     |
| Distributed | Local copies + remote repositories |

---

## 3. Git vs GitHub

### Git

Git is a version control system used to track and manage code changes.

### GitHub

GitHub is a cloud-based platform used to host Git repositories and collaborate with developers.

### Difference

| Git                       | GitHub                             |
| ------------------------- | ---------------------------------- |
| Version control tool      | Hosting and collaboration platform |
| Works locally             | Provides remote hosting            |
| Tracks code history       | Hosts repositories                 |
| Command-line tool         | Website and collaboration services |
| Created by Linus Torvalds | Launched by GitHub in 2008         |

### Other Git Hosting Platforms

- GitLab.
- Bitbucket.
- Codeberg.

---

## 4. Important Git Terminology

**Repository (Repo):** A storage location containing project files and their version history.

**Working Directory:** The directory where you modify project files.

**Staging Area:** A place where changes are prepared before committing.

**Commit:** A saved snapshot of staged changes.

**Branch:** An independent line of development.

**Merge:** Combining changes from different branches.

**Clone:** Copying a remote repository to a local computer.

**Fork:** Creating your own GitHub-side copy of another user's repository.

**Remote:** A reference to a repository hosted elsewhere.

**HEAD:** A reference to the currently checked-out commit (normally through the current branch).

**Origin:** The conventional default name of a remote repository.

---

## 5. Git Installation and Configuration

Check Git installation:

```bash
git --version
```

Configure username:

```bash
git config --global user.name "Your Name"
```

Configure email:

```bash
git config --global user.email "your@email.com"
```

Check configuration:

```bash
git config --list
```

Check a specific configuration:

```bash
git config user.name
git config user.email
```

Important: Git commit identity is separate from your GitHub login authentication.

---

## 6. Git Repository

A repository stores project files and their version history.

### Create a New Repository

```bash
git init
```

This initializes a Git repository in the current directory.

### Check Repository Status

```bash
git status
```

### Clone Existing Repository

```bash
git clone https://github.com/username/project.git
```

### Difference Between git init and git clone

| git init                                  | git clone                     |
| ----------------------------------------- | ----------------------------- |
| Creates a new local repository            | Copies an existing repository |
| Starts without existing project history   | Includes existing history     |
| Does not automatically configure a remote | Usually configures origin     |

---

## 7. Git Working Areas

Git has three important local areas:

**1. Working Directory**

- Where files are modified.
- Changes are not necessarily staged.

**2. Staging Area**

- Contains selected changes ready for commit.
- Created using git add.

**3. Repository**

- Stores committed snapshots and history.

### Git Workflow

Working Directory → Staging Area → Local Repository → Remote Repository

### Important Commands

```bash
git status
git add .
git commit -m "Add login feature"
git push origin main
```

---

## 8. Important Git Commands

### 1. git init

Creates a new local repository.

```bash
git init
```

### 2. git status

Displays the current state of files.

```bash
git status
```

### 3. git add

Adds changes to the staging area.

```bash
git add index.html
git add .
```

### 4. git commit

Records staged changes in repository history.

```bash
git commit -m "Initial commit"
```

### 5. git log

Displays commit history.

```bash
git log
git log --oneline
git log --graph --oneline --all
```

### 6. git diff

Shows differences between versions or working states.

```bash
git diff
git diff --staged
```

### 7. git show

Displays information about a commit.

```bash
git show
```

### 8. git restore

Restores file content.

```bash
git restore index.html
```

Unstages a file:

```bash
git restore --staged index.html
```

Warning: Restoring an unstaged file can discard its uncommitted changes.

### 9. git rm

Removes a tracked file.

```bash
git rm file.txt
```

### 10. git mv

Renames or moves a tracked file.

```bash
git mv old.txt new.txt
```

---

## 9. Git Branching

A branch is an independent line of development.

Branches allow developers to work on different features without directly changing the main development branch.

### Important Branch Commands

Create branch:

```bash
git branch feature-login
```

List branches:

```bash
git branch
```

Switch branch:

```bash
git switch feature-login
```

Create and switch together:

```bash
git switch -c feature-login
```

Delete branch:

```bash
git branch -d feature-login
```

Force delete branch:

```bash
git branch -D feature-login
```

Rename current branch:

```bash
git branch -m new-name
```

### Example Workflow

```bash
git switch -c feature-navbar

git add .
git commit -m "Create navbar"

git switch main
git merge feature-navbar
```

---

## 10. Git Merge

Merge combines changes from one branch into another.

### Example

```bash
git switch main
git merge feature-login
```

### Types of Merge

**1. Fast-Forward Merge**

When the target branch has not diverged, Git moves its branch pointer forward.

**2. Three-Way Merge**

Git combines changes using a common ancestor and the two branch tips.

### Merge Conflict

A merge conflict occurs when Git cannot automatically combine changes.

Example:

```text
<<<<<<< HEAD
Welcome User
=======
Welcome Admin
>>>>>>> feature-login
```

### How to Resolve Merge Conflict

1. Open the conflicted file.
2. Understand both changes.
3. Select or combine the required code.
4. Remove conflict markers.
5. Save the file.
6. Stage the resolved file.
7. Complete the merge commit if required.

```bash
git add .
git commit
```

---

## 11. Git Rebase

Rebase moves or replays commits onto another base commit.

Example:

```bash
git switch feature-login
git rebase main
```

### Merge vs Rebase

| Merge                                | Rebase                              |
| ------------------------------------ | ----------------------------------- |
| Combines branch histories            | Replays commits onto a new base     |
| Can create merge commit              | Usually creates linear history      |
| Preserves existing commit identities | Replayed commits get new hashes     |
| Good for integration                 | Useful for cleaning feature history |

Important: Avoid rebasing shared public history unless the team agrees, because it rewrites commit history.

---

## 12. Git Remote and GitHub

A remote connects your local repository with another repository.

### Add Remote

```bash
git remote add origin https://github.com/username/project.git
```

### Check Remotes

```bash
git remote -v
```

### Change Remote URL

```bash
git remote set-url origin https://github.com/username/project.git
```

### Remove Remote

```bash
git remote remove origin
```

### Push Code

```bash
git push origin main
```

### First Push with Upstream

```bash
git push -u origin main
```

### Pull Changes

```bash
git pull origin main
```

### Fetch Changes

```bash
git fetch origin
```

### Difference Between Fetch and Pull

| Fetch                                        | Pull                                  |
| -------------------------------------------- | ------------------------------------- |
| Downloads remote updates                     | Fetches and integrates remote updates |
| Does not update current branch automatically | Integrates into current branch        |
| Safer for inspecting updates first           | Convenient for updating local work    |

---

## 13. Git Pull vs Git Push

**git push:** Sends local commits to a remote repository.

**git pull:** Fetches remote changes and integrates them into the current branch.

Example:

```bash
git pull origin main
git push origin main
```

---

## 14. Git Stash

Git Stash temporarily stores uncommitted changes so you can work on something else.

### Commands

Save changes:

```bash
git stash
```

Save with a message:

```bash
git stash push -m "Work in progress"
```

List stashes:

```bash
git stash list
```

Apply latest stash:

```bash
git stash apply
```

Apply and remove latest stash:

```bash
git stash pop
```

Delete stash:

```bash
git stash drop
```

Delete all stashes:

```bash
git stash clear
```

Important: Stash generally stores tracked-file changes; use `-u` to include untracked files.

```bash
git stash push -u
```

---

## 15. Git Reset vs Git Revert

### Git Reset

Moves the current branch pointer to another commit and can change staging/working files.

Types:

**Soft Reset**

```bash
git reset --soft HEAD~1
```

Removes the last commit but keeps changes staged.

**Mixed Reset**

```bash
git reset HEAD~1
```

Removes the last commit and unstages changes, while keeping working files.

**Hard Reset**

```bash
git reset --hard HEAD~1
```

Removes the last commit and discards corresponding changes from the index and working tree.

### Git Revert

Creates a new commit that reverses changes introduced by an earlier commit.

```bash
git revert HEAD
```

### Reset vs Revert

| Reset                       | Revert                     |
| --------------------------- | -------------------------- |
| Moves branch pointer        | Creates a reversing commit |
| Can rewrite local history   | Preserves existing history |
| Useful for local cleanup    | Useful for shared history  |
| Hard reset can discard work | Safer for shared branches  |

---

## 16. Git Cherry-Pick

Cherry-pick applies changes introduced by a specific commit onto the current branch.

```bash
git cherry-pick commit-id
```

Useful when you need one specific commit without merging the entire branch.

---

## 17. Git Tags

Tags mark important points in repository history, commonly releases.

### Commands

```bash
git tag
git tag v1.0.0
git tag -a v1.0.0 -m "Version 1.0"
git push origin v1.0.0
git push origin --tags
git tag -d v1.0.0
```

---

## 18. .gitignore File

`.gitignore` tells Git which untracked files or paths to ignore.

Example:

```gitignore
node_modules/
.env
dist/
build/
.DS_Store
*.log
```

### Why .gitignore is Important?

- Avoids uploading unnecessary files.
- Keeps repository clean.
- Helps protect sensitive configuration files.
- Reduces repository size.

Important: `.gitignore` does not automatically stop tracking files that Git already tracks.

For an already tracked file:

```bash
git rm --cached .env
git commit -m "Stop tracking env file"
```

Never upload passwords, API keys or database credentials to GitHub.

---

## 19. GitHub Fundamentals

GitHub is a platform for hosting Git repositories and collaborating on software projects.

### Important Features

**1. Repository:** Stores project files and history.

**2. README.md:** Explains the project.

**3. Issues:** Tracks bugs, tasks and feature requests.

**4. Pull Request (PR):** Proposes changes from one branch or fork to another.

**5. Fork:** Creates a GitHub-side copy of a repository.

**6. Actions:** Automates workflows such as testing and deployment.

**7. Releases:** Publishes software versions.

**8. Discussions:** Supports community conversations.

### Pull Request Workflow

1. Create a feature branch or fork.
2. Make changes.
3. Commit and push changes.
4. Open a Pull Request.
5. Review the code.
6. Resolve requested changes.
7. Merge the Pull Request.

### Fork vs Clone

| Fork                                      | Clone                        |
| ----------------------------------------- | ---------------------------- |
| Creates remote copy on GitHub             | Creates local copy           |
| Useful for contributing to other projects | Useful for local development |
| Performed on hosting platform             | Performed using Git          |

---

## 20. GitHub Authentication

GitHub supports different authentication methods.

### 1. HTTPS Authentication

Uses secure HTTPS connections.

For Git operations, GitHub supports Personal Access Tokens instead of account passwords.

### 2. SSH Authentication

Uses an SSH key pair.

- Public key is added to GitHub.
- Private key remains on your computer.

Check SSH connection:

```bash
ssh -T git@github.com
```

### 3. Git Credential Manager

Helps securely manage Git credentials and authentication.

---

# DEVELOPMENT TOOLS

## 21. What are Development Tools?

Development Tools are software applications that help developers write, test, debug, manage and deploy applications.

### Categories

1. Code Editors.
2. IDEs.
3. Version Control Tools.
4. Terminal Tools.
5. Debugging Tools.
6. Testing Tools.
7. Package Managers.
8. API Testing Tools.
9. Database Tools.
10. Deployment Tools.

---

## 22. Code Editor vs IDE

### Code Editor

A lightweight application primarily used to write and edit source code.

Examples:

- Visual Studio Code.
- Sublime Text.
- Notepad++.

### IDE

IDE stands for Integrated Development Environment.

It provides an integrated environment for coding, debugging, building and other development tasks.

Examples:

- Visual Studio.
- IntelliJ IDEA.
- PyCharm.
- Eclipse.

### Difference

| Code Editor                        | IDE                              |
| ---------------------------------- | -------------------------------- |
| Mainly code editing                | Complete development environment |
| Usually lightweight                | Often more feature-rich          |
| Uses extensions for extra features | Often includes integrated tools  |
| Example: VS Code                   | Example: IntelliJ IDEA           |

Note: VS Code is technically a source-code editor with powerful IDE-like capabilities through extensions.

---

## 23. Visual Studio Code (VS Code)

VS Code is a free source-code editor developed by Microsoft.

### Important Features

- Syntax highlighting.
- IntelliSense.
- Extensions.
- Integrated terminal.
- Debugging support.
- Git integration.
- Search and replace.
- Multiple file editing.

### Important VS Code Shortcuts

| Shortcut           | Function        |
| ------------------ | --------------- |
| Ctrl + Shift + P   | Command Palette |
| Ctrl + P           | Quick Open      |
| Ctrl + Shift + E   | Explorer        |
| Ctrl + Shift + F   | Search          |
| Ctrl + `           | Open Terminal   |
| Ctrl + S           | Save            |
| Ctrl + Shift + N   | New Window      |
| Alt + Up/Down      | Move Line       |
| Shift + Alt + Down | Copy Line Down  |
| Ctrl + /           | Toggle Comment  |
| F2                 | Rename Symbol   |
| F5                 | Start Debugging |

### Important VS Code Features

**IntelliSense:** Provides code suggestions and auto-completion.

**Extensions:** Add extra functionality to VS Code.

**Integrated Terminal:** Allows commands to run inside VS Code.

**Debugger:** Helps identify and fix code errors.

---

## 24. Terminal and Command Line

A terminal is an interface used to interact with the operating system through commands.

### Important Terms

**CLI:** Command Line Interface.

**GUI:** Graphical User Interface.

**Shell:** A program that interprets and executes commands.

**Terminal Emulator:** An application that provides access to a shell.

### Windows Tools

- Command Prompt (CMD).
- PowerShell.
- Windows Terminal.
- Git Bash.

### Basic Windows Commands

```cmd
dir
cd folder-name
cd ..
mkdir project
rmdir folder-name
cls
echo Hello
type file.txt
```

### Basic Git Bash / Unix Commands

```bash
pwd
ls
cd folder-name
cd ..
mkdir project
touch index.html
rm file.txt
clear
cat file.txt
```

### Important Difference

| CMD                               | PowerShell                             |
| --------------------------------- | -------------------------------------- |
| Traditional Windows command shell | Modern task automation shell           |
| Text-based commands               | Commands and objects                   |
| Uses commands such as dir         | Supports cmdlets such as Get-ChildItem |

---

## 25. Node.js and npm

### Node.js

Node.js is an open-source JavaScript runtime built on Chrome's V8 JavaScript engine.

It allows JavaScript to run outside the browser.

### npm

npm commonly refers to the default package manager used with Node.js.

It is used to install and manage JavaScript packages and project dependencies.

### Important npm Commands

Check version:

```bash
node -v
npm -v
```

Initialize project:

```bash
npm init
```

Initialize with default settings:

```bash
npm init -y
```

Install package:

```bash
npm install express
```

Install development dependency:

```bash
npm install -D nodemon
```

Install all dependencies:

```bash
npm install
```

Uninstall package:

```bash
npm uninstall express
```

Run script:

```bash
npm run dev
```

### package.json

Stores project metadata, scripts and dependency declarations.

Example:

```json
{
  "name": "my-project",
  "version": "1.0.0",
  "scripts": {
    "start": "node server.js",
    "dev": "nodemon server.js"
  },
  "dependencies": {
    "express": "^5.0.0"
  }
}
```

### package-lock.json

Records the resolved dependency tree to support reproducible installations.

### node_modules

Directory containing installed project packages and their dependencies.

Important: Usually `node_modules` should be included in `.gitignore`.

---

## 26. Package Managers

Package Managers install, update and manage software dependencies.

### Common JavaScript Package Managers

1. npm.
2. Yarn.
3. pnpm.

### Comparison

| npm                    | Yarn                | pnpm                                                     |
| ---------------------- | ------------------- | -------------------------------------------------------- |
| Default with Node.js   | Alternative manager | Alternative manager                                      |
| Uses package-lock.json | Uses yarn.lock      | Uses pnpm-lock.yaml                                      |
| Installs packages      | Installs packages   | Efficient disk usage through content-addressable storage |

---

## 27. Browser Developer Tools (DevTools)

Browser DevTools are built-in tools used to inspect, debug and analyze websites.

Examples:

- Chrome DevTools.
- Firefox Developer Tools.
- Edge DevTools.

### Important Tabs

**1. Elements**

- Inspect HTML.
- Modify DOM.
- Inspect CSS.

**2. Console**

- View JavaScript errors.
- Execute JavaScript.
- Debug code.

**3. Sources**

- Inspect source files.
- Set breakpoints.
- Debug JavaScript.

**4. Network**

- Monitor HTTP requests.
- Inspect API responses.
- Check loading time.
- Identify failed requests.

**5. Application**

- Inspect Local Storage.
- Inspect Session Storage.
- Inspect cookies.
- Inspect service workers.

**6. Performance**

- Analyze runtime performance.
- Identify performance bottlenecks.

**7. Memory**

- Analyze memory usage.
- Investigate memory leaks.

### Important Shortcuts

```text
F12 = Open DevTools
Ctrl + Shift + I = Open DevTools
Ctrl + Shift + J = Open Console (Chrome)
Ctrl + Shift + C = Inspect Element
```

---

## 28. API Development and Testing Tools

API tools help developers create, test and debug API requests.

### Postman

Postman is a platform used to develop, test and document APIs.

Features:

- Send HTTP requests.
- Test API responses.
- Manage environments.
- Organize collections.
- Automate API tests.

### Thunder Client

A lightweight API testing extension for VS Code.

### cURL

A command-line tool used to transfer data using different network protocols.

Example:

```bash
curl https://jsonplaceholder.typicode.com/users
```

### API Testing Example

```http
GET https://api.example.com/users
```

Check:

- Status code.
- Response body.
- Response headers.
- Response time.

---

## 29. Database Development Tools

Database tools help developers create, inspect and manage databases.

### MongoDB Compass

A graphical interface for working with MongoDB databases.

Features:

- View databases.
- Browse collections.
- Insert and update documents.
- Run queries.
- Analyze schemas.

### Other Database Tools

| Tool            | Purpose                   |
| --------------- | ------------------------- |
| MongoDB Compass | MongoDB GUI               |
| MySQL Workbench | MySQL development         |
| pgAdmin         | PostgreSQL management     |
| DBeaver         | Multi-database management |

---

## 30. Debugging Tools

Debugging tools help developers identify and fix errors.

### Common Debugging Features

1. Breakpoints.
2. Step Into.
3. Step Over.
4. Step Out.
5. Watch Variables.
6. Call Stack.
7. Debug Console.

### Important Terms

**Breakpoint:** Pauses code execution at a specific location.

**Step Into:** Enters a function call.

**Step Over:** Executes a function call without entering it.

**Step Out:** Completes the current function and returns to its caller.

**Call Stack:** Shows the sequence of active function calls.

**Watch:** Monitors selected variables or expressions.

---

## 31. Testing and Automation Tools

### Jest

JavaScript testing framework used for unit and integration testing.

### Vitest

A testing framework commonly used with modern frontend projects.

### Cypress

A browser-based end-to-end testing tool.

### Playwright

An automation framework for browser testing.

### Selenium

A browser automation framework.

### Testing Categories

| Category            | Purpose                    |
| ------------------- | -------------------------- |
| Unit Testing        | Individual functions       |
| Integration Testing | Connected components       |
| E2E Testing         | Complete user workflows    |
| API Testing         | API behavior and responses |

---

## 32. Code Quality and Formatting Tools

### ESLint

Analyzes JavaScript and TypeScript code to identify potential errors and enforce coding rules.

### Prettier

Automatically formats code according to defined formatting rules.

### Husky

Helps run Git hooks, such as linting or testing before commits.

### Git Hooks

Scripts that execute automatically at specific Git events.

Examples:

- pre-commit.
- commit-msg.
- pre-push.

---

## 33. Build Tools and Bundlers

Build tools help transform, bundle and optimize application code.

### Vite

A modern frontend build tool that provides fast development and production builds.

### Webpack

A module bundler that combines application modules and assets into optimized bundles.

### Babel

A JavaScript compiler commonly used to transform modern JavaScript syntax for compatibility with target environments.

### TypeScript

A programming language built on JavaScript that adds static type-checking features.

### Comparison

| Tool       | Main Purpose                    |
| ---------- | ------------------------------- |
| Vite       | Frontend development and builds |
| Webpack    | Module bundling                 |
| Babel      | JavaScript transformation       |
| TypeScript | Static type checking            |

---

## 34. Deployment and DevOps Tools

### GitHub Actions

Automates workflows such as testing, building and deployment.

### Docker

A platform for packaging applications and their dependencies into containers.

### Jenkins

An automation server used for CI/CD pipelines.

### Kubernetes

A container orchestration platform used to manage containerized applications.

### Cloud Platforms

- AWS.
- Microsoft Azure.
- Google Cloud.

---

## 35. Environment Variables

Environment variables store configuration values outside application source code.

Examples:

- Database URL.
- API keys.
- Application port.
- Authentication secrets.

### .env Example

```env
PORT=5000
MONGO_URI=mongodb://localhost:27017/myapp
JWT_SECRET=your-secret
```

Node.js example:

```javascript
console.log(process.env.PORT);
```

With dotenv:

```javascript
require("dotenv").config();
```

Important:

- Never upload `.env` containing secrets.
- Add `.env` to `.gitignore`.
- Use environment variables for production configuration.
- Never expose private server secrets in frontend code.

---

## 36. Software Development Workflow

A typical development workflow:

1. Understand project requirements.
2. Create project repository.
3. Set up development environment.
4. Create feature branch.
5. Write code.
6. Test functionality.
7. Debug errors.
8. Commit changes.
9. Push changes to GitHub.
10. Create Pull Request.
11. Review and merge code.
12. Deploy application.
13. Monitor application.

### Example MERN Workflow

```text
Requirement
    ↓
VS Code
    ↓
React Frontend
    ↓
Node.js + Express Backend
    ↓
MongoDB
    ↓
Testing with Postman
    ↓
Git Commit
    ↓
GitHub Push
    ↓
Deployment
```

---

# 37. Important Git Interview Questions

**Q1. What is Git?**

Git is a distributed version control system used to track and manage source code changes.

**Q2. What is GitHub?**

GitHub is a platform used to host Git repositories and collaborate on projects.

**Q3. What is a repository?**

A repository stores project files and version history.

**Q4. What is a commit?**

A commit is a snapshot of staged changes saved in repository history.

**Q5. What is a branch?**

A branch is an independent line of development.

**Q6. What is the difference between git fetch and git pull?**

Fetch downloads remote changes without integrating them into the current branch, whereas pull fetches and integrates them.

**Q7. What is git merge?**

Git merge combines changes from different branches.

**Q8. What is a merge conflict?**

A merge conflict occurs when Git cannot automatically combine changes.

**Q9. What is git stash?**

Git stash temporarily saves uncommitted changes.

**Q10. What is git rebase?**

Rebase replays commits onto a new base commit.

**Q11. What is git reset?**

Git reset moves the current branch pointer and can modify staging and working files.

**Q12. What is git revert?**

Git revert creates a new commit that reverses an earlier commit's changes.

**Q13. What is .gitignore?**

It specifies intentionally untracked files and paths Git should ignore.

**Q14. What is HEAD?**

HEAD identifies the currently checked-out commit, usually through the current branch.

**Q15. What is the difference between fork and clone?**

Fork creates a remote copy on a hosting platform, whereas clone creates a local copy.

**Q16. What is a Pull Request?**

A Pull Request proposes changes for review and merging into another branch.

**Q17. What is cherry-pick?**

Cherry-pick applies changes from a specific commit onto the current branch.

**Q18. What is a Git tag?**

A tag marks a specific commit, commonly for a software release.

**Q19. What is a remote repository?**

A remote repository is another repository hosted at a location such as GitHub.

**Q20. What is origin?**

Origin is the conventional default name of a Git remote.

---

# 38. Important Development Tools Interview Questions

**Q21. What is a Code Editor?**

A code editor is an application used to write and edit source code.

**Q22. What is an IDE?**

An IDE is an integrated development environment that combines tools for coding, debugging and building applications.

**Q23. What is VS Code?**

VS Code is a source-code editor developed by Microsoft.

**Q24. What is a Terminal?**

A terminal provides an interface for interacting with a command-line shell.

**Q25. What is CLI?**

CLI stands for Command Line Interface.

**Q26. What is Node.js?**

Node.js is a JavaScript runtime built on Chrome's V8 engine.

**Q27. What is npm?**

npm is a package manager used to install and manage JavaScript dependencies.

**Q28. What is package.json?**

package.json stores project metadata, scripts and dependency information.

**Q29. What is node_modules?**

It is the directory containing installed project dependencies.

**Q30. What is package-lock.json?**

It records the resolved dependency tree for more consistent installations.

**Q31. What are Browser DevTools?**

Browser DevTools are tools used to inspect, debug and analyze web applications.

**Q32. What is Postman?**

Postman is a platform used for API development and testing.

**Q33. What is MongoDB Compass?**

MongoDB Compass is a graphical interface for managing MongoDB databases.

**Q34. What is ESLint?**

ESLint analyzes JavaScript and TypeScript code for potential problems and coding-rule violations.

**Q35. What is Prettier?**

Prettier is an automated code formatter.

**Q36. What is Docker?**

Docker is a platform used to build and run applications in containers.

**Q37. What is Vite?**

Vite is a frontend build tool that provides fast development and production builds.

**Q38. What is CI/CD?**

CI/CD automates code integration, testing and software delivery or deployment.

**Q39. What is an Environment Variable?**

An environment variable stores configuration information outside application source code.

**Q40. What is Debugging?**

Debugging is the process of finding and fixing software errors.

---

# 39. Quick Revision

- Git = Distributed Version Control System.
- GitHub = Repository hosting platform.
- VCS = Version Control System.
- Repository = Project + Version History.
- Commit = Saved Snapshot.
- Branch = Independent development line.
- Merge = Combine branches.
- Rebase = Replay commits onto another base.
- Clone = Copy remote repository locally.
- Fork = Create remote copy.
- Fetch = Download remote updates.
- Pull = Fetch + Integrate.
- Push = Upload local commits.
- Stash = Temporarily save changes.
- Reset = Move branch pointer.
- Revert = Create reversing commit.
- Cherry-Pick = Apply a specific commit.
- Tag = Mark a release commit.
- HEAD = Current checked-out commit reference.
- Origin = Default remote name.
- .gitignore = Ignore untracked paths.
- VS Code = Source-code editor.
- IDE = Integrated Development Environment.
- CLI = Command Line Interface.
- Terminal = Shell access interface.
- Node.js = JavaScript Runtime.
- npm = JavaScript Package Manager.
- package.json = Project metadata and dependencies.
- package-lock.json = Dependency lock file.
- node_modules = Installed packages.
- Postman = API Testing Tool.
- DevTools = Browser Debugging Tools.
- ESLint = Code Analysis.
- Prettier = Code Formatting.
- Vite = Frontend Build Tool.
- Docker = Container Platform.
- GitHub Actions = Workflow Automation.

---

# 40. Practical Tasks

Complete these practical tasks to strengthen your concepts:

1. Install Git and verify its version.
2. Configure Git username and email.
3. Create a new local repository.
4. Add files and create your first commit.
5. Create a feature branch.
6. Switch between branches.
7. Merge a feature branch into main.
8. Create and resolve a merge conflict.
9. Connect your local repository to GitHub.
10. Push your project to GitHub.
11. Clone another repository.
12. Practice git stash and git revert.
13. Create a proper .gitignore file for a MERN project.
14. Initialize a Node.js project using npm.
15. Install Express and Nodemon.
16. Test an API using Postman.
17. Inspect a website using Chrome DevTools.
18. Use breakpoints to debug JavaScript.
19. Format code using Prettier.
20. Deploy a small project using GitHub and a hosting platform.

**End of Git and Development Tools Notes.**
