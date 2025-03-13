---
routeAlias: installation-and-configuration
---

<img absolute src="../git-logo.png" w-10 top-2 right-2/>
<SlideCurrentNo absolute bottom-0 right-2/>
<Link to="installation-and-configuration" absolute top-3.4 font-bold right-15 color="#db4c37">Installation and configuration</Link>

# Summary

1. <Link to="introduction">Introduction</Link>
2. <span v-mark.box.green="{ at: 1, animate: false }">**Installation and configuration**</span>
3. <Link to="fundamental-principles">Fundamental principles</Link>
4. <Link to="commits-and-history">Commits and history</Link>
5. <Link to="references">References</Link>
6. <Link to="merge-rebase">Merge - Rebase</Link>
7. <Link to="other-commands-and-tools">Other commands and tools</Link>
8. <Link to="my-history-is-beautiful">My History is Beautiful</Link>
9. <Link to="remotes">Remotes</Link>
10. <Link to="workflows">Workflows</Link>
---

<img absolute src="../git-logo.png" w-10 top-2 right-2/>
<SlideCurrentNo absolute bottom-0 right-2/>
<Link to="installation-and-configuration" absolute top-3.4 font-bold right-15 color="#db4c37">Installation and configuration</Link>

# Installation

- **Windows**
  - via : https://git-scm.com/download/win
  - winget : winget install --id Git.Git -e --source winget
  - chocolate : choco install git.install
- **Linux**
  - Ubuntu: apt-get install git
  - Arch: pacman -S git
  - etc
- **MacOS**
  - homebrew: brew install git

<div border border-blue border-4 text-center ml-80 mr-80 pt-2 pb-2 mt-6><code>git version</code></div>

---

<img absolute src="../git-logo.png" w-10 top-2 right-2/>
<SlideCurrentNo absolute bottom-0 right-2/>
<Link to="installation-and-configuration" absolute top-3.4 font-bold right-15 color="#db4c37">Installation and configuration</Link>

# Configuration

- Global configuration file  
  `cat ~/.gitconfig`
- Show global configuration  
  `git config --global -l`
- Worktree configuration  
  `git config --worktree -l # See git help git-worktree`
- Local configuration file  
  `cat project_folder/.git/config`
- Show local configuration  
  `git config --local -l`

---

<img absolute src="../git-logo.png" w-10 top-2 right-2/>
<SlideCurrentNo absolute bottom-0 right-2/>
<Link to="installation-and-configuration" absolute top-3.4 font-bold right-15 color="#db4c37">Installation and configuration</Link>

# Configuration

- User name:  
  `git config --global user.name "Jean Valjean"`
- User email:  
  `git config --global user.email "jval01@miserables.fr"`
- Change default branch name:  
  `git config --global init.defaultBranch main`
- Convert to `lf` return lines on repository by not on file-system:  
  `git config --global core.autocrlf input`

---

<img absolute src="../git-logo.png" w-10 top-2 right-2/>
<SlideCurrentNo absolute bottom-0 right-2/>
<Link to="installation-and-configuration" absolute top-3.4 font-bold right-15 color="#db4c37">Installation and configuration</Link>

# `.gitattributes` file
Defining attributes per path

`.gitattributes` file: at root of the project  
Defines a behavior for files per path


```bash
# All text files should have the "lf" (Unix) line endings
* text eol=lf

# Explicitly declare text files you want to always be
# normalized and converted to native line endings on checkout.
*.java text
*.js text
*.html text

# Denote all files that are truly binary and should not be modified.
*.png binary
*.jar binary
*.pdf binary
*.gzip binary
```
---

<img absolute src="../git-logo.png" w-10 top-2 right-2/>
<SlideCurrentNo absolute bottom-0 right-2/>
<Link to="installation-and-configuration" absolute top-3.4 font-bold right-15 color="#db4c37">Installation and configuration</Link>

# `.gitignore` file
Specifies intentionally untracked files to ignore

<div mt-10/>

- `.gitignore`: Impacts underlying tree structure
- Refers folers and files that must not be tracked
- Accepts names and patterns

<div mt-10/>

```
target
.project
.classpath
.settings
**/*.bak
!**/process.bak
```
