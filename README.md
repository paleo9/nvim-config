# nvim-config

My neovim configuration started as a clone from 
[kickstart.nvim](https://github.com/nvim-lua/kickstart.nvim)

## Config files and Markdown documentation

Config files are xxx.lua files, the central one being init.lua.

Each config file should have an accompanying markdown file for documentation
(xxx.lua.md) in the Doc directory.

The markdown file is able to contain much more detailed information than
comments could sensibly provide, so comments in config files should be rare and
only one or two lines long.

Plugins will be referenced in init.lua. Each plugin should have its own config
file and markdown file.

    plugin-name.lua => plugin-name.lua.md

As plugin config files and documentation take time to produce, unused plugins
may keep their config and documentation.

## Files in this directory

* Doc/:
    Directory containing markdown files to accompany the lua files. Allows decluttering source files and more detailed notes with better formatting.

* init.lua Doc/init.lua.md:
    The main config and documentation files for my nvim. Contains all settings except for plugin configuration. 

* plugin-name.lua Doc/plugin-name.lua.md:
    Config and documentation for a plugin.

