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
Note, I personally use Neovide instead of Neovim, which is basically just an alternate frontend for Neovim that provides smooth scrolling and really smooth cursor movements.

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
After running these commands, Neovim will be launched and Packer (NVchad's plugin manager) will do its thing to install all the plugins.

Now, this will have installed the default Neovim configuration, however to complete the setup of **my** Neovim configuration, a few additional steps are required.

We'll now need to edit a few files to install some additional plugins.
Before we do though, enter the `~/.config/nvim/lua/custom`, once there replace the contents of `chadrc.lua` with the following:

```lua
local M = {}
M.plugins = {
  user = require "custom.plugins"
}
M.ui = {
  theme = "catppuccin",
}

return M
```

This will allow custom plugins to be installed on our NVchad instance.
Now, enter the directory `plugins` whilst inside the directory you just entered.
If it doesn't exist, just make it.

Now, you'll need to replace the contents of `init.lua` (if its exists, if not jut make it) with the following:

```lua
  ["iamcco/markdown-preview.nvim"] = {
    run = function() vim.fn["mkdp#util#install"]() end,
  },
  ["Pocco81/true-zen.nvim"] = {
    config = function()
		         require("true-zen").setup {} end,
  },
  ["lervag/vimtex"] = {},
}
```

Once you have done that, launch Neovim and run `:PackerInstall` to install the additional plugins.
