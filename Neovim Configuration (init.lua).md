# Neovim Configuration (init.lua)

-- Basic settings
vim.opt.number = true           -- Show line numbers
vim.opt.relativenumber = true   -- Relative line numbers
--vim.opt.cursorline = true       -- Highlight cursor line
vim.opt.termguicolors = true    -- True Color support
vim.opt.signcolumn = "yes"      -- Always show sign column

-- Indentation settings
vim.opt.tabstop = 2             -- Tab width
vim.opt.shiftwidth = 2          -- Auto-indent width
vim.opt.expandtab = true        -- Convert tabs to spaces
vim.opt.smartindent = true      -- Smart indent

-- Search settings
vim.opt.hlsearch = true         -- Highlight search results
vim.opt.incsearch = true        -- Incremental search
vim.opt.ignorecase = true       -- Case-insensitive search
vim.opt.smartcase = true        -- Case-sensitive if uppercase present

-- Clipboard
vim.opt.clipboard = "unnamedplus"

-- Backup
vim.opt.backup = false
vim.opt.swapfile = false
vim.opt.undofile = true

-- Scroll
vim.opt.scrolloff = 8           -- Keep 8 lines above/below cursor
vim.opt.sidescrolloff = 8

-- Key mappings
vim.g.mapleader = " "           -- Set leader key to space
vim.g.maplocalleader = " "

-- Keymap helper function
local keymap = vim.keymap.set
local opts = { noremap = true, silent = true }

-- Save and quit
keymap("n", "<leader>w", ":w<CR>", opts)
keymap("n", "<leader>q", ":q<CR>", opts)

-- Window navigation
keymap("n", "<C-h>", "<C-w>h", opts)
keymap("n", "<C-j>", "<C-w>j", opts)
keymap("n", "<C-k>", "<C-w>k", opts)
keymap("n", "<C-l>", "<C-w>l", opts)

-- Buffer navigation
keymap("n", "<S-l>", ":bnext<CR>", opts)
keymap("n", "<S-h>", ":bprevious<CR>", opts)

-- Clear search highlight
keymap("n", "<Esc>", ":nohlsearch<CR>", opts)

-- Move lines (Visual mode)
keymap("v", "J", ":m '>+1<CR>gv=gv", opts)
keymap("v", "K", ":m '<-2<CR>gv=gv", opts)

-- Escape to Normal mode in Terminal mode
--keymap("t", "<Esc>", "<C-\><C-n>", opts)
