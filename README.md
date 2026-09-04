# tmux2kitty
# Native Kitty tabs for tmux and remote sessions

> **Use Kitty's native tabs with persistent tmux sessions — including remote sessions.**

If you're looking for a terminal emulator that natively works with tmux or GNU Screen, tmux2kitty brings tmux's persistent sessions together with Kitty's tabs—giving you the best of both worlds.

**tmux is the modern replacement for GNU Screen.** It keeps your terminal sessions, windows, and processes alive even when you disconnect. `tmux2kitty` lets Kitty display those tmux windows as **native Kitty tabs**, so you get the persistence of tmux without giving up Kitty's tab management.

It can:

* Attach to an existing local or **remote tmux session** and recreate its windows as native Kitty tabs.
* Automatically **resume remote tmux sessions** when you open Kitty again.
* Keep Kitty tabs synchronized with tmux as windows are created, renamed, or closed.
* Turn newly created tmux windows into Kitty tabs automatically.

**tmux keeps your sessions alive. Kitty provides the native terminal UI. `tmux2kitty` connects them.**

---------

## Features

- **Native Kitty Tabs:** Each tmux window gets its own native Kitty tab.
- **Resume Existing Sessions:** Attach to an existing tmux session and automatically recreate all of its windows as native Kitty tabs, so you can continue your persistent tmux workflow right where you left off.
- **Remote & Local Support:** Works smoothly over SSH with resilient control masters or locally on your machine.
- **Dynamic Tab Renaming:** Automatically syncs Kitty tab titles with your active tmux window names and indices (`index-name`).
- **Auto-Syncing:** Automatically maps, sorts, and cleans up tabs to mirror your tmux window states.
- **Zero Heavy Dependencies:** Written entirely in pure Bash with minimal requirements (`kitty`, `tmux`, `jq`, and a Python helper for tab sorting).
- **Resilient Reconnections:** Handles network drops gracefully when running over remote SSH.

---------

## Prerequisites

Make sure you have the following installed on your machine:
- **Operating System:** Tested and working on **Ubuntu 26.04 Linux** (compatible with other Linux distributions supporting Bash, Kitty, and tmux).
- **[Kitty](https://sw.kovidgoyal.net/kitty/)** terminal emulator (version with remote control support)
- **`tmux`** installed both locally and on your remote target (if using remote mode)
- **`jq`** command-line JSON processor (used for tracking and updating tab titles)
- **Python 3** (used internally for precise tab sorting/matching)
### Ubuntu / Debian

Install the required packages:

   ```bash
      sudo apt update
      sudo apt install tmux jq python3
   ```

Install Kitty:
   ```bash
      sudo apt install kitty
   ```
---------

## Installation & Setup

1. Clone or download the script:
   ```bash
       git clone https://github.com/rambkk/tmux2kitty.git
       cd tmux2kitty
   ```

2. Make the script executable:
   ```bash
       chmod +x tmux2kitty
   ```

---------

## Usage

Run the script by specifying either a remote SSH host or `local`, optionally followed by a tmux session name.

### Examples

- **Resume an existing remote session:** If you already have a tmux session running with multiple windows, simply specify the session and `tmux2kitty` will create a native Kitty tab for each existing window.
   ```bash
      ./tmux2kitty user@my-server.com -t mysession
   ```
  Once connected, the existing tmux windows are mapped to Kitty tabs automatically. Any new tmux windows you create are also synchronized, and closed windows are removed from Kitty.

- **Connect to a remote server:** Prompts you to select a tmux session.
   ```bash
      ./tmux2kitty user@my-server.com
   ```

- **Run locally:** Uses the default or selected tmux session.
   ```bash
      ./tmux2kitty local
   ```

- **Run locally with a specific session:**
   ```bash
      ./tmux2kitty local -t dev-environment
   ```

---------

## Keybindings (Optional Kitty Integration)

Add the keybindings provided in the `kitty.conf` file to your `~/.config/kitty/kitty.conf` to switch between your synchronized tabs instantly:

- **`Ctrl + Left_arrow`** / **`Ctrl + Right_arrow`**: Previous / next tab
- **`Ctrl + 0`** through **`Ctrl + 9`**: Go directly to a specific tab index

---------

## License

Copyright (C) 2026 Ram Narula  
This project is licensed under the terms of the MIT License.  
(See the [LICENSE](LICENSE) file for the full license text.)

