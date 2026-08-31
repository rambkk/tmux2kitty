# tmux2kitty
Turn tmux windows into native Kitty tabs.

> **Bridge tmux windows to native Kitty tabs using remote control sockets.**

`tmux2kitty` is a lightweight Bash utility that seamlessly maps your remote (or local) tmux windows into native, high-performance **Kitty** terminal tabs. It watches your tmux session in real time, auto-spawning or cleaning up native Kitty tabs as windows are created or destroyed, allowing you to enjoy Kitty's native GPU acceleration and tab management while maintaining persistent tmux workflows.

---------

## Features

- **Native Kitty Tabs:** Each tmux window gets its own dedicated, native Kitty tab.
- **Remote & Local Support:** Works smoothly over SSH with resilient control masters or locally on your machine.
- **Auto-Syncing:** Automatically maps, sorts, and cleans up tabs to mirror your tmux window states.
- **Zero Heavy Dependencies:** Written entirely in pure Bash with minimal requirements (`kitty`, `tmux`, and a Python helper for tab sorting).
- **Resilient Reconnections:** Handles network drops gracefully when running over remote SSH.

---------

## Prerequisites

Make sure you have the following installed on your machine:
- **[Kitty](https://sw.kovidgoyal.net/kitty/)** terminal emulator (version with remote control support)
- **`tmux`** installed both locally and on your remote target (if using remote mode)
- **Python 3** (used internally for precise tab sorting/matching)

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

### Examples:

- Connect to a remote server (prompts for session selection):
   ```bash
      ./tmux2kitty user@my-server.com
   ```

- Connect to a remote server and specify a session:
   ```bash
      ./tmux2kitty user@my-server.com -t mysession
   ```

- Run locally:
   ```bash
      ./tmux2kitty local
   ```

- Run locally with a custom session:
   ```bash
      ./tmux2kitty local -t dev-environment
   ```

---------

## Keybindings (Optional Kitty Integration)

Add the keybindings provided in the `kitty.conf` file to your ~/.config/kitty/kitty.conf to switch between your synchronized tabs instantly:

- **`Ctrl + Left_arrow`** / **`Ctrl + Right_arrow`**: Previous / next tab
- **`Ctrl + 0`** through **`Ctrl + 9`**: Go directly to a specific tab index

---------

## License

Copyright (C) 2026 Ram Narula  
This project is licensed under the terms of the MIT License.  
(See the [LICENSE](LICENSE) file for the full license text.)

