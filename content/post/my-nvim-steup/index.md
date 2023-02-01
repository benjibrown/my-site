---
title: My Neovim Setup
description: All about my neovim setup, and how you can replicate it yourself.
slug: test
date: 2022-03-06 00:00:00+0000
image: cover.png
categories:
    - Markdown
tags:
    - 
---

My neovim setup is built on top of NVchad howevever, it has a few extra plugins which really do help a lot. <br />
Using `neovide` instead of `neovim` also helps a bit.

## Plugins

The plugins I use excluding the default NVchad ones are:

- True-Zen.nvim - For ZenMode (see image above)
- Markdown-Preview.nvim - For live previews of markdown
- Vimtex.vim - Live previews of LaTeX and other LaTeX utilities

## Setup

First, you'll have to install the NVchad configuration for Neovim. 
To do so run the following:
```bash
# Create a backup of your current neovim config
mv ~/.config/nvim ~/.config/nvim-backup
# Clone the NVchad configuration to ~/.config/nvim and launch Neovim
git clone https://github.com/NvChad/NvChad ~/.config/nvim --depth 1 && nvim
```
After running these commands, neovim will be launched and packer will do its thing to install all the plugins.
