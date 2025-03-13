---
routeAlias: fundamental-principles
---

<img absolute src="../git-logo.png" w-10 top-2 right-2/>
<SlideCurrentNo absolute bottom-0 right-2/>
<Link to="fundamental-principles" absolute top-3.4 font-bold right-15 color="#db4c37">Fundamental principles</Link>

# Summary

1. <Link to="introduction">Introduction</Link>
2. <Link to="installation-and-configuration">Installation and configuration</Link>
3. <span v-mark.box.green="{ at: 1, animate: false }">**Fundamental principles**</span>
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
<Link to="fundamental-principles" absolute top-3.4 font-bold right-15 color="#db4c37">Fundamental principles</Link>

# Content Management

<v-clicks>

- Git is a content manager
- Contains projet snapshots
  - No delta (unlike SVN, CVS)
  - Fast access to all versions
- Identical content is deduplicated **by design**
- Content cannot be modified
- **CAS** : Content Adressed Storage
  - key-value storage
  - the key is the content SHA-1
</v-clicks>

---

<img absolute src="../git-logo.png" w-10 top-2 right-2/>
<SlideCurrentNo absolute bottom-0 right-2/>
<Link to="fundamental-principles" absolute top-3.4 font-bold right-15 color="#db4c37">Fundamental principles</Link>

# SHA-1

<v-clicks>

- <span v-mark.green.highlight="{at: 1, animate: false}">160-bit cryptographic hash function</span> (20 bytes)
  - Represented in Git on a hexadecimal form (40 characters)
  - Not recommended for **security purpose** but valid for **CAS purpose**
- <span v-mark.green.highlight="{at: 2, animate: false}">Guarantees</span>
  - Id unicity in a decentralized context
  - deduplication
- <span v-mark.green.highlight="{at: 3, animate: false}">Facilitates change detection</span> by hash comparison
</v-clicks>

<div v-click mt-10>

> $2^{160}$ total values (or $10^{48}$)  
> If we generate more than **3 000 objects/second** during **1 billion years**:  
> -> **1 chance out of 1 billion** to experience **hash collision**.
</div>

---

<img absolute src="../git-logo.png" w-10 top-2 right-2/>
<SlideCurrentNo absolute bottom-0 right-2/>
<Link to="fundamental-principles" absolute top-3.4 font-bold right-15 color="#db4c37">Fundamental principles</Link>

# Git Objects
Stored in `.git/objects/` (CAS)

<v-clicks>

- <span v-mark.green.highlight="{at: 1, animate: false}">Blob</span>
  - **B**inary **L**arge **OB**ject: Non-interpreted binary content
  - file equivalent
- <span v-mark.green.highlight="{at: 2, animate: false}">Tree</span>
  - Folder equivalent
  - Contains trees and/or blobs
  - ⚠️an empty tree is not tracked: `.gitkeep`
- <span v-mark.green.highlight="{at: 3, animate: false}">Commit</span>
  - a project state snapshot
</v-clicks>

<div v-click mt-5>

> Git stores its objects via a hash partitioning based on 2 chars sequences in hexadecimal representation.  
> Each sequence corresponds to a directory, except for the last one.
</div>

---

<img absolute src="../git-logo.png" w-10 top-2 right-2/>
<SlideCurrentNo absolute bottom-0 right-2/>
<Link to="fundamental-principles" absolute top-3.4 font-bold right-15 color="#db4c37">Fundamental principles</Link>

# A commit = a snapshot

<img src="../commit-snapshot.svg" />

---

<img absolute src="../git-logo.png" w-10 top-2 right-2/>
<SlideCurrentNo absolute bottom-0 right-2/>
<Link to="fundamental-principles" absolute top-3.4 font-bold right-15 color="#db4c37">Fundamental principles</Link>

# Commit anatomy

<v-clicks>

- <span v-mark.green.highlight="{at: 1, animate: false}">Project Root Tree</span>
- <span v-mark.green.highlight="{at: 2, animate: false}">Metadata:</span>
  - timestamp
  - Author
  - Committer
- <span v-mark.green.highlight="{at: 3, animate: false}">Message</span>
- <span v-mark.green.highlight="{at: 4, animate: false}">Parent commits</span>
  - Empty (initial commits)
  - One (general case)
  - Two (merge result)
  - More (octopus merge)
</v-clicks>

