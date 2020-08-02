## Commonly used commands

- Move forward to the next occurence of `g`: `fg`
- Change word: `cw`
- Write to the sudo command with the current filename: `:w !sudo tee %`
- Change directory and edit file: `:cd ~/wiki` + `:e vim.md`
- View directory listing from vim: `:e .`
- Open project with NERDTree within vim: `:NERDTree ~/projects/pybot`
- Visual mode with previously selected area reselected: `:vmap > >gv`
- Declare abbr for insert mode: `iab ff Firefox`

## Buffers & Windows

- Split horizontally: `ctrl-w s`
- Split vertically: `ctrl-w v`
- Move focus down: `ctrl-w j`
- Cycle focus: `ctrl-w w`
- Focus previous: `ctrl-w p`
- Close window: `ctrl-w c`
- Close all but current: `ctrl-w o`
- Resize window: `ctrl-w +-`
- Move buffer up on window: `ctrl-w J`
- Move buffer down on window: `ctrl-w K`
- Switch to buffer: `:b name`
- Previous buffer: `:bp`
- Next buffer: `:bn`
- Delete buffer: `:bd`

## Search & Replace

- Find current word: `*`
- Replace dev with prod in the current buffer: `:%s/dev/prod`
- Flags for replace: 
  * `c` - confirm or skip each match
  * `i` - ignore case
  * `I` - case sensitive
  * `n` - show number of matches
  * `p` - print matching lines
  * `g` - global
- Replace in current line: `:s/dev/prod`
- Show all lines matching reg exp: `:g/re/p`
- Search with very magic syntax: `/\v(.y){3}`

## Map

- `nmap` - normal mode
- `imap` - insert mode
- `vmap` - visual mode
- `map` - normal, visual and operating-pending modes
- `map!` - command and insert modes
- `nnoremap` - swap keys 
