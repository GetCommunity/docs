# tmux

## Configuration

Edit the `~/.tmux.conf` file to customize your tmux configuration. Below is an example of a basic configuration that changes the prefix key to Ctrl+a, which is a common choice among tmux users.

```bash
# ~/.tmux.conf
# Set true color (24-bit color) support
set-option -sa terminal-overrides ",xterm:Tc"

# Set prefix
unbind C-b
set -g prefix C-a
bind C-a send-prefix

# Enable mouse support
set -g mouse on

# Easier pane navigation
bind -n M-Left select-pane -L
bind -n M-Right select-pane -R
bind -n M-Up select-pane -U
bind -n M-Down select-pane -D

# List of plugins
set -g @plugin 'tmux-plugins/tpm'
set -g @plugin 'tmux-plugins/tmux-sensible'

# Other examples:
# set -g @plugin 'github_username/plugin_name'
# set -g @plugin 'github_username/plugin_name#branch'
# set -g @plugin 'git@github.com:user/plugin'
# set -g @plugin 'git@bitbucket.com:user/plugin'

# Initialize TMUX plugin manager (keep this line at the very bottom of tmux.conf)
run '~/.tmux/plugins/tpm/tpm'
```

```bash
# Reload tmux configuration without restarting
Ctrl+b r
Ctrl+a r
```

## Basic Commands

| Command                       | Action                            |
|-------------------------------|------------------------------------|
| `tmux new -s session_name`    | Create a new tmux session          |
| `tmux ls`                     | List all tmux sessions             |
| `tmux attach -t session_name` | Attach to an existing tmux session |

## Window Management

| Command    | Action                          |
|------------|---------------------------------|
| `Ctrl+a c` | Create a new tmux window        |
| `Ctrl+a w` | List all windows                |
| `Ctrl+a n` | Switch to the next window       |
| `Ctrl+a p` | Switch to the previous window   |
| `Ctrl+a ,` | Rename the current window       |
| `Ctrl+a d` | Detach from the current session |

## Pane Management

| Command            | Action                                |
|--------------------|---------------------------------------|
| `Ctrl+a arrow key` | Move between panes                    |
| `exit`             | Close the current pane                |
| `Ctrl+a %`         | Split the current window vertically   |
| `Ctrl+a "`         | Split the current window horizontally |

## Scroll Mode

| Command    | Action            |
|------------|-------------------|
| `Ctrl+a [` | Enter scroll mode |
