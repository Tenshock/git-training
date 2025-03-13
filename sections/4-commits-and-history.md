---
routeAlias: commits-and-history
---

<img absolute src="../git-logo.png" w-10 top-2 right-2/>
<SlideCurrentNo absolute bottom-0 right-2/>
<Link to="commits-and-history" absolute top-3.4 font-bold right-15 color="#db4c37">Commits and history</Link>

# Summary

1. <Link to="introduction">Introduction</Link>
2. <Link to="installation-and-configuration">Installation and configuration</Link>
3. <Link to="fundamental-principles">Fundamental principles</Link>
4. <span v-mark.box.green="{ at: 1, animate: false }">**Commits and history**</span>
5. <Link to="references">References</Link>
6. <Link to="merge-rebase">Merge - Rebase</Link>
7. <Link to="other-commands-and-tools">Other commands and tools</Link>
8. <Link to="my-history-is-beautiful">My History is Beautiful</Link>
9. <Link to="remotes">Remotes</Link>
10. <Link to="workflows">Workflows</Link>
---

<div border-7 border-orange absolute top-0 left-0 bottom-0 right-0 z="-1"/>
<img absolute src="../git-logo.png" w-10 top-2 right-2/>
<SlideCurrentNo absolute bottom-0 right-2/>
<Link to="commits-and-history" absolute top-3.4 font-bold right-15 color="#db4c37">Commits and history</Link>

# ⚠️ Watch out: `pathspec`!
A way to target a group of files

`<pathspec>`: a pattern allowing to limit operations on one or part of the **working tree** structure.

```bash
# targets ./file1.html
git <command> file1.html

# targets ./file1.html and ./file2.html
git <command> file1.html file2.html

# targets all files under ./directory
git <command> directory/

# targets all html files under the current directory
git <command> *.html

# targets all current directory
git <command> .
```

---

<div border-7 border-orange absolute top-0 left-0 bottom-0 right-0 z="-1"/>
<img absolute src="../git-logo.png" w-10 top-2 right-2/>
<SlideCurrentNo absolute bottom-0 right-2/>
<Link to="commits-and-history" absolute top-3.4 font-bold right-15 color="#db4c37">Commits and history</Link>

# ⚠️ Watch out: `commit`!
A commit reference.

<v-clicks>

- <span v-mark.green.highlight="{at: 1, animate: false}">**Static references**</span>:
  - Commit id: `9269d99a3f232fcf90142b469e52feb61a7accdf`
  - Short id: `9269d99`
  - current commit: `HEAD`, `@`
- <span v-mark.green.highlight="{at: 2, animate: false}">**Relative references**</span>:
  - Parent: `\<commit>^`
  - Grandparent: `\<commit>^^`
  - N-th commit ancestor: `\<commit>~n`
  - N-th commit parent (in a merge case): `\<commit>^n`
  - commit range (2nd boundary excluded): `<commit2>..<commit1>` OR `<commit2> ^<commit1>`

</v-clicks>

---

<img absolute src="../git-logo.png" w-10 top-2 right-2/>
<SlideCurrentNo absolute bottom-0 right-2/>
<Link to="commits-and-history" absolute top-3.4 font-bold right-15 color="#db4c37">Commits and history</Link>

# Storage spaces

<v-clicks>

- <span v-mark.green.highlight="{at: 1, animate: false}">**Working tree**</span> (working directory tree)
  - Contains the project current commit snapshot, coming from the **repository**
  - It's the directory containing the `.git` directory
  - Contains potential work in progress
- <span v-mark.green.highlight="{at: 2, animate: false}">**Index**</span> (Staging area, cache)
  - Contains informations for next commit
  - The initial state is equal to current commit (`HEAD`)
- <span v-mark.green.highlight="{at: 3, animate: false}">**Repository**</span> (`.git` directory)
  - `.git` directory at root of the project
  - Contains **all** projects objects and references
  - Contains the _full_ project history
  - Permanent storage
</v-clicks>

---

<img absolute src="../git-logo.png" w-10 top-2 right-2/>
<SlideCurrentNo absolute bottom-0 right-2/>
<Link to="commits-and-history" absolute top-3.4 font-bold right-15 color="#db4c37">Commits and history</Link>

# Commit creation lifecycle

<div v-click.hide="2" bg-white absolute w-24 h-22 top-25 left-70/>
<div v-click.hide="3" bg-white absolute w-32 h-22 top-40 left-143/>
<img src="../commit-lifecycle.svg" ml-auto mr-auto h-40/>

