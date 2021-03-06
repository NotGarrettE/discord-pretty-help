![version](https://img.shields.io/pypi/v/discord-pretty-help) ![python](https://img.shields.io/badge/python-3.6+-blue)

# discord-pretty-help

An embed version of the built in help command for discord.py

Based on the DefaultHelpCommand that discord.py uses, but revised for embeds and cogs on individual pages that can be "scrolled" through with reactions.

## Installation

`pip install discord-pretty-help`

## Usage

Example of how to use it:

```python
from discord.ext import commands
from pretty_help import PrettyHelp

bot = commands.Bot(command_prefix="!", help_command=PrettyHelp())
```

### Optional Args

- `color` - Set the default embed color
- `active` - Set the time (in seconds) that the message will be active default is 30s
- `navigation` - Set the emojis that will control the help menu. Uses a `pretty_help.Navigation()` instance.

By default, the help will just pick a random color on every invoke. You can change this using the `color` argument:

```python
import discord
from discord.ext import commands
from pretty_help import PrettyHelp, Navigation



bot = commands.Bot(command_prefix="!")

# ":discord:743511195197374563" is a custom discord emoji format. Adjust to match your own custom emoji.
nav = Navigation(":discord:743511195197374563", "👎", "\U0001F44D")
color = discord.Color.dark_gold()

bot.help_command = PrettyHelp(navigation=nav, color=color, active=5)

```

The basic `help` command will break commands up by cogs. Each cog will be a different page. Those pages can be navigated with
the arrow embeds. The message is unresponsive after 30s of no activity, it'll remove the reactions to let you know.

![example](https://raw.githubusercontent.com/stroupbslayen/discord-pretty-help/master/images/example.gif)

# Changelog
## [1.1.0]
- Added `Navigation`
- Added category index page by default
- Conditional `help` command output in *`No Category`* page

# Notes:

- discord.py must already be installed to use this
- `manage-messages` permission is recommended so reactions can be removed automatically

