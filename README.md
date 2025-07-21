# My Tmux Configuration

A clean, productivity-focused tmux setup with vim integration and smart navigation.

## Features

- 🎯 **Smart Navigation**: Seamless switching between tmux panes and vim splits
- 🎨 **Theme**: Clean custom theme with pink accents matching Neovim Catppuccin
- ⌨️ **Intuitive Keybindings**: Logical key mappings for splits and navigation
- 🔄 **Session Persistence**: Auto-save and restore sessions with resurrect/continuum
- 🎵 **Spotify Integration**: Control music without leaving your terminal
- 🖱️ **Mouse Support**: Full mouse support for selecting, scrolling, and resizing

## Installation

1. Backup your existing tmux configuration:
   ```bash
   mv ~/.tmux.conf ~/.tmux.conf.bak
   mv ~/.tmux ~/.tmux.bak
   ```

2. Clone this configuration:
   ```bash
   git clone git@github.com:sean-d/tmux.git ~/.config/tmux
   ```

3. Install TPM (Tmux Plugin Manager):
   ```bash
   git clone https://github.com/tmux-plugins/tpm ~/.tmux/plugins/tpm
   ```

4. Start tmux and install plugins:
   ```bash
   tmux
   # Press Ctrl+Space I (capital i) to install plugins
   ```
   
   All plugins will be automatically downloaded and installed. You'll see the installation progress in tmux.

## Key Mappings

Prefix key: `Ctrl+Space`

### Essential Commands
| Key | Description |
|-----|-------------|
| `Ctrl+Space r` | Reload tmux configuration |
| `Ctrl+Space I` | Install plugins |
| `Ctrl+Space U` | Update plugins |

### Window Management
| Key | Description |
|-----|-------------|
| `Ctrl+Space c` | Create new window |
| `Ctrl+Space ,` | Rename current window |
| `Alt+Left` | Previous window |
| `Alt+Right` | Next window |
| `Ctrl+Space &` | Close current window |

### Pane Management
| Key | Description |
|-----|-------------|
| `Ctrl+Space \|` | Split window vertically |
| `Ctrl+Space -` | Split window horizontally |
| `Ctrl+h/j/k/l` | Navigate between panes (vim-aware) |
| `Ctrl+d` or `exit` | Close current pane |

### Pane Resizing
| Key | Description |
|-----|-------------|
| `Alt+h` | Resize pane left (2 cells) |
| `Alt+l` | Resize pane right (2 cells) |
| `Alt+j` | Resize pane down (2 cells) |
| `Alt+k` | Resize pane up (2 cells) |

### Copy Mode & Scrolling
| Key | Description |
|-----|-------------|
| `Ctrl+Space [` | Enter copy mode |
| `q` | Exit copy mode |
| Mouse scroll | Scroll in pane (automatic copy mode) |

### Spotify Integration
| Key | Description |
|-----|-------------|
| `Ctrl+Space s` | Show Spotify menu with album art and controls |

**Note**: A popup notification appears in the bottom right when tracks change

## Features in Detail

### Vim Integration
The configuration includes smart pane navigation that works seamlessly with Neovim. When you press `Ctrl+h/j/k/l`, it will:
- Switch between tmux panes if you're not in vim
- Switch between vim splits if you're in vim
- Move from vim to tmux panes at vim window boundaries

### Status Bar
- **Left**: Session name with custom icon
- **Right**: Date and time
- **Center**: Window tabs with highlighting for active window (pink for active)

### Session Management
Sessions are automatically saved every 15 minutes and restored when tmux starts:
- **tmux-resurrect**: Save/restore sessions manually
- **tmux-continuum**: Automatic session saves

### Mouse Support
Full mouse support is enabled:
- Click to select panes
- Drag to resize panes
- Scroll to navigate content
- Select text to copy (in copy mode)

## Configuration Structure

```
~/.config/tmux/
└── tmux.conf          # Main configuration file

~/.tmux/
└── plugins/           # TPM managed plugins (git ignored)
    ├── tpm/
    ├── tmux-sensible/
    ├── tmux-resurrect/
    └── ...
```

## Customization

### Changing the Prefix Key
Edit `tmux.conf` and modify:
```bash
set -g prefix C-Space  # Change C-Space to your preferred key
```

### Modifying Keybindings
All keybindings are clearly commented in the configuration. Look for sections like:
- `##### Prefix and Keybindings #####`
- `##### Smart Pane Navigation #####`

### Adjusting Colors
The color scheme uses custom hex colors. Look for the Status Bar Configuration section in tmux.conf. The main accent color is pink (#f5c2e7) to match the Neovim Catppuccin theme.

## Plugins

### Core Plugins
- **tpm** - Tmux Plugin Manager
- **tmux-sensible** - Basic tmux settings everyone can agree on
- **tmux-resurrect** - Persist tmux sessions across system restarts
- **tmux-continuum** - Continuous saving of tmux environment

### Enhancement Plugins
- **tmux-spotify** - Spotify controls and now-playing notifications
- **vim-tmux-navigator** - Seamless navigation between vim and tmux

## Tips & Tricks

### Quick Window Switching
- Use `Alt+Left/Right` for fast window switching without prefix
- Number your frequently used windows for quick access with `Ctrl+Space [0-9]`

### Efficient Pane Layout
- After splitting, use `Ctrl+Space Space` to cycle through layouts
- Use `Ctrl+Space z` to zoom/unzoom a pane

### Copy & Paste
1. Enter copy mode: `Ctrl+Space [`
2. Navigate with vim keys (hjkl)
3. Start selection: `v`
4. Copy selection: `y`
5. Paste: `Ctrl+Space ]`

### Session Management
- Create named session: `tmux new -s project-name`
- Detach from session: `Ctrl+Space d`
- List sessions: `tmux ls`
- Attach to session: `tmux attach -t project-name`

## Troubleshooting

### Plugins not loading
1. Ensure TPM is installed in `~/.tmux/plugins/tpm`
2. Run `Ctrl+Space I` to install plugins
3. Restart tmux: `tmux kill-server && tmux`

### Colors look wrong
1. Ensure your terminal supports 256 colors
2. Check `$TERM` environment variable: `echo $TERM`
3. Should be `xterm-256color` or similar

### Prefix key not working
1. Ensure no other application is capturing `Ctrl+Space`
2. Try the reload command: `tmux source-file ~/.config/tmux/tmux.conf`

### Vim navigation not working
1. Install vim-tmux-navigator in your vim/neovim config
2. Ensure the `is_vim` detection in tmux.conf matches your vim executable

### Spotify plugin not working
1. Ensure Spotify app is installed and running
2. On macOS, grant Terminal/iTerm permission to control Spotify in System Preferences
3. If popup notifications stop working, remove and reinstall the plugin:
   ```bash
   rm -rf ~/.tmux/plugins/tmux-spotify
   # Then press Ctrl+Space I to reinstall
   ```

## Resources

- [Tmux Documentation](https://github.com/tmux/tmux/wiki)
- [TPM Documentation](https://github.com/tmux-plugins/tpm)
- [Tmux Cheat Sheet](https://tmuxcheatsheet.com/)
- [Vim-Tmux Navigator](https://github.com/christoomey/vim-tmux-navigator)