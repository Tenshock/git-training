---
routeAlias: other-commands-and-tools
---

<img absolute src="../git-logo.png" w-10 top-2 right-2/>
<SlideCurrentNo absolute bottom-0 right-2/>
<Link to="other-commands-and-tools" absolute top-3.4 font-bold right-15 color="#db4c37">Other Commands and Tools</Link>

# Summary

1. <Link to="introduction">Introduction</Link>
2. <Link to="installation-and-configuration">Installation and configuration</Link>
3. <Link to="fundamental-principles">Fundamental principles</Link>
4. <Link to="commits-and-history">Commits and history</Link>
5. <Link to="references">References</Link>
6. <Link to="merge-rebase">Merge - Rebase</Link>
7. <span v-mark.box.green="{ at: 1, animate: false }">**Other commands and tools**</span>
8. <Link to="my-history-is-beautiful">My History is Beautiful</Link>
9. <Link to="remotes">Remotes</Link>
10. <Link to="workflows">Workflows</Link>
---

<img absolute src="../git-logo.png" w-10 top-2 right-2/>
<SlideCurrentNo absolute bottom-0 right-2/>
<Link to="other-commands-and-tools" absolute top-3.4 font-bold right-15 color="#db4c37">Other Commands and Tools</Link>

# Alias
Saving you some finger travels

Allows to define new names for a given command

```bash {1|3-8|3-12|*}
git config ([--global]|[--local]) alias.<alias_name> <command>

# Examples
git config --global alias.sw switch
git config --global alias.co commit
git config --global alias.unstage 'reset HEAD --'
git config --local alias.last 'log -1 HEAD'
git config --local alias.hist 'log --oneline --graph'

# Usages
git last
git unstage my_file.txt
```

<v-click>

> commands available in the PATH that are in the form `"git-my-name"` can be invoked in the same way: `git my-name`!  
> Also, terminal plugins (`oh-my-zsh`, `oh-my-posh`, _etc_) have git plugins that populate several aliases for you.
</v-click>

---

<img absolute src="../git-logo.png" w-10 top-2 right-2/>
<SlideCurrentNo absolute bottom-0 right-2/>
<Link to="other-commands-and-tools" absolute top-3.4 font-bold right-15 color="#db4c37">Other Commands and Tools</Link>

# Stash
The last storage place

Allows you to save some work from your `working tree` and your `index` without commiting them.

```bash {*|1-2|4-5|7-8|10-11|13-14|*}
# Lists all stashs
git stash list

# Stashes all modifications, do not stash untracked files
git stash [push] [-m <message>]

# Stashes all modifications AND untracked files
git stash -u

# Applies last saved stash and deletes it
git stash pop

# Applies n-th stash but keeping it
git stash apply stash@{n}
```

---
clicks: 3
---

<img absolute src="../git-logo.png" w-10 top-2 right-2/>
<SlideCurrentNo absolute bottom-0 right-2/>
<Link to="other-commands-and-tools" absolute top-3.4 font-bold right-15 color="#db4c37">Other Commands and Tools</Link>

# Revert
The mirror commit

Creates a commit that cancels modifications from the commit(s) specified

````md magic-move { at: 2 }
```bash
git revert 33a2d
```
```bash {2|*}
git revert 33a2d
git reset --hard 79c72 # or @^
```
````

<img v-click="[0]" src="../revert-1.svg" top-70 absolute left="50%" translate-x="-50%"/>
<img v-click="[1]" src="../revert-2.svg" top-70 absolute left="50%" translate-x="-50%"/>
<img v-click="[2,4]" src="../revert-3.svg" top-70 absolute left="50%" translate-x="-50%"/>

---
clicks: 2
---

<img absolute src="../git-logo.png" w-10 top-2 right-2/>
<SlideCurrentNo absolute bottom-0 right-2/>
<Link to="other-commands-and-tools" absolute top-3.4 font-bold right-15 color="#db4c37">Other Commands and Tools</Link>

# Cherry-pick
Apply arbitrary commit(s)

Given one or more existing commits, apply the change each one introduces, recording a new commit for each.

```bash {0|0|1}
git cherry-pick beaf4
```

