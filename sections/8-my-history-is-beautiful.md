---
routeAlias: my-history-is-beautiful
---

<img absolute src="../git-logo.png" w-10 top-2 right-2/>
<SlideCurrentNo absolute bottom-0 right-2/>
<Link to="other-commands-and-tools" absolute top-3.4 font-bold right-15 color="#db4c37">My History is Beautiful</Link>

# Summary

1. <Link to="introduction">Introduction</Link>
2. <Link to="installation-and-configuration">Installation and configuration</Link>
3. <Link to="fundamental-principles">Fundamental principles</Link>
4. <Link to="commits-and-history">Commits and history</Link>
5. <Link to="references">References</Link>
6. <Link to="merge-rebase">Merge - Rebase</Link>
7. <Link to="other-commands-and-tools">Other commands and tools</Link>
8. <span v-mark.box.green="{ at: 1, animate: false }">**My History is Beautiful**</span>
9. <Link to="remotes">Remotes</Link>
10. <Link to="workflows">Workflows</Link>

---

<div border-7 border-orange absolute top-0 left-0 bottom-0 right-0 z="-1"/>
<img absolute src="../git-logo.png" w-10 top-2 right-2/>
<SlideCurrentNo absolute bottom-0 right-2/>
<Link to="my-history-is-beautiful" absolute top-3.4 font-bold right-15 color="#db4c37">My History is Beautiful</Link>

# ⚠️Watch out
with great power comes great responsibility

This section explains methods to **totally rewrite** its history.

```bash
git help rebase

NOTES
  You should understand the implications of using git rebase on a repository that you share

RECOVERING FROM UPSTREAM REBASE
  Rebasing (or any other form of rewriting) a branch that others have based work on is a bad idea:  
  anyone downstream of it is forced to manually fix their history.
```

---
clicks: 2
---

<img absolute src="../git-logo.png" w-10 top-2 right-2/>
<SlideCurrentNo absolute bottom-0 right-2/>
<Link to="my-history-is-beautiful" absolute top-3.4 font-bold right-15 color="#db4c37">My History is Beautiful</Link>

# Interactive Rebase
Full control over history

`git rebase --interactive` option:
- Displays todo-list to perform
- Assign an action to each commit
- Can specify a commit range, by default from HEAD to `<commit>` exclusively

<div mt-5 v-click="1">

````md magic-move { at: 2 }
```bash
git rebase --interactive 8072b
```
```bash
git rebase --interactive 8072b
pick 33a2d C2
pick 8232e C3
pick 79c72 C4
```
````
</div>

<img v-click="[1,3]" src="../interactive.svg" top-91 absolute left="50%" translate-x="-50%"/>

---
clicks: 6
---

<img absolute src="../git-logo.png" w-10 top-2 right-2/>
<SlideCurrentNo absolute bottom-0 right-2/>
<Link to="my-history-is-beautiful" absolute top-3.4 font-bold right-15 color="#db4c37">My History is Beautiful</Link>

# Interactive Rebase - TODO list

<div mt-10/>

````md magic-move
```bash
git rebase --interactive HEAD~3
```
```bash
git rebase --interactive HEAD~3
pick 33a2d C2
pick 8232e C3
pick 79c72 C4
```
```bash {*|1,2|1,3|1,4}
git rebase --interactive HEAD~3
pick 79c72 C4
pick 8232e C3
pick 33a2d C2
```
```bash
git rebase --interactive HEAD~3
pick 79c72 C4
pick 8232e C3
pick 33a2d C2
Successfully rebased and updated refs/heads/main.
```
````

<img v-click="[0,3]" src="../interactive-1.svg" top-60 absolute left="50%" translate-x="-50%"/>
<img v-click="[3]"   src="../interactive-2.svg" top-60 absolute left="50%" translate-x="-50%"/>
<img v-click="[4]"   src="../interactive-3.svg" top-60 absolute left="50%" translate-x="-50%"/>
<img v-click="[5]"   src="../interactive-4.svg" top-60 absolute left="50%" translate-x="-50%"/>
<img v-click="[6]"   src="../interactive-5.svg" top-60 absolute left="50%" translate-x="-50%"/>

