# init.lua.md

This file contains documentation for init.lua - the main 
configuration file for nvim.

## A note about folding

Folds are used extensively; here are some useful commands for folds:

  | Action                    | command |
  |---------------------------|---------|
  | Toggle fold open / closed | za      |
  | Jump to next fold         | zj      |
  | Jump to previous fold     | zk      |
  | Jump to start of fold     | [z      |
  | Jump  to end of fold      | ]z      |

lua files use 'foldmethod=marker'. The start of a fold is marked with {{{ and ends with }}}.
These markers are placed inside comments. They may be given a number to denote nesting level:

``` lua
    -- my major section {{{1
    -- my subsection {{{2
    -- }}} end of subsection
    -- }}} end of major section
```

## Setting options: 

    * See `:help vim.opt`
    * For more options, you can see `:help option-list`

## [ Leader key ]

    * Set <space> as the leader key
    * See `:help mapleader`

NOTE: Must happen before plugins are loaded (otherwise wrong leader will be used)

``` lua
    vim.g.mapleader
    vim.g.maplocalleader
```

## [ Displaying various things ] 

* Use markers to place folds
* Make line numbers default
* Make relative line numbers default
* Don't show the mode, since it's already in the status line
* Show signcolumn by default
* Enable break indent
* Open horizontal splits to the right
* Open vertical splits below
* Set how neovim will display whitespace characters see `:help 'listchars'`
* Preview substitutions live, as you type!
* Show which line your cursor is on
* Set number of screen lines to keep above and below the cursor.

``` lua
    vim.opt.foldmethod = 'marker'
    vim.opt.number
    vim.opt.relativenumber
    vim.opt.showmode
    vim.opt.signcolumn
    vim.opt.breakindent
    vim.opt.splitright
    vim.opt.splitbelow
    vim.opt.list = true
    vim.opt.listchars
    vim.opt.inccommand
    vim.opt.cursorline
    vim.opt.scrolloff
```

## [ Fonts ] 

* whether the terminal can use an installed Nerd Font 
I use kitty terminal, it doesn't need patched fonts, so have_nerd_font = false.
I have installed suitable fonts though.

``` lua
    vim.g.have_nerd_font
```

## [ Mouse ] 

* Enable mouse mode, can be useful for resizing splits for example!

``` lua
    vim.opt.mouse

```
## [ Time related things ]

* Set time between nothing typed and writing the swap fie to disk (update time)
* Set time between 1st and 2nd letters of a key mapping, e.g. <leader>f

``` lua
vim.opt.updatetime
vim.opt.timeoutlen
```

## [ Clipboard ]

Sync clipboard between OS and Neovim. Schedule the setting after `UiEnter` 
because it can increase startup-time. Remove this option if you want your 
OS clipboard to remain independent.  See `:help 'clipboard'`

``` lua
vim.schedule(function()
  vim.opt.clipboard
end)

```

## [ History ]

* Save undo history

``` lua
    vim.opt.undofile
```

## [ Searching ]

* Case-insensitive searching UNLESS \C or one or more capital letters in the search term.

``` lua
    vim.opt.ignorecase
    vim.opt.smartcase
```

## [[ Basic Keymaps ]]
`:help vim.keymap.set()`

### Miscellaneous keymaps
* Clear highlights on search. `:help hlsearch`
* Open diagnostic [Q]uickfix list' `setloclist`
* Exit terminal mode. Doesn't work for tmux and some terminals.

### Keybinds to make split navigation easier
Navigate splits with Ctrl+<hjkl>. `wincmd`
* Move focus to the {left,right,lower,upper} window


## [ Basic Autocommands ]
`:help lua-guide-autocommands`

### Miscellaneous autocommands
* Highlight when yanking. TextYankPost. `:help vim.highlight.on_yank()`

## [[ Plugins ]]

### [ Install lazy.nvim plugin manager ]
`:help lazy.nvim.txt` or (github lazy.nvim)[https://github.com/folke/lazy.nvim]

### [ Configure and install plugins ]

To check the current status of your plugins and perform Update, Install, Check
etc, run :Lazy.

NOTE: Plugins can be added with a link (or for a github repo: 'owner/repo'
link).

NOTE: Plugins can also be added by using a table, with the first argument being
the link and the following keys can be used to configure plugin
behavior/loading/etc.

Use `opts = {}` to force a plugin to be loaded.

NOTE: Plugins can also be configured to run Lua code when they are loaded.

This is often very useful to both group configuration, as well as handle lazy
loading plugins that don't need to be loaded immediately at startup.

For example, in the configuration for which-key, we use: `event = 'VimEnter'`

which loads which-key before all the UI elements are loaded. Events can be
normal autocommands events (`:help autocmd-events`).

Then, because we use the `config` key, the configuration only runs after the
plugin has been loaded: `config = function() ... end`

NOTE: Plugins can specify dependencies.

The dependencies are proper plugin specifications as well - anything you do for
a plugin at the top level, you can do for a dependency.

Use the `dependencies` key to specify the dependencies of a particular plugin.

* hardtime: nag you if you don't use text object and motions
* vim-sleuth: automatic tabstop and shiftwidth formatting
* which-key: 
* telescope: fuzzy finder files, lsp, ...)


Here are the comments from the initial gitsigns section from init.lua.
I am now using the script provided by kickstart but leaving the 
original comments here:
``` lua
  -- Here is a more advanced example where we pass configuration
  -- options to `gitsigns.nvim`. This is equivalent to the following Lua:
  --    require('gitsigns').setup({ ... })
  --
  -- See `:help gitsigns` to understand what the configuration keys do
  -- { -- Adds git related signs to the gutter, as well as utilities for managing changes
  --   'lewis6991/gitsigns.nvim',
  --   opts = {
  --     signs = {
  --       add = { text = '+' },
  --       change = { text = '~' },
  --       delete = { text = '_' },
  --       topdelete = { text = '‾' },
  --       changedelete = { text = '~' },
  --     },
  --   },
  -- },
```

-- vim: foldmethod=syntax ts=2 sts=2 sw=2 expandtab