<img v-click="[0]" src="../cherry-pick-1.svg" scale-96 top-46 absolute left="45%" translate-x="-50%"/>
<img v-click="[1]" src="../cherry-pick-2.svg" scale-96 top-46 absolute left="45%" translate-x="-50%"/>
<img v-click="[2]" src="../cherry-pick-3.svg" scale-96 top-46 absolute left="45%" translate-x="-50%"/>

---

<img absolute src="../git-logo.png" w-10 top-2 right-2/>
<SlideCurrentNo absolute bottom-0 right-2/>
<Link to="other-commands-and-tools" absolute top-3.4 font-bold right-15 color="#db4c37">Other Commands and Tools</Link>

# Worktree
One repository, several working trees

- Allows to have multiple `working trees`, all attached to the **same repository**
- A repository has a **main worktree** (It's the one you work one day-to-day)
- Several **linked worktree** may be added, deleted, etc
- One branch may only be checked on **one worktree at a time**
- Usually, linked worktrees are created outside of the main worktree

---

<img absolute src="../git-logo.png" w-10 top-2 right-2/>
<SlideCurrentNo absolute bottom-0 right-2/>
<Link to="other-commands-and-tools" absolute top-3.4 font-bold right-15 color="#db4c37">Other Commands and Tools</Link>

# Add a worktree

```bash
git branch
* main
feature1
feature2
```
<div mt-5/>

<div absolute w-105>

```bash {*|1,3-4|1,6-7|1,9-10|1,12-13|1,15-16|*}
git worktree add <path> [<commit-ish>]

# Worktree feature1 on branch "feature1"
git worktree add ../feature1

# Worktree toto on branch "feature2"
git worktree add ../toto feature2

# Worktree tata on new branch "tata"
git worktree add ../tata

# Worktree titi on new branch "hotfix"
git worktree add ../titi -b hotfix

# Worktree tutu in detached mode
git worktree add ../tutu --detach # or -d
```
</div>
<div v-click="7" absolute left-125 w-105>

````md magic-move { at: 8 }
```bash
git worktree list
```
```bash
git worktree list
/home/user/my-project    a8682c8 [main]
/home/user/feature1      b4ceee6 [feature1]
/home/user/toto          90fd1c0 [feature2]
/home/user/tata          a8682c8 [tata]
/home/user/titi          a8682c8 [hotfix]
/home/user/tutu          a8682c8 [detached HEAD]
```
````
</div>

---

<img absolute src="../git-logo.png" w-10 top-2 right-2/>
<SlideCurrentNo absolute bottom-0 right-2/>
<Link to="other-commands-and-tools" absolute top-3.4 font-bold right-15 color="#db4c37">Other Commands and Tools</Link>

# Delete worktrees

````md magic-move { at: 1 }
```bash
 pwd
 /home/user/my-project

 git worktree list
 /home/user/my-project    a8682c8 [main]
 /home/user/feature1      b4ceee6 [feature1]
 /home/user/toto          90fd1c0 [feature2]
 /home/user/tata          a8682c8 [tata]
 /home/user/titi          a8682c8 [hotfix]
/home/user/tutu          a8682c8 [detached HEAD]
```
```bash
 pwd
 /home/user/my-project

 git worktree list
 /home/user/my-project    a8682c8 [main]
 /home/user/feature1      b4ceee6 [feature1]
 /home/user/toto          90fd1c0 [feature2]
 /home/user/tata          a8682c8 [tata]
 /home/user/titi          a8682c8 [hotfix]
```
```bash
 pwd
 /home/user/my-project

 git worktree list
 /home/user/my-project    a8682c8 [main]
 /home/user/feature1      b4ceee6 [feature1]
 /home/user/toto          90fd1c0 [feature2]
 /home/user/tata          a8682c8 [tata]
```
```bash
 pwd
 /home/user/my-project

 git worktree list
 /home/user/my-project    a8682c8 [main]
 /home/user/feature1      b4ceee6 [feature1]
 /home/user/toto          90fd1c0 [feature2]
```
````

<div absolute top-73 w-217 mt-5>

```bash {0|1-2|1-5|1-8}
# Remove by relative path
git worktree remove ../tutu

# Remove by absolute path
git worktree remove /home/user/titi

# Remove by last path match
git worktree remove tata
```
</div>

---

<div border-7 border-blue absolute top-0 left-0 bottom-0 right-0 z="-1"/>
<img absolute src="../git-logo.png" w-10 top-2 right-2/>
<SlideCurrentNo absolute bottom-0 right-2/>
<Link to="other-commands-and-tools" absolute top-3.4 font-bold right-15 color="#db4c37">Other Commands and Tools</Link>

# Hands-on - 10 minutes

```bash
git clone https://github.com/Tenshock/git-exercise.git worktree-tp
cd worktree-tp
[bash|zsh] init-3.sh

```

1. Add a worktree based on `feature` branch
2. In the worktree previously created, update the README and commit it
3. From the worktree, add another worktree, named `my-worktree`, on a new branch `my-branch`
4. Go to `my-worktree`, list all worktrees
5. Still in `my-worktree`, update the `README.md` file without commiting it
6. Go back to the main worktree, delete all other linked worktrees

---

<div border-7 border-green absolute top-0 left-0 bottom-0 right-0 z="-1"/>
<img absolute src="../git-logo.png" w-10 top-2 right-2/>
<SlideCurrentNo absolute bottom-0 right-2/>
<Link to="other-commands-and-tools" absolute top-3.4 font-bold right-15 color="#db4c37">Other Commands and Tools</Link>

# Correction

1. Add a worktree based on `feature` branch
```bash
git worktree add ../feature
```

2. In the worktree previously created, update the README and commit it
```bash
cd ../feature
echo 'A new line!' >> README.md
git commit -am 'docs: update README'
```

3. From the worktree, add another worktree, named `my-worktree`, on a new branch `my-branch`
```bash
git worktree add ../my-worktree -b my-branch
```

4. Go to `my-worktree`, list all worktrees
```bash
cd ../my-worktree
git worktree list
```

---

<div border-7 border-green absolute top-0 left-0 bottom-0 right-0 z="-1"/>
<img absolute src="../git-logo.png" w-10 top-2 right-2/>
<SlideCurrentNo absolute bottom-0 right-2/>
<Link to="other-commands-and-tools" absolute top-3.4 font-bold right-15 color="#db4c37">Other Commands and Tools</Link>

# Correction

5. Still in `my-worktree`, update the `README.md` file without commiting it
```bash
echo 'Another line' >> README.md
```

6. Go back to the main worktree, delete all other linked worktrees
```bash
cd ../tp-worktree
git worktree remove feature
git worktree remove my-worktree --force # or -f
```

---

<img absolute src="../git-logo.png" w-10 top-2 right-2/>
<SlideCurrentNo absolute bottom-0 right-2/>
<Link to="other-commands-and-tools" absolute top-3.4 font-bold right-15 color="#db4c37">Other Commands and Tools</Link>

# Blame
👀👀👀

Show what revision and author last modified each line of a file

````md magic-move
```bash {1,2}
 # For all options
 git blame --help

 # Shows blame on all file
 git blame README.md
```
```bash
# For all options
git blame --help

# Shows blame on all file
git blame README.md
52cd07ed (Cédric Prezelin 2025-03-18 15:34:09 +0100 1) # Git Exercice
52cd07ed (Cédric Prezelin 2025-03-18 15:34:09 +0100 2)
52cd07ed (Cédric Prezelin 2025-03-18 15:34:09 +0100 3) This is a repository with several branches and commits to tr
52cd07ed (Cédric Prezelin 2025-03-18 15:34:09 +0100 4)
cf376326 (Cédric Prezelin 2025-03-18 15:35:30 +0100 5) ## Getting Started
cf376326 (Cédric Prezelin 2025-03-18 15:35:30 +0100 6)
cf376326 (Cédric Prezelin 2025-03-18 15:35:30 +0100 7) Follow instructions in the git workshop.
cf376326 (Cédric Prezelin 2025-03-18 15:35:30 +0100 8)
```
````

---

<img absolute src="../git-logo.png" w-10 top-2 right-2/>
<SlideCurrentNo absolute bottom-0 right-2/>
<Link to="other-commands-and-tools" absolute top-3.4 font-bold right-15 color="#db4c37">Other Commands and Tools</Link>

# Bisect
Facilitate bug hunt!

Allows to perform a dichotomic search to find some changes.

```bash {*|1-2|4-5|7-8|10-11|*}
# Start the bisect
git bisect start

# Defines the good commit
git bisect good \<commit>

# Defines the bad commit
git bisect bad \<commit>

# Skip a step
git bisect skip \<commit>
```

<div mt-5/>

<v-click at="5">

> The algorithmic complexity of a dichotomic search is $\log_2(n)$.  
For a bug hunt on a 20 000 commits range, it will need maximum.. **14 iterations**.
</v-click>

---
clicks: 12
---

<img absolute src="../git-logo.png" w-10 top-2 right-2/>
<SlideCurrentNo absolute bottom-0 right-2/>
<Link to="other-commands-and-tools" absolute top-3.4 font-bold right-15 color="#db4c37">Other Commands and Tools</Link>

# Bisect - Step by Step
Facilitate bug hunt!

<div absolute w-217 v-click="[0,4]">

````md magic-move
```bash {0|1|2}
git bisect start
git bisect good 0.0.1
git bisect bad
```
```bash {3-5}
git bisect start
git bisect good 0.0.1
git bisect bad
Bisecting: 4 revisions left to test after this (roughly 4 steps)
[33a2dd81ec841b4373b3f2f64f45841e60314671] fix: update tax calculation
```
````
</div>
<div absolute w-217 v-click="[4,6]">

````md magic-move { at: 5 }
```bash
git bisect good
```
```bash
git bisect good
Bisecting: 3 revisions left to test after this (roughly 3 steps)
[de9d96bea5f756645b3a7f9aa788c31c224822c1] ci: clear flakky tests
```
````
</div>

<div absolute w-217 v-click="[6,8]">

````md magic-move { at: 7 }
```bash
git bisect bad
```
```bash
git bisect bad
Bisecting: 2 revisions left to test after this (roughly 2 steps)
[08b9d9d05b57857892fd6dfd3f6ad1f38286fdd8] feat: add tax evasion endpoint
```
````

</div>
<div absolute w-217 v-click="[8,10]">

````md magic-move { at: 9 }
```bash
git bisect bad
```
```bash
git bisect bad
Bisecting: 1 revision left to test after this (roughly 1 step)
[8232e7bef86458b348d2c7b962c8c86cb7a1badc] refactor: simplify TVA calculus
```
````

</div>
<div absolute w-217 v-click="[10,12]">

````md magic-move { at: 11 }
```bash
git bisect good
```
```bash
git bisect good
08b9dd81ec841b4373b3f2f64f45841e60314671 is the first bad commit
commit 08b9dd81ec841b4373b3f2f64f45841e60314671
Author: John Doe <john.doe@acme.com>
Date:   Fri Mar 21 10:57:30 2025 +0100

    feat: add tax evasion endpoint

 README.md | 2 +-
 1 file changed, 1 insertion(+), 1 deletion(-)
```
````
</div>
<div absolute w-217 v-click="[12]">

```bash
git bisect reset
```
</div>

<img v-click="[0,2]" src="../bisect-1.svg" scale-96 top-95 absolute left="50%" translate-x="-50%"/>
<img v-click="[2]"   src="../bisect-2.svg" scale-96 top-95 absolute left="50%" translate-x="-50%"/>
<img v-click="[3,5]"   src="../bisect-3.svg" scale-96 top-95 absolute left="50%" translate-x="-50%"/>
<img v-click="[5,7]"   src="../bisect-4.svg" scale-96 top-95 absolute left="50%" translate-x="-50%"/>
<img v-click="[7,9]"   src="../bisect-5.svg" scale-96 top-95 absolute left="50%" translate-x="-50%"/>
<img v-click="[9,11]"   src="../bisect-6.svg" scale-96 top-95 absolute left="50%" translate-x="-50%"/>
<img v-click="[11]"   src="../bisect-7.svg" scale-96 top-95 absolute left="50%" translate-x="-50%"/>
<img v-click="[12]"   src="../bisect-1.svg" scale-96 top-95 absolute left="50%" translate-x="-50%"/>

---
clicks: 3
---

<img absolute src="../git-logo.png" w-10 top-2 right-2/>
<SlideCurrentNo absolute bottom-0 right-2/>
<Link to="other-commands-and-tools" absolute top-3.4 font-bold right-15 color="#db4c37">Other Commands and Tools</Link>

# Bisect - Run
Automate bug hunt!

Run a `bisect` and configure a command to automatically test whether a commit is good or bad.  
If the script returns a `0` code, the commit is considered as good, otherwise it is considered as bad.

<div mt-5 v-click="1">

````md magic-move { at: 2 }
```bash {0|1}
 git bisect start @ 0.0.1
 git bisect run <command> # Boom, automatic!
```
```bash {2-11}
git bisect start @ 0.0.1
git bisect run <command> # Boom, automatic!
08b9dd81ec841b4373b3f2f64f45841e60314671 is the first bad commit
commit 08b9dd81ec841b4373b3f2f64f45841e60314671
Author: John Doe <john.doe@acme.com>
Date:   Fri Mar 21 10:57:30 2025 +0100

    feat: add tax evasion endpoint

 README.md | 2 +-
 1 file changed, 1 insertion(+), 1 deletion(-)
```
````
</div>

<img v-click="[0,2]" src="../bisect-1.svg" scale-96 top-107 absolute left="50%" translate-x="-50%"/>
<img v-click="[2]"   src="../bisect-3.svg" scale-96 top-107 absolute left="50%" translate-x="-50%"/>
<img v-click="[3]"   src="../bisect-6.svg" scale-96 top-107 absolute left="50%" translate-x="-50%"/>

---

<div border-7 border-blue absolute top-0 left-0 bottom-0 right-0 z="-1"/>
<img absolute src="../git-logo.png" w-10 top-2 right-2/>
<SlideCurrentNo absolute bottom-0 right-2/>
<Link to="other-commands-and-tools" absolute top-3.4 font-bold right-15 color="#db4c37">Other Commands and Tools</Link>

# Hands-on - 10 minutes

```bash
git clone https://github.com/Tenshock/git-exercise.git bisect
cd bisect
[bash|zsh] init-4.sh
```

<div mt-10/>

1. In the `bisect` branch, find the first commit where the `README.md` is equal to `bad`, without **run**. You can use the `begin` as the first good commit
2. In the `bisect-run` branch, retrieve the `command.sh` file from the `command` branch
3. Find the first commit where `README.md` is equal to `bad`, **with a bisect run**. You can use the `begin-run` tag as the first good commit

---

<div border-7 border-green absolute top-0 left-0 bottom-0 right-0 z="-1"/>
<img absolute src="../git-logo.png" w-10 top-2 right-2/>
<SlideCurrentNo absolute bottom-0 right-2/>
<Link to="other-commands-and-tools" absolute top-3.4 font-bold right-15 color="#db4c37">Other Commands and Tools</Link>

# Correction

1. In the `bisect` branch, find the first commit where the `README.md` is equal to `bad`, without **run**. You can use the `begin` as the first good commit
```bash
git switch bisect
git bisect start
git bisect good begin
git bisect bad HEAD # or git bisect bad @ or git bisect bad
git bisect bad|good
```

2. In the `bisect-run` branch, retrieve the `command.sh` file from the `command` branch
```bash
git switch bisect-run
git restore command.sh --source command
```

3. Find the first commit where `README.md` is equal to `bad`, **with a bisect run**. You can use the `begin-run` tag as the first good commit
```bash
git bisect start @ begin-run
git bisect run ./command.sh
```

---

<img absolute src="../git-logo.png" w-10 top-2 right-2/>
<SlideCurrentNo absolute bottom-0 right-2/>
<Link to="other-commands-and-tools" absolute top-3.4 font-bold right-15 color="#db4c37">Other Commands and Tools</Link>

# Graphical Extensions

<v-click>

```bash
# not in built-in git anymore
git gui browser <reference>
gitk
```
</v-click>

<v-click>

- Github Desktop (Linux, MacOS, Windows, free)
- Source Tree (MacOS, Windows, free)
- GitKraken (Linux, MacOS, Windows, freemium)
- Fork (MacOS, Windows, free)
- IDE GUIs (Git Lens, Jetbrains, etc)
</v-click>

<img v-click="2" src="../graphical-tools.png" w-150 mr-auto ml-auto mt-5/>


