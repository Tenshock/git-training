---
routeAlias: introduction
---

<img absolute src="../git-logo.png" w-10 top-2 right-2/>
<SlideCurrentNo absolute bottom-0 right-2/>
<Link to="introduction" absolute top-3.4 font-bold right-15 color="#db4c37">Introduction</Link>

# Summary

1. <span v-mark.box.green="{ at: 1, animate: false }">**Introduction**</span>
2. <Link to="installation-and-configuration">Installation and configuration</Link>
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
<Link to="introduction" absolute top-3.4 font-bold right-15 color="#db4c37">Introduction</Link>

# History

<v-clicks>

- Created by **Linus Torvalds** in 2005
- Replacement of BitKeeper
- Objectives: manage community work around the Linux kernel
- Git - the stupid content tracker  
  _"Git is a fast, scalable, distributed revision control system with an unusually rich command"_
- Github
  - **2013**: 3.5M users
  - **2015**: 10M users
  - **2021**: 65M users
  - **2023**: 100M users
</v-clicks>

---

<img absolute src="../git-logo.png" w-10 top-2 right-2/>
<SlideCurrentNo absolute bottom-0 right-2/>
<Link to="introduction" absolute top-3.4 font-bold right-15 color="#db4c37">Introduction</Link>

# Introduction

<v-clicks>

- DVCS
  - Decentralized, no SPOF
  - VCS: Version Control System
  - **Be able to work without affecting others**
- Efficient: local commands
  - Able to work offline
  - Work with snapshots
- Fault tolerant
  - non-destructive actions
  - catch-up aids
</v-clicks>

---

<img absolute src="../git-logo.png" w-10 top-2 right-2/>
<SlideCurrentNo absolute bottom-0 right-2/>
<Link to="introduction" absolute top-3.4 font-bold right-15 color="#db4c37">Introduction</Link>

# Centralized VCS (CVS, SVN, etc)

**Offline work impossible**

<img ml-3 src="../centralized-vcs.svg" />

---

<img absolute src="../git-logo.png" w-10 top-2 right-2/>
<SlideCurrentNo absolute bottom-0 right-2/>
<Link to="introduction" absolute top-3.4 font-bold right-15 color="#db4c37">Introduction</Link>

# Decentralized VCS (Git, Mercurial)

**Complete decentralization, tier-tier coordination**

<img ml-15 src="../tier-tier-decentralized-vcs.svg" />

---

<img absolute src="../git-logo.png" w-10 top-2 right-2/>
<SlideCurrentNo absolute bottom-0 right-2/>
<Link to="introduction" absolute top-3.4 font-bold right-15 color="#db4c37">Introduction</Link>

# Decentralized VCS with central repository

**Coordination by central repository**

<img ml-5 src="../coord-decentralized-vcs.svg" />