---

<img absolute src="../git-logo.png" w-10 top-2 right-2/>
<SlideCurrentNo absolute bottom-0 right-2/>
<Link to="fundamental-principles" absolute top-3.4 font-bold right-15 color="#db4c37">Fundamental principles</Link>

# Graph
A Git History representation

The *repository* contains **ALL** commits, which may be organized as an **acyclic oriented graph**.

<img v-click src="../git-graph.svg" ml-auto mr-auto mt-20 h-50>

---

<img absolute src="../git-logo.png" w-10 top-2 right-2/>
<SlideCurrentNo absolute bottom-0 right-2/>
<Link to="fundamental-principles" absolute top-3.4 font-bold right-15 color="#db4c37">Fundamental principles</Link>

# Git References
Stored in `.git/refs/`

References are stored in `.git/refs`.  
The file name is the **reference name**, the file content is the **reference target**.

- Pointer towards a commit
- Pointer towards another reference
- Several Types:
  - **Symbolic**: `HEAD` is `.git/HEAD`
  - **local branches**: `.git/refs/heads/`
  - **remote branches**: `.git/refs/remotes`
  - **Tags**: `.git/refs/tags/`

---

<img absolute src="../git-logo.png" w-10 top-2 right-2/>
<SlideCurrentNo absolute bottom-0 right-2/>
<Link to="fundamental-principles" absolute top-3.4 font-bold right-15 color="#db4c37">Fundamental principles</Link>

# Git Commands

<div translate-y="-3">

```
add                       commit                    filter-branch             ls-files                  notes                     repack                    submodule
am                        commit-graph              fmt-merge-msg             ls-remote                 p4                        replace                   submodule--helper
annotate                  commit-tree               for-each-ref              ls-tree                   pack-objects              replay                    subtree
apply                     config                    for-each-repo             mailinfo                  pack-redundant            request-pull              switch
archimport                count-objects             format-patch              mailsplit                 pack-refs                 rerere                    symbolic-ref
archive                   credential                fsck                      maintenance               patch-id                  reset                     tag
bisect                    credential-cache          fsck-objects              merge                     pickaxe                   restore                   unpack-file
blame                     credential-cache--daemon  fsmonitor--daemon         merge-base                prune                     rev-list                  unpack-objects
branch                    credential-store          gc                        merge-file                prune-packed              rev-parse                 update-index
bugreport                 cvsexportcommit           get-tar-commit-id         merge-index               pull                      revert                    update-ref
bundle                    cvsimport                 grep                      merge-octopus             push                      rm                        update-server-info
cat-file                  cvsserver                 gui--askpass              merge-one-file            quiltimport               send-email                upload-archive
check-attr                daemon                    hash-object               merge-ours                range-diff                send-pack                 upload-archive--writer
check-ignore              describe                  help                      merge-recursive           read-tree                 sh-i18n--envsubst         upload-pack
check-mailmap             diagnose                  hook                      merge-recursive-ours      rebase                    shell                     var
check-ref-format          diff                      http-backend              merge-recursive-theirs    receive-pack              shortlog                  verify-commit
checkout                  diff-files                http-fetch                merge-resolve             reflog                    show                      verify-pack
checkout--worker          diff-index                http-push                 merge-subtree             refs                      show-branch               verify-tag
checkout-index            diff-tree                 imap-send                 merge-tree                remote                    show-index                version
cherry                    difftool                  index-pack                mergetool                 remote-ext                show-ref                  web--browse
cherry-pick               difftool--helper          init                      mktag                     remote-fd                 sparse-checkout           whatchanged
citool                    fast-export               init-db                   mktree                    remote-ftp                stage                     worktree
clean                     fast-import               instaweb                  multi-pack-index          remote-ftps               stash                     write-tree
clone                     fetch                     interpret-trailers        mv                        remote-http               status
column                    fetch-pack                log                       name-rev                  remote-https              stripspace
```
</div>

---
layout: fact
---

<img absolute src="../git-logo.png" w-10 top-2 right-2/>
<SlideCurrentNo absolute bottom-0 right-2/>
<Link to="fundamental-principles" absolute top-3.4 font-bold right-15 color="#db4c37">Fundamental principles</Link>

# 173 commands

### As of `git 2.48.1`

---

