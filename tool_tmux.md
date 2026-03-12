# tmux

## Configuration

Edit the `~/.tmux.conf` file to customize your tmux configuration. Below is an example of a basic configuration that changes the prefix key to Ctrl+b, which is a common choice among tmux users.

code ~/.tmux.conf

```bash
# ~/.tmux.conf
# Set true color (24-bit color) support
set-option -sa terminal-overrides ",xterm:Tc"

# # Set prefix to Ctrl+a (instead of the default Ctrl+b)
# unbind C-b
# set -g prefix C-a
# bind C-a send-prefix

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
```

## Basic Commands

| Command                             | Action                             |
|-------------------------------------|------------------------------------|
| `tmux new -s session_name`          | Create a new tmux session          |
| `tmux ls`                           | List all tmux sessions             |
| `tmux attach -t session_name`       | Attach to an existing tmux session |
| `tmux kill-session -t session_name` | Terminate an existing tmux session |

## Window Management

| Command    | Action                          |
|------------|---------------------------------|
| `Ctrl+b c` | Create a new tmux window        |
| `Ctrl+b w` | List all windows                |
| `Ctrl+b n` | Switch to the next window       |
| `Ctrl+b p` | Switch to the previous window   |
| `Ctrl+b ,` | Rename the current window       |
| `Ctrl+b d` | Detach from the current session |

## Pane Management

| Command            | Action                                |
|--------------------|---------------------------------------|
| `Ctrl+b arrow key` | Move between panes                    |
| `exit`             | Close the current pane                |
| `Ctrl+b %`         | Split the current window vertically   |
| `Ctrl+b "`         | Split the current window horizontally |

## Scroll Mode

| Command    | Action            |
|------------|-------------------|
| `Ctrl+b [` | Enter scroll mode |

## Persistent Sessions

First clone `tpm` (tmux plugin manager) to manage your tmux plugins:

```bash
git clone https://github.com/tmux-plugins/tpm ~/.tmux/plugins/tpm
```

Edit your `~/.tmux.conf` file to include the following lines to enable the tmux plugin manager and add any desired plugins:

```bash
set -g @plugin 'tmux-plugins/tpm'
set -g @plugin 'tmux-plugins/tmux-resurrect'
set -g @plugin 'tmux-plugins/tmux-continuum'

# Enable automatic restore upon tmux server start
set -g @continuum-restore 'on'

# Initialize TMUX plugin manager (keep this line at the very bottom of tmux.conf)
run '~/.tmux/plugins/tpm/tpm'
```