<v-click>

1. Work in the working tree: add, modification, delete
```bash
vim CONTRIBUTING.md
```
</v-click>

<v-click>

2. Update the **index**  
```bash
git add CONTRIBUTING.md
```
</v-click>

<v-click>
3. Create a new commit with added modifications in the index
```bash
git commit -m "docs: update CONTRIBUTING instructions"
```
</v-click>

<v-click>

4. Start Again
</v-click>

---
clicks: 4
---

<img absolute src="../git-logo.png" w-10 top-2 right-2/>
<SlideCurrentNo absolute bottom-0 right-2/>
<Link to="commits-and-history" absolute top-3.4 font-bold right-15 color="#db4c37">Commits and history</Link>

# File lifecycle

<img v-click="[0]" src="../file-lifecycle-1.svg" absolute h-100 left-5/>
<img v-click="[1]" src="../file-lifecycle-2.svg" absolute h-100 left-5/>
<img v-click="[2]" src="../file-lifecycle-3.svg" absolute h-100 left-5/>
<img v-click="[3]" src="../file-lifecycle-4.svg" absolute h-100 left-5/>
<img v-click="[4]" src="../file-lifecycle-5.svg" absolute h-100 left-5/>

---

<img absolute src="../git-logo.png" w-10 top-2 right-2/>
<SlideCurrentNo absolute bottom-0 right-2/>
<Link to="commits-and-history" absolute top-3.4 font-bold right-15 color="#db4c37">Commits and history</Link>

# Know the current state of your project
`git status`

Show the file states in the **working tree** and in the **index**.

````md magic-move
```bash
# Files, current branch, its potential upstream, etc
git status
```
```bash
# Files, current branch, its potential upstream, etc
git status
On branch main
Your branch is up to date with 'origin/main'.

nothing to commit, working tree clean
```
````

<v-click>

````md magic-move
```bash
# Short version
git status --short --branch # or git status -sb
```
```bash
# Short version
git status --short --branch # or git status -sb
## main...origin/main
```
````
</v-click>

---

<img absolute src="../git-logo.png" w-10 top-2 right-2/>
<SlideCurrentNo absolute bottom-0 right-2/>
<Link to="commits-and-history" absolute top-3.4 font-bold right-15 color="#db4c37">Commits and history</Link>

# Commit preparation: Working tree and Index
How to add files to the index

To add to the index files that are `untracked` or `modified`

```bash {1,2|4,5|*}
# Adds files following pathspec
git add <pathspec>

# Adds ALL working tree alterations (adds, updates, deletions, permissions)
git add --all # or git add -A
```

---

<img absolute src="../git-logo.png" w-10 top-2 right-2/>
<SlideCurrentNo absolute bottom-0 right-2/>
<Link to="commits-and-history" absolute top-3.4 font-bold right-15 color="#db4c37">Commits and history</Link>

# Commit preparation: Working tree and Index
How to remove files to the index

To remove to the index files that are `added` or `staged`

```bash {1,2|4,5|7,8|*}
# Cancels modification in the working tree
git restore <patchspec>

# Cancels in the index (git add reverse)
git restore --staged <pathspec> # or git restore -S

# Cancels in the index AND in the working tree
git restore --staged --worktree <pathspec> # or git restore -SW
```

<div text-center border border-blue border-4 mt-5 v-click>

the `--source=<tree>` parameter restore the working tree files with **the content from the given tree**.  
By default, it is **equal to `HEAD`**.
</div>
---

<img absolute src="../git-logo.png" w-10 top-2 right-2/>
<SlideCurrentNo absolute bottom-0 right-2/>
<Link to="commits-and-history" absolute top-3.4 font-bold right-15 color="#db4c37">Commits and history</Link>

# Commit preparation: Working tree and Index
How to add a deletion to the index

To add a file deletion to the index:

```bash {1,2|4,5|7,8|*}
# Deletes from the working tree AND the index
git rm <pathspec>

# Deletes only from the index
git rm --cached <pathspec>

# Deletes recursively
git rm -r <pathspec>
```

---

<img absolute src="../git-logo.png" w-10 top-2 right-2/>
<SlideCurrentNo absolute bottom-0 right-2/>
<Link to="commits-and-history" absolute top-3.4 font-bold right-15 color="#db4c37">Commits and history</Link>

# Comparing states
How to compare between several zones or commits.

