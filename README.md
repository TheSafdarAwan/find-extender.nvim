## Description

This Plugin **extends** the capability of find, till and y/d/c command's in nvim.
By Default **neovim** only accepts one character when finding for pattern. This
plugin give's you more power over how the finding commands and d/c/y commands
behave and how many characters they can accepts as input.

🔥 This Plugins Effects the following commands:

    f|F (find commands)
    t|T (till commands)
    ;|, (repeat last pattern commands)
    c{t|T|f|f} (change command)
    d{t|T|f|f} (delete command)
    y{t|T|f|f} (yank command)

By default after pressing any of these commands now you have to type two
characters(or more you can specify characters length) rather than One to
go to next position.

## ✨ Features

- **pattern limit**: adds capability to accept more characters for finding command's pattern.
- **y/d/c**: yank/delete/change(y/d/c) text with same capability as the finding commands.
- **timeout**: You can enable timeout to find the pattern before your character
  specified limit has completed. Even if you only gave _1_ character as an input.
  You can control that as well.
- **count**: accepts count before finding key or after in case of y/d/c keys.
- **UI Related**: Highlight the yanked area using `highlight.range`(see :h vim.highlight.range()).

## 🚀 Usage

<!-- #### count -->
<!-- TODO: add gif demo and then explanation. -->

<!-- ### yank/change/delete -->
<!--  TODO: add more gif demos using count and subject related demos -->
<!-- #### yank -->
<!-- #### change -->
<!-- #### delete -->

#### find forward

<img alt="f command" src="https://github.com/TheSafdarAwan/assets/blob/main/find-extender.nvim/fir.gif">

#### find backwards

<img alt="F command" src="https://github.com/TheSafdarAwan/assets/blob/main/find-extender.nvim/backwards_Fir.gif">

#### delete

<img alt="d command" src="https://github.com/TheSafdarAwan/assets/blob/main/find-extender.nvim/dtir.gif">

## 📦 Installation

Install with your preferred package manager:

[vim-plug](https://github.com/junegunn/vim-plug)

```vim
Plug 'TheSafdarAwan/find-extender.nvim'
```

[packer](https://github.com/wbthomason/packer.nvim)

```lua
use {
    opt = true,
    "TheSafdarAwan/find-extender.nvim",
    -- to lazy load this plugin
    keys = {
        { "v", "f" },
        { "v", "F" },
        { "n", "f" },
        { "n", "F" },
        { "n", "T" },
        { "n", "t" },
        { "v", "T" },
        { "v", "t" },
        { "n", "c" },
        { "n", "d" },
        { "n", "y" },
    },
    config = function()
        -- configuration here
    end,
}
```

## Setup

```lua
require("find-extender").setup({
    -- if you want do disable the plugin the set this to false
    enable = true,
    -- how many characters to find for
    chars_length = 2, -- default value is 2 chars
    -- timeout before the find-extender.nvim goes to find the available
    -- characters on timeout after the limit of start_timeout_after_chars
    -- has been reached
    -- timeout in ms
    timeout = false, -- false by default
    -- timeout starting point
    start_timeout_after_chars = 2, -- 2 by default
    -- key maps config
    keymaps = {
        modes = "nv",
        till = { "T", "t" },
        find = { "F", "f" },
        -- to delete, copy or change using t,f or T,F commands
        text_manipulation = {
            -- yank
            yank = { "f", "F", "t", "T" },
            -- delete
            delete = { "f", "F", "t", "T" },
            -- change
            change = { "f", "F", "t", "T" },
        },
    },
    highlight_on_yank = {
        -- whether to highlight the yanked are or not
        enable = true,
        -- time for which the area will be highlighted
        timeout = 40,
        -- highlight group for the yanked are color
        hl_group = "IncSearch",
    }
})
```

## Commands

There are three commands available.

- FindExtenderDisable
- FindExtenderEnable
- FindExtenderToggle

## ⚙️ Configuration

### chars_length

You can change the amount of characters you want to find by specifying the amount in
this key.

```lua
-- how many characters to find for
chars_length = 2 -- default value is 2 chars
```

Default is _2_ characters and more than that is not recommended because it will slow you down
and that's not what i intend this plugin to do.

### timeout

Timeout before the find-extender.nvim goes to find the characters that you have entered.
before you complete the chars_length character's limit.

```lua
-- timeout in ms
timeout = false -- false by default
```

### start_timeout_after_chars

How many characters after which the timeout should be triggered.

```lua
start_timeout_after_chars = 1, -- 1 by default
```

### ⌨ keymaps

Keymaps are exposed to user if any key you want to remove just remove it from the
tbl

```lua
keymaps = {
    modes = "nv",
    till = { "T", "t" },
    find = { "F", "f" },
},
```

Modes is a string with the modes name initials.

### text_manipulation

Mappings related to the text manipulation like change, delete and yank(copy).
If you want to disable any of the macro then set it to false.

```lua
keymaps = {
    ...,
    -- to delete, copy or change using t,f or T,F commands
    text_manipulation = {
        -- yank
        yank = { "f", "F", "t", "T" },
        -- delete
        delete = { "f", "F", "t", "T" },
        -- change
        change = { "f", "F", "t", "T" },
    },
}
```

### highlight on yank

These options control the highlight when yanking text.

```lua
highlight_on_yank = {
    -- whether to highlight the yanked are or not
    enable = true,
    -- time for which the area will be highlighted
    timeout = 40,
    -- highlight group for the yanked are color
    hl_group = "IncSearch",
}
```

### Related Plugins

👉 Written in vimscript

- [vim-easymotion](https://github.com/easymotion/vim-easymotion)
- [vim-sneak](https://github.com/justinmk/vim-sneak)
- [clever-f.vim](https://github.com/rhysd/clever-f.vim)

👉 Written in lua

- [leap.nvim](https://github.com/ggandor/leap.nvim),
- [lightspeed.nvim](https://github.com/ggandor/lightspeed.nvim)
- [flit.nvim](https://github.com/ggandor/flit.nvim/)
