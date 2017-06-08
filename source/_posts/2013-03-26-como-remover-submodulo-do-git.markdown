---
author: pauloluan
comments: true
date: 2013-03-26 11:19:22
layout: post
slug: como-remover-submodulo-do-git
title: Como remover submódulo do GIT
wordpress_id: 840
tags:
- GIT
- submódulo
- submodules
---

To remove a submodule you need to:

    1. Delete the relevant section from the ".gitmodules" file.
    2. Delete the relevant section from ".git/config".
    3. Run "git rm --cached path_to_submodule" (no trailing slash).
    4. Commit
    5. Delete the now untracked submodule files: "rm -rf path_to_submodule"

<!-- more -->
[Fonte](http://stackoverflow.com/questions/1260748/how-do-i-remove-a-git-submodule)