```bash {1,2|4,5|7,8|*}
# Differences between  `working tree` and the `index`
git diff [<pathspec>]

# Differences between index and HEAD
git diff --staged [<pathspec>]

# Differences between 2 commits for a given pathspec
git diff \<commit> \<commit> <pathspec>
```
<div v-click="3" mt-20>

> 💡 There is multiple diff algorithms, with performances and outputs varying.
</div>

---

<img absolute src="../git-logo.png" w-10 top-2 right-2/>
<SlideCurrentNo absolute bottom-0 right-2/>
<Link to="commits-and-history" absolute top-3.4 font-bold right-15 color="#db4c37">Commits and history</Link>

# Add a commit
Make changes permanent in the repository

To add a new commit to the repository: the index content is used to create a new commit with `HEAD` has its direct parent.

```bash {1,2|4,5|7,8|*}
# Adds a new commit with a message
git commit  --message <message> [--message <message>] # or git commit -m

# Adds a new commit with the message being written in an editor
git commit

# Adds all **modified** files, but NOT **untracked** ones
git commit --all # or git commit -a
```

---

<img absolute src="../git-logo.png" w-10 top-2 right-2/>
<SlideCurrentNo absolute bottom-0 right-2/>
<Link to="commits-and-history" absolute top-3.4 font-bold right-15 color="#db4c37">Commits and history</Link>

# Update the last commit
Oopsie fixie

To overrides the last commit:

```bash {1,2|4,5|7,8|*}
# Overrides the last commit while rewriting the message
git commit --amend --message <message>

# Rewrites the last commit message in an editor
git commit --amend

# Overrides the last commit while keeping the message
git commit --amend --no-edit
```

---

<img absolute src="../git-logo.png" w-10 top-2 right-2/>
<SlideCurrentNo absolute bottom-0 right-2/>
<Link to="commits-and-history" absolute top-3.4 font-bold right-15 color="#db4c37">Commits and history</Link>

# Show the commit history
Go back in time

To show the commits history, messages, updates, etc:

```bash {1,2|4,5|7,8|10,11|13,14|16,17|*}
# Shows history from HEAD
git log

# Shows history from another reference
git log \<commit> # May be a branch, a relative reference, etc

# Shows history while limiting commits
git log -n4

# Shows history with diffs
git log --patch

# Shows history on one line
git log --oneline

# Show history in a graph view
git log --graph
```

---

<div border-7 border-blue absolute top-0 left-0 bottom-0 right-0 z="-1"/>
<img absolute src="../git-logo.png" w-10 top-2 right-2/>
<SlideCurrentNo absolute bottom-0 right-2/>
<Link to="commits-and-history" absolute top-3.4 font-bold right-15 color="#db4c37">Commits and history</Link>

# Hands-on - 15 minutes

<div text-4>

1. Initialize a new git repository
2. Add a new `README.md` file and commit it
3. Add a new `CONTRIBUTING.md` file and commit it
4. Verify history, there must be 2 commits
5. Apply updates on both files
6. Check the repository state
7. Move the `CONTRIBUTING.md` file to a `staged` status
8. Commit what is in the `index` space
9. Check the repository state: `README.md` must be in a `modified` state
10. Check the history, there must be 3 commits
11. Revert changes on the `README.md` file, it must be in status `unmodified` then
12. Show all modifications between the two last commits (find 3 ways to do it)
13. **BONUS**: Retrieve the `CONTRIBUTING.md` file state as at its creation, only in the working tree. Then, re-update its state to `unmodified`
14. **BONUS**: update the last commit so that the author is your neighbor et the date is yesterday

</div>
---

<div border-7 border-green absolute top-0 left-0 bottom-0 right-0 z="-1"/>
<img absolute src="../git-logo.png" w-10 top-2 right-2/>
<SlideCurrentNo absolute bottom-0 right-2/>
<Link to="commits-and-history" absolute top-3.4 font-bold right-15 color="#db4c37">Commits and history</Link>

# Correction

1. Initialize a new git repository
```bash
git init
```

2. Add a new `README.md` file and commit it
```bash
touch README.md
git add README.md
git commit
```

3. Add a new `CONTRIBUTING.md` file and commit it
```bash
touch CONTRIBUTING.md
git add CONTRIBUTING.md
git commit
```

4. Verify history, there must be 2 commits
```bash
git log [--oneline]
```

5. Apply updates on both files
```bash
vim README.md
vim CONTRIBUTING.md
```

---