---

<img absolute src="../git-logo.png" w-10 top-2 right-2/>
<SlideCurrentNo absolute bottom-0 right-2/>
<Link to="my-history-is-beautiful" absolute top-3.4 font-bold right-15 color="#db4c37">My History is Beautiful</Link>

# Interactive Rebase - TODO list
Main actions

- **p, pick \<commit>** = use commit
- **r, reword \<commit>** = use commit, but edit the commit message
- **e, edit \<commit>** = use commit, but stop for amending
- **s, squash \<commit>** = use commit, but meld into previous commit
- **f, fixup \<commit>** = like "squash" but keep only the previous commit's log message
- **x, exec \<command>** = run command (the rest of the line) using shell
- **d, drop \<commit>** = remove commit

---
clicks: 7
---

<img absolute src="../git-logo.png" w-10 top-2 right-2/>
<SlideCurrentNo absolute bottom-0 right-2/>
<Link to="my-history-is-beautiful" absolute top-3.4 font-bold right-15 color="#db4c37">My History is Beautiful</Link>

# Interactive Rebase - TODO list

````md magic-move
```bash
git rebase --interactive HEAD~3
```
```bash
git rebase --interactive HEAD~3
pick 33a2d C2
pick 8232e C3
pick 79c72 C4
```
```bash {*|2|3|4|5}
git rebase --interactive HEAD~3
pick 8232e C3
drop 33a2d C2
exec yarn test
fixup 79c72 C4
```
```bash
git rebase --interactive HEAD~3
pick 8232e C3
drop 33a2d C2
exec yarn test
fixup 79c72 C4
Successfully rebased and updated refs/heads/main.
```
````

<img v-click="[0,3]" src="../interactive-2-1.svg" top-60 absolute left="50%" translate-x="-50%"/>
<img v-click="[3,6]" src="../interactive-2-2.svg" top-60 absolute left="50%" translate-x="-50%"/>
<img v-click="[6]" src="../interactive-2-3.svg" top-60 absolute left="50%" translate-x="-50%"/>
<img v-click="[7]" src="../interactive-2-4.svg" top-60 absolute left="50%" translate-x="-50%"/>

---

<img absolute src="../git-logo.png" w-10 top-2 right-2/>
<SlideCurrentNo absolute bottom-0 right-2/>
<Link to="my-history-is-beautiful" absolute top-3.4 font-bold right-15 color="#db4c37">My History is Beautiful</Link>

# Interactive Rebase - Sequence
How to proceed

1. Execute `git rebase --interactive <commit>`
2. Edit the todo-list
3. If a conflict arises, resolve it like for a classic rebase
4. Go on until the end

<div v-click mt-5 border border-blue border-4>

```bash
# To edit the todo-list while in interactive rebase
git rebase --edit-todo

# Skip the current step and go to next step
git rebase --skip

# Abort rebase
git rebase --abort
```
</div>

---
clicks: 10
---

<img absolute src="../git-logo.png" w-10 top-2 right-2/>
<SlideCurrentNo absolute bottom-0 right-2/>
<Link to="my-history-is-beautiful" absolute top-3.4 font-bold right-15 color="#db4c37">My History is Beautiful</Link>

# Interactive Rebase - Edit
Fixup the "C2" commit

<div absolute w-100>

````md magic-move
```bash
git rebase --interactive 8072b
```
```bash
git rebase --interactive 8072b
pick 33a2d C2
pick 8232e C3
pick 79c72 C4
```
```bash {*|2|2|2|2|2|3|4}
git rebase --interactive 8072b
edit 33a2d C2
pick 8232e C3
pick 79c72 C4
```
```bash {5}
git rebase --interactive 8072b
edit 33a2d C2
pick 8232e C3
pick 79c72 C4
Successfully rebased and updated refs/heads/main.
```
````
</div>

<div absolute w-100 v-click="4" left-120>

