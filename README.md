# nvim-config

My neovim configuration forked from 
[kickstart.nvim](https://github.com/nvim-lua/kickstart.nvim)

## Config files and documentation

Config files are xxx.lua files, accompanying documentation for each config 
file should be in a markdown file (xxx.lua.md) in the Doc directory.

Comments in config files should be rare and only one or two lines long. The 
markdown file can contain much more detailed information than comments 
could sensibly provide. Overlong comments clutter the code.

Plugins have their own config file and markdown file plugin-name.lua, Doc/plugin-name.lua.md.
Any plugins required will be referenced in init.lua so there is no need to remove a plugin config file and/or its accompanying documentation, they may be kept in case they are wanted later.

## Files in this directory

File(s) | Purpose
|------- | -------
init.lua Doc/init.lua.md | The main config and documentation files for my nvim. Contains all settings except for plugin configuration. 
plugin-name.lua Doc/plugin-name.lua.md | Config and documentation for a plugin.
simple.lua | A bare bones config file to use as ```nvim -u ~/.config/nvim/simple.lua``` for little jobs.
Original/ | Directory containing the original files from kickstart repository.
Doc/ | Directory containing markdown files to accompany the lua files. Allows decluttering source files and more detailed notes with better formatting.
