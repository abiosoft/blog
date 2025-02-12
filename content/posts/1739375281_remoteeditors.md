+++
title = 'Remote editors in Vim territory'
description = 'Remote editors in Vim territory'
date = 2025-02-12T16:48:01+01:00
readTime = true
tags = ["vim", "ssh", "vscode", "fleet", "gateway"]
+++

If there is one thing that Vim users have emphasised over time, it is the fact that Vim is always available.

Vim is available on pretty much every Unix machine. In the rare case that Vim is missing, the less functional parent, Vi, would be found.

### Vimmers don't quit

There is a popular joke about users not being able to quit Vim. It is a very popular search term with answers in many tech-related [QnA platforms](https://stackoverflow.com/q/11828270). But that is not our focus here.

Vim users never want to quit. Of course they quit the editor from time to time, but they never want to quit having the Vim experience.

Top of the list of the non-negotiable Vim experience is the use of `h`, `j`, `k`, `l` as navigation keys. It is an indoctrination that has no return, the right hand fingers connive with the brain in rebelling against every attempt of moving the fingers away from the comfort of the [home-row](https://www.computerhope.com/jargon/h/hrk.htm) keys, to the stress of arrow keys.

For a number of reasons Vim cannot always be used. But Vim users want the Vim experience with every editor. And that is why pretty much every relevant code editor has Vim support of some sorts.

Even Emacs has a [Vim mode](https://github.com/emacs-evil/evil), akin to having a functional military base in an enemy territory.

### Vimming remotely

Many Linux users access remote machines with [SSH](https://en.wikipedia.org/wiki/Secure_Shell). And with remote workspaces becoming increasingly popular, remote SSH sessions have become a viable option for code editing.

Remote does not necessarily imply a machine in a far away data center, it can be a Virtual Machine running on the same device.

Vim fits perfectly for remote sessions because it only needs a shell session to run.

### The right tool for the job

While Vim excels as a code editor, it may fall short in other areas like providing framework or programming language specific features.

Due to this, Vim users need to succumb to the use of more featured editors and IDEs.

However, the pain of living outside of Vim is quickly felt and the instinct of bringing the Vim experience along kicks in.

### Remote Editors

Emacs long had [Tramp Mode](https://www.emacswiki.org/emacs/TrampMode), which is impressive at what it offers. But the landscape changed in [2019](https://code.visualstudio.com/blogs/2019/05/02/remote-development) when [Visual Studio Code](https://code.visualstudio.com) got the [Remote Editing](https://code.visualstudio.com/docs/remote/ssh) feature.

With remote editing, the IDE becomes a thin client for it's remote companion. It runs and feels native but the engine is on a remote machine.

Visual Studio Code may be leading the park but other options are surfacing including [Fleet](https://www.jetbrains.com/fleet/) and [Gateway](https://www.jetbrains.com/remote-development/gateway/).

Visual Studio Code, Fleet and Gateway actually have one thing in common, support for a decent Vim mode.

### Viable alternative

As mentioned earlier, Vimmers don't quit. Whether locally or remotely via SSH, in the Terminal or the GUI, the Vim experience is not negotiable.

Now there are alternatives that offer powerful IDE features, feel native while running remotely, and a decent Vim editing experience.

Vim remains undisputed in its simplicity and experience. But when the right tool is needed for the job, the Vim experience is no longer the necessary sacrifice

It is therefore safe to concede that remote editors are now roaming in Vim territory.