<div border-7 border-green absolute top-0 left-0 bottom-0 right-0 z="-1"/>
<img absolute src="../git-logo.png" w-10 top-2 right-2/>
<SlideCurrentNo absolute bottom-0 right-2/>
<Link to="commits-and-history" absolute top-3.4 font-bold right-15 color="#db4c37">Commits and history</Link>

# Correction

6. Check the repository state
```bash
git status
```

7. Move the `CONTRIBUTING.md` file to a `staged` status
```bash
git add CONTRIBUTING.md
```

8. Commit what is in the `index` space
```bash
git commit
```

9. Check the repository state: `README.md` must be in a `modified` state
```bash
git status
```

10. Check the history, there must be 3 commits
```bash
git log [--oneline]
```

11. Revert changes on the `README.md` file, it must be in status `unmodified` then
```bash
git restore README.md
```
---

<div border-7 border-green absolute top-0 left-0 bottom-0 right-0 z="-1"/>
<img absolute src="../git-logo.png" w-10 top-2 right-2/>
<SlideCurrentNo absolute bottom-0 right-2/>
<Link to="commits-and-history" absolute top-3.4 font-bold right-15 color="#db4c37">Commits and history</Link>

# Correction

12. Show all modifications between the two last commits (find 3 ways to do it)
```bash
git diff HEAD^^ HEAD
git diff @~2..
git log -p -2
```

13. **BONUS**: Retrieve the `CONTRIBUTING.md` file state as at its creation, only in the working tree. Then, re-update its state to `unmodified`
```bash
git restore --source <commit1> CONTRIBUTING.md
git restore -SW CONTRIBUTING.md
```

14: **BONUS**: Update the last commit so that the author is your neighbor et the date is yesterday
```bash
git commit --amend --no-edit --author=’John Doe <john.doe@git.com>’ --date=‘2022-03-13’
```

---

<img absolute src="../git-logo.png" w-10 top-2 right-2/>
<SlideCurrentNo absolute bottom-0 right-2/>
<Link to="commits-and-history" absolute top-3.4 font-bold right-15 color="#db4c37">Commits and history</Link>

# Commit messages
Best practices among the community

Git recommends a certain way of formatting messages:
```bash
git commit --help # section DISCUSSION
```
<div mt-10/>

> "Though not required, it’s a good idea to begin the commit message with a single short (no more than 50 characters) line summarizing the change, followed by a blank line and then a more thorough description"

<div mt-10/>

```bash
git commit -m "remove support for websockets" -m "Infra team warns about potential malicious requests through websocket"

remove support for websockets

Infra team warns about potential malicious requests through websocket
```

---

<img absolute src="../git-logo.png" w-10 top-2 right-2/>
<SlideCurrentNo absolute bottom-0 right-2/>
<Link to="commits-and-history" absolute top-3.4 font-bold right-15 color="#db4c37">Commits and history</Link>

# Commit messages
Leverage Conventional Commits

To go further, there is conventions adopted by several products and tooling such as [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/).

```
<type>[<scope>][!]: <subject>
<BLANK LINE>
<body>
<BLANK LINE>
<footer>
```

<div v-click mt-10>

```
chore(graphql)!: remove support for websockets

Infra team warns about potential malicious requests through websockets

BREAKING CHANGE: subscriptions endpoints are no more available
closes #19203
```
</div>

---

<img absolute src="../git-logo.png" w-10 top-2 right-2/>
<SlideCurrentNo absolute bottom-0 right-2/>
<Link to="commits-and-history" absolute top-3.4 font-bold right-15 color="#db4c37">Commits and history</Link>

# Commit messages
Leverage Conventional Commits

Advantages:
- Easier for contributors to read about the history
- Commit structure normalized
- Better communication about changes
- Better CI integration
- Automatic CHANGELOGs generation
- Automatic versioning (may follow [SemVer](https://semver.org/))

---

<img absolute src="../git-logo.png" w-10 top-2 right-2/>
<SlideCurrentNo absolute bottom-0 right-2/>
<Link to="commits-and-history" absolute top-3.4 font-bold right-15 color="#db4c37">Commits and history</Link>

# Atomic Commits
All about commit structure

Atomic commits are away to **define commits**, **their messages**, the **code behavior** and the **changes that are included** in it.

An atomic commit **must**:
- <span v-mark.green="1">build</span>, with passing tests
- focus around <span v-mark.green="1">**one** work unit</span>
- have a <span v-mark.green="1">clear commit message</span>

<div mt-5 text-center border border-blue border-4>

**Advantages**  
Better work history: unit of work, clear message  
All commit can be tested and built  
A commit can be reverted easily
</div>