<img absolute src="../git-logo.png" w-10 top-2 right-2/>
<SlideCurrentNo absolute bottom-0 right-2/>
<Link to="fundamental-principles" absolute top-3.4 font-bold right-15 color="#db4c37">Fundamental principles</Link>

# Git Commands

```
add          diff      pull       show
bisect       fetch     push       stash
blame        help      rebase     status
branch       init      remote     submodule
cherry-pick  log       reset      subtree
clean        merge     restore    switch
clone        mv        revert     tag
commit       prune     rm         worktree
```

---

<img absolute src="../git-logo.png" w-10 top-2 right-2/>
<SlideCurrentNo absolute bottom-0 right-2/>
<Link to="fundamental-principles" absolute top-3.4 font-bold right-15 color="#db4c37">Fundamental principles</Link>

# Commands Types
Two main types

`git help --all`

<v-clicks>

- <span v-mark.green.highlight="{at: 1, animate: false}">High level</span>
  - **Porcelain**
  - **Auxiliary**
- <span v-mark.green.highlight="{at: 2, animate: false}">Low level</span>
  - **plumbing**
</v-clicks>

<div v-click border-3 border border-blue text-center ml-auto mr-auto w-200 p-5 mt-10>

### **Understanding git internal behavior** helps better apprehend and **master high level commands**.
</div>

---

<img absolute src="../git-logo.png" w-10 top-2 right-2/>
<SlideCurrentNo absolute bottom-0 right-2/>
<Link to="fundamental-principles" absolute top-3.4 font-bold right-15 color="#db4c37">Fundamental principles</Link>

# HELP!
One command to rule them all.

The most useful command, **the one to remember**.

<div mt-10 text-center>

`git help <command>`

`git <command> --help`

`git help --guide`

`git help <concept>`

</div>

---

<div border-7 border-blue absolute top-0 left-0 bottom-0 right-0 z="-1"/>
<img absolute src="../git-logo.png" w-10 top-2 right-2/>
<SlideCurrentNo absolute bottom-0 right-2/>
<Link to="fundamental-principles" absolute top-3.4 font-bold right-15 color="#db4c37">Fundamental principles</Link>

# Hands-on - 10 minutes

1. Create a directory “myproject" and move into it
2. Execute the command to create a Git repository inside this project
3. Display directory contents, including hidden items
4. Display contents of .git directory
5. Create a “myfile” file with content in it
6. Find the low-level command to calculate the file SHA-1 and create a blob
7. Execute this command on the “myfile” file
8. Find the blob stored in the local repository
9. Find the low-level command to display the contents of the blob based on the calculated identifier
10. Find the high-level command to display the blob content based on the calculated identifier

---

<div border-7 border-green absolute top-0 left-0 bottom-0 right-0 z="-1"/>
<img absolute src="../git-logo.png" w-10 top-2 right-2/>
<SlideCurrentNo absolute bottom-0 right-2/>
<Link to="fundamental-principles" absolute top-3.4 font-bold right-15 color="#db4c37">Fundamental principles</Link>

# Correction

1. Create a directory “myproject" and move into it  
  ```shell
  mkdir myproject
  cd myproject
  ```
2. Execute the command to create a Git repository inside this project  
```shell
git init
```
3. Display directory contents, including hidden items  
```shell
ls -a
```
4. Display contents of .git directory  
```shell
ls .git
```
5. Create a “myfile” file with content in it  
```shell
echo 'Hello' > myfile
```

---

<div border-7 border-green absolute top-0 left-0 bottom-0 right-0 z="-1"/>
<img absolute src="../git-logo.png" w-10 top-2 right-2/>
<SlideCurrentNo absolute bottom-0 right-2/>
<Link to="fundamental-principles" absolute top-3.4 font-bold right-15 color="#db4c37">Fundamental principles</Link>

# Correction

6. Find the low-level command to calculate the file SHA-1 and create a blob  
```shell
git help -a
```
7. Execute this command on the “myfile” file  
```shell
git hash-object -w myfile
```
8. Find the blob stored in the local repository  
```shell
ls .git/objects/<2 first SHA-1 characters>/<remaining SHA-1>
```
9. Find the low-level command to display the contents of the blob based on the calculated identifier  
```shell
git cat-file -p <SHA-1>
```
10. Find the high-level command to display the blob content based on the calculated identifier  
```shell
git show <SHA-1>
```

