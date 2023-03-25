# neovim-miscs
Configuring neovim from scratch are squential procedures, not worth remembering, but suitable for writing as a list. 

## Hardware and Operating system

Macbook Air M2 chip(macOS Ventura).

## Prerequsites
Install some softwares and tools before configuring neovim.

- Install Xcode Command Line: `xcode-select --install`
- [Homebrew](https://brew.sh/)
- [Oh My Zsh](https://ohmyz.sh)
- [Font Iosevka](https://github.com/be5invis/Iosevka)
- [Volta](https://volta.sh/): a tool manager for FrontEnd

## Targets
- write configurations completely in Lua
- make neovim suitable for developing frontend projects(mainly React-based projects)
- suitable for learning programming languages like Rust/Agda/Ocaml/Haskell/Racket
- markdown
- neogit
- nvim-orgmode

## Choose plugin manager
It's ineviable to manage plugins to use Neovim.
Q: Lazy.nvim or packer?
A: Lazy. The creator of packer choosed Lazy.

## Bootstrap Lazy according to readme.md of https://github.com/folke/lazy.nvim
- create init.lua in folder `~/.config/nvim`
- put bootstrap code in init.lua
```lua
vim.g.mapleader = [[ ]]
vim.g.maplocalleader = [[,]]
local lazypath = vim.fn.stdpath("data") .. "/lazy/lazy.nvim"
if not vim.loop.fs_stat(lazypath) then
  vim.fn.system({
    "git",
    "clone",
    "--filter=blob:none",
    "https://github.com/folke/lazy.nvim.git",
    "--branch=stable", -- latest stable release
    lazypat
  })
end
vim.opt.rtp:prepend(lazypath)
```
Above code of bootstraping lazy failed in my Mac, so I print the lazypath and clone the lazy repository to that path manually.

brew install --cask neovide
- add one line: `require("lazy").setup("plugins")` , the parameter "plugins" indicates using a Lua module to split plugins specs in multiple files.
- create folder `~/.config/nvim/lua/plugins`
- create file `~/.config/nvim/lua/plugins/init.lua`

## Rust

- download binaries of rust-analyzer, uncompress and rename it
- make it executable: `chmod +x rust-analyzer`
- find $PATH: `echo $PATH`, generally it contains `~/.cargo/bin`
- move binary to that path: `mv rust-analyzer ~/.cargo/bin`
- Firstly add plugin: [nvim-lspconfig](https://github.com/neovim/nvim-lspconfig)
- add `require'lspconfig'.rust_analyzer.setup{}` to `~/.config/nvim/init.lua`
- add [suggest configurations](https://github.com/neovim/nvim-lspconfig#suggested-configuration) to `~/.config/nvim/init.lua`

## Neovide - GUI client
- install Neovide using homebrew: `brew install --cask neovide`