````md magic-move { at: 5 }
```bash
vim README.md
```
```bash {2}
vim README.md
git add README.md
```
```bash {3}
vim README.md
git add README.md
git commit --amend --no-edit
```
```bash {4|0|0|0}
vim README.md
git add README.md
git commit --amend --no-edit
git rebase --continue
```
````
</div>

<img v-click="[0,3]" src="../interactive-3-1.svg" top-60 absolute left="50%" translate-x="-50%"/>
<img v-click="[3,6]" src="../interactive-3-2.svg" top-60 absolute left="50%" translate-x="-50%"/>
<img v-click="[6,8]"   src="../interactive-3-3.svg" top-60 absolute left="50%" translate-x="-50%"/>
<img v-click="[8]"   src="../interactive-3-4.svg" top-60 absolute left="50%" translate-x="-50%"/>
<img v-click="[9]"   src="../interactive-3-5.svg" top-60 absolute left="50%" translate-x="-50%"/>
<img v-click="[10]"   src="../interactive-3-6.svg" top-60 absolute left="50%" translate-x="-50%"/>

---

<div border-7 border-blue absolute top-0 left-0 bottom-0 right-0 z="-1"/>
<img absolute src="../git-logo.png" w-10 top-2 right-2/>
<SlideCurrentNo absolute bottom-0 right-2/>
<Link to="my-history-is-beautiful" absolute top-3.4 font-bold right-15 color="#db4c37">My History is Beautiful</Link>

# Hands-on - 10 minutes

```bash
git clone https://github.com/Tenshock/git-exercise.git interactive-rebase
cd interactive-rebase
git switch interactive-rebase
```

1. Move the commit `add file5,file6` such as it becomes the parent of `add file3` commit
2. Delete the commit `add file2` (2 ways)
3. Edit the commit `add file3` by modifying the content of the file `file3`
4. Merge commits `add file3` and `add file4` and modify the new commit message
5. Split the commit `add file5,file6` in two commits `add file5` and `add file6` that contain each the respective file
6. **BONUS**: Retrieve the `add file2` commit and put it as parent of the current tip of the branch

---

<div border-7 border-green absolute top-0 left-0 bottom-0 right-0 z="-1"/>
<img absolute src="../git-logo.png" w-10 top-2 right-2/>
<SlideCurrentNo absolute bottom-0 right-2/>
<Link to="my-history-is-beautiful" absolute top-3.4 font-bold right-15 color="#db4c37">My History is Beautiful</Link>

# Correction

1. Move the commit `add file5,file6` such as it becomes the parent of `add file3` commit
```bash
git rebase -i @~3
pick 4d2d80b add file3
pick 8bc4d52 add file4
pick 8eae6d7 add file5,file6
⬇️
pick 8eae6d7 add file5,file6
pick 4d2d80b add file3
pick 8bc4d52 add file4
# Then save your todo-list
```

---

<div border-7 border-green absolute top-0 left-0 bottom-0 right-0 z="-1"/>
<img absolute src="../git-logo.png" w-10 top-2 right-2/>
<SlideCurrentNo absolute bottom-0 right-2/>
<Link to="my-history-is-beautiful" absolute top-3.4 font-bold right-15 color="#db4c37">My History is Beautiful</Link>

# Correction

2. Delete the commit `add file2` (2 ways)
```bash
git rebase -i @~4
pick 077f137 add file2
pick 349bafb add file5,file6
pick 9c31520 add file3
pick 84a280c add file4

# First solution
drop 077f137 add file2
pick 349bafb add file5,file6
pick 9c31520 add file3
pick 84a280c add file4
# Then save your todo-list

# Second solution
pick 349bafb add file5,file6
pick 9c31520 add file3
pick 84a280c add file4
# Then save your todo-list
```

---

<div border-7 border-green absolute top-0 left-0 bottom-0 right-0 z="-1"/>
<img absolute src="../git-logo.png" w-10 top-2 right-2/>
<SlideCurrentNo absolute bottom-0 right-2/>
<Link to="my-history-is-beautiful" absolute top-3.4 font-bold right-15 color="#db4c37">My History is Beautiful</Link>

