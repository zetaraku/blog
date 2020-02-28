---
title: How to Change Hexo Themes
date: 2020-02-22 17:12:57
categories: Tutorial
tags: [hexo, theme, git-submodule]
---

# Change the current theme

Modify this option in `_config.yml`.
```yml _config.yml
theme: <theme-name>    # <- change the 'theme' option to the theme name you're using
```

# Install a theme

```sh
git clone <theme-repo-url> themes/<theme-name>
```

# Remove a theme

```sh
git rm -rf themes/<theme-name>
```

# Install a theme as a submodule (recommended)

```sh
git submodule add <theme-repo-url> themes/<theme-name>
```

* Refer to this [Tutorial](https://juejin.im/post/5c2e22fcf265da615d72c596) for more details. (zh-CN)

# Remove a theme as a submodule

```sh
git submodule deinit -f themes/<theme-name>
rm -rf .git/modules/themes/<theme-name>
git rm -f themes/<theme-name>
```

# Cloning an existed project with submodules

```sh
git clone --recursive <repo-url>
```
or
```sh
git clone <repo-url>
git submodule init               # Initialize the submodules recorded in the index
git submodule update --remote    # Update the submodules to match what this project expects.
```

# Catch up with the updates of the theme

```sh
git submodule update --remote    # Update the submodules to match what this project expects.
```