# Correction

3. Edit the commit `add file3` by modifying the content of the file `file3`
```bash
git rebase -i @~2
pick 7a827be add file3
pick 35365fc add file4
⬇️
edit 7a827be add file3
pick 35365fc add file4
# Then save your todo-list

echo 'a new line 🐼' >> file3
git commit -a --amend --no-edit

git rebase --continue
```

---

<div border-7 border-green absolute top-0 left-0 bottom-0 right-0 z="-1"/>
<img absolute src="../git-logo.png" w-10 top-2 right-2/>
<SlideCurrentNo absolute bottom-0 right-2/>
<Link to="my-history-is-beautiful" absolute top-3.4 font-bold right-15 color="#db4c37">My History is Beautiful</Link>

# Correction

4. Merge commits `add file3` and `add file4` and modify the new commit message
```bash
git rebase -i HEAD~2
pick 3320ce9 add file3
pick 3fe1a3f add file4
⬇️
pick 3320ce9 add file3
squash 3fe1a3f add file4
# Then save your todo-list
# Then edit the commit message
```

---

<div border-7 border-green absolute top-0 left-0 bottom-0 right-0 z="-1"/>
<img absolute src="../git-logo.png" w-10 top-2 right-2/>
<SlideCurrentNo absolute bottom-0 right-2/>
<Link to="my-history-is-beautiful" absolute top-3.4 font-bold right-15 color="#db4c37">My History is Beautiful</Link>

# Correction

5. Split the commit `add file5,file6` in two commits `add file5` and `add file6` that contain each the respective file
```bash
git rebase -i HEAD^^
pick 205ca19 add file5,file6
pick b731919 add file3,file4
⬇️
edit 205ca19 add file5,file6
pick b731919 add file3,file4
# Then save your todo-list

git reset @^
git add file5
git commit -m 'add file5'
git add file6
git commit -m 'add file6'
git rebase --continue
```

---

<div border-7 border-green absolute top-0 left-0 bottom-0 right-0 z="-1"/>
<img absolute src="../git-logo.png" w-10 top-2 right-2/>
<SlideCurrentNo absolute bottom-0 right-2/>
<Link to="my-history-is-beautiful" absolute top-3.4 font-bold right-15 color="#db4c37">My History is Beautiful</Link>

# Correction

6. **BONUS**: Retrieve the `add file2` commit and put it as parent of the current tip of the branch
```bash
git reflog # Find your wanted commit

git rebase -i HEAD^
pick 23e55f9 add file3,file4
⬇️
pick <commit>
pick 23e55f9 add file3,file4
# Then save your todo-list
```

---

<img absolute src="../git-logo.png" w-10 top-2 right-2/>
<SlideCurrentNo absolute bottom-0 right-2/>
<Link to="my-history-is-beautiful" absolute top-3.4 font-bold right-15 color="#db4c37">My History is Beautiful</Link>

# Interactive Rebase - Autosquash
To speed up things even more

`--autosquash` allows to apply fixup, remword, amend and squash operations fastly

Commits flavors:
- `git commit --fixup <commit>`: Creates a fixup commit that targets `<commit>`, leaving the target `<commit>` message as is
- `git commit --fixup amend:<commit>`: Creates an amend commit that also updates the target `<commit>` message
- `git commit --fixup reword:<commit>`: Creates a commit that will only updates the target `<commit>` message
- `git commit --stash <commit>`: Creates a commit that will stash with the target `<commit>`

<div mt-5/>

> In the editor, when modifying the commit message, **do not update the first line** that goes with `"amend! ..."` or `"fixup! ..."`.  
> Git uses it to match for the target commit when performing the `rebase --autosquash`.

---
clicks: 7
---

<img absolute src="../git-logo.png" w-10 top-2 right-2/>
<SlideCurrentNo absolute bottom-0 right-2/>
<Link to="my-history-is-beautiful" absolute top-3.4 font-bold right-15 color="#db4c37">My History is Beautiful</Link>

# Interactive Rebase - Edit
Fixup the "C2" commit

<div absolute w-218 v-click="[0,4]">

```bash {0|1|1-2|1-3}
vim src/Program.cs
git add src/Program.cs
git commit --fixup 33a2d
```
</div>

<div absolute w-218 v-click="[4,8]">

````md magic-move { at: 5 }
```bash
git rebase --interactive 33a2d^
```
```bash
git rebase --interactive --autosquash 33a2d^
```
```bash
git rebase --interactive --autosquash 33a2d^
pick 33a2d C2
fixup aeb31 fixup! C2
pick 8232e C3
pick 79c72 C4
```
```bash
git rebase --interactive --autosquash 33a2d^
pick 33a2d C2
fixup aeb31 fixup! C2
pick 8232e C3
pick 79c72 C4
Successfully rebased and updated refs/heads/main.
```
````
</div>

<img v-click="[0,3]" src="../autosquash-1.svg" top-60 absolute left="50%" translate-x="-50%"/>
<img v-click="[3,7]" src="../autosquash-2.svg" top-60 absolute left="50%" translate-x="-50%"/>
<img v-click="[7]"   src="../autosquash-3.svg" top-60 absolute left="50%" translate-x="-50%"/>

---

<div border-7 border-blue absolute top-0 left-0 bottom-0 right-0 z="-1"/>
<img absolute src="../git-logo.png" w-10 top-2 right-2/>
<SlideCurrentNo absolute bottom-0 right-2/>
<Link to="my-history-is-beautiful" absolute top-3.4 font-bold right-15 color="#db4c37">My History is Beautiful</Link>

# Hands-on - 10 minutes

```bash
git clone https://github.com/Tenshock/git-exercise.git interactive-rebase-autosquash
cd interactive-rebase-autosquash
git switch interactive-rebase-autosquash
```

1. Update the content of `file3` and with a fixup commit, update the `add file3` commit
2. With one autosquash rebase
   * update the `file2` file in the commit `add file2`
   * update the `file4` file in the commit `add file4`
   * delete the commit `add file3`
3. Update the `file2` file in the commit `add file2` while updating the commit message as well
4. **Bonus**: Update the `file1` file in the commit `add file1` with a fixup commit

---

<div border-7 border-green absolute top-0 left-0 bottom-0 right-0 z="-1"/>
<img absolute src="../git-logo.png" w-10 top-2 right-2/>
<SlideCurrentNo absolute bottom-0 right-2/>
<Link to="my-history-is-beautiful" absolute top-3.4 font-bold right-15 color="#db4c37">My History is Beautiful</Link>

# Correction

1. Update the content of `file3` and with a fixup commit, update the `add file3` commit
```bash
echo "some new content" >> file3
git commit -a --fixup HEAD~2
git rebase -i --autosquash HEAD~4
```

2. With one autosquash rebase
   * update the `file2` file in the commit `add file2`
   * update the `file4` file in the commit `add file4`
   * delete the commit `add file3`
```bash
echo 'and again' >> file2
git commit -a --fixup HEAD~3
echo 'aaand again.' >> file4
git commit -a --fixup HEAD~2
git rebase -i --autosquash HEAD~6
```

---

<div border-7 border-green absolute top-0 left-0 bottom-0 right-0 z="-1"/>
<img absolute src="../git-logo.png" w-10 top-2 right-2/>
<SlideCurrentNo absolute bottom-0 right-2/>
<Link to="my-history-is-beautiful" absolute top-3.4 font-bold right-15 color="#db4c37">My History is Beautiful</Link>

# Correction

3. Update the `file2` file in the commit `add file2` while updating the commit message as well
```bash
echo 'and another one' >> file2
git commit -a --fixup amend:HEAD~3
# Remember, update commit message body in editor, not the title!
git rebase -i --autosquash
```

4. **Bonus**: Update the `file1` file in the commit `add file1` with a fixup commit
```bash
echo 'the final one' >> file1
git commit -a --fixup HEAD~4
git rebase -i --autosquash --root
```

