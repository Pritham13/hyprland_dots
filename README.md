# Hyprland Configuration

A comprehensive Hyprland window manager configuration with custom keybindings, window rules, monitor setup, wallpaper management, and utility scripts.


## 📁 Repository Structure

```
.config/hypr/
├── hyprland.conf           # Main configuration file (sources other configs)
├── binds.conf              # Keybindings (workspace, window, media controls)
├── window_rules.conf       # Window-specific rules and floating behaviors
├── monitor.conf            # Monitor and resolution settings
├── hyprpaper.conf          # Wallpaper configuration
├── hyprland-gui.conf       # GUI-specific settings (currently empty)
├── scripts/                # Utility scripts for system configuration
│   ├── git_init.sh         # SSH agent initialization for git
│   ├── igpu.sh             # GPU switching (integrated GPU mode)
│   ├── WallustSwww.sh      # Wallust color generation for wallpaper
│   ├── WaybarCava.sh       # Audio visualizer setup
│   ├── WaybarLayout.sh     # Waybar layout configuration
│   └── WaybarStyles.sh     # Waybar styling
└── README.md               # Original readme

```

## 🔧 Dependencies

### Core Requirements
- `hyprland` - Window manager
- `hyprpaper` - Wallpaper daemon
- `kitty` - Terminal emulator (configured default)
- `dolphin` - File manager (configured default)
- `firefox` - Primary browser
- `brave-browser` - Secondary browser

### Input & Display
- `waybar` - Status bar
- `rofi` - Application launcher
- `brightnessctl` - Brightness control
- `wpctl` - Volume/audio control

### Utilities & Scripts
- `wl-paste` - Clipboard management
- `cliphist` - Clipboard history
- `grimblast` - Screenshot utility
- `playerctl` - Media player control
- `swww` - Wallpaper daemon (for Wallust script)
- `wallust` - Color scheme generation (for Wallust script)
- `supergfxctl` - GPU control utility (for igpu script)
- `ssh-agent` - SSH key management (for git_init script)

### Optional
- `nm-applet` - Network manager applet (configured in autostart)

## ⌨️ Key Features

### Keybindings

#### Window Management
| Key Combination | Action |
|---|---|
| `Alt + Return` | Open terminal |
| `Alt + Q` | Kill active window |
| `Alt + V` | Toggle floating window |
| `Alt + P` | Toggle pseudotiling (dwindle) |
| `Alt + T` | Toggle split layout |
| `Alt + SHIFT + F` | Fullscreen |

#### Navigation & Focus
| Key Combination | Action |
|---|---|
| `Alt + H/L` | Move focus left/right |
| `Alt + K/J` | Move focus up/down |
| `Alt + 1-9/0` | Switch to workspace 1-10 |

#### Window Operations
| Key Combination | Action |
|---|---|
| `Alt + SHIFT + H/L/K/J` | Resize window left/right/up/down |
| `Alt + SHIFT + 1-9/0` | Move window to workspace 1-10 |
| `Super + V` | Open clipboard history |

#### Applications & Special
| Key Combination | Action |
|---|---|
| `Alt + SPACE` | Open application launcher (rofi) |
| `Alt + E` | Open file manager |
| `Alt + F` | Open Firefox |
| `Alt + D` | Open Brave Browser |
| `Alt + S` | Toggle special workspace (scratchpad) |
| `Alt + SHIFT + S` | Move window to special workspace |
| `Alt + Print` | Screenshot active window |
| `Alt + SHIFT + Print` | Screenshot area |
| `Alt + ESC` | Exit Hyprland |


#### Workspace Navigation
| Input | Action |
|---|---|
| `Alt + Mouse Scroll` | Switch workspaces |
| `Alt + LMB + Drag` | Move windows |
| `Alt + RMB + Drag` | Resize windows |


### Monitor Setup
- **eDP-1** (Laptop Screen): 1920x1080@143.98Hz, primary
- **HDMI-A-1** (External): 1920x1080@99.93Hz, positioned left of DP-1

## 🚀 Setup Instructions for Zsh

### 1. Initial Installation

Copy the configuration directory to your user's config folder:

```bash
# Ensure the directory structure exists
mkdir -p ~/.config/hypr

# Copy all configuration files to the location
cp -r /path/to/this/repo/* ~/.config/hypr/
```

### 2. Make Scripts Executable

Grant execute permissions to all scripts:

```bash
chmod +x ~/.config/hypr/scripts/*.sh
```

### 3. Configure Your Zsh Shell

Add the following to your `~/.zshrc` to integrate Hyprland configuration:


### 4. Wallpaper Configuration

Update wallpaper paths in `~/.config/hypr/hyprpaper.conf`:

```bash
# Edit the configuration
$EDITOR ~/.config/hypr/hyprpaper.conf

# Change these lines to your wallpaper paths:
preload = ~/Pictures/wallpapers/your-wallpaper.jpg
wallpaper = ,~/Pictures/wallpapers/your-wallpaper.jpg
```

### 5. Monitor Configuration

Edit `~/.config/hypr/monitor.conf` to match your display setup:

```bash
# View current monitor info
hyprctl monitors

# Edit the configuration
$EDITOR ~/.config/hypr/monitor.conf

# Update with your monitor names and resolutions
monitor=DP-1,1920x1080@60,0x0,1.0
monitor=HDMI-1,1920x1080@60,1920x0,1.0
```

### 6. Customize Default Programs

Edit `~/.config/hypr/hyprland.conf` and modify the "MY PROGRAMS" section:

```bash
# Change terminal
$terminal = kitty          # or: alacritty, gnome-terminal, etc.

# Change file manager
$fileManager = dolphin     # or: thunar, nautilus, etc.

# Change browsers
$browser1 = firefox        # primary browser
$browser2 = brave-browser  # secondary browser
```

### 7. SSH Setup for Scripts

If using the `git_init.sh` script, ensure your SSH key exists:

```bash
# Generate SSH key if needed
ssh-keygen -t ed25519 -f ~/.ssh/git

# The script will automatically load it via ssh-agent
```

### 8. GPU Configuration

For laptop users with integrated/dedicated GPU switching:

```bash
# Check available GPU profiles
supergfxctl -l

# To auto-switch to integrated GPU at startup, the igpu.sh script will handle it
# Modify igpu.sh if you need different GPU settings
$EDITOR ~/.config/hypr/scripts/igpu.sh
```


## 📝 Configuration Files Explained

### `hyprland.conf`
Main configuration entry point. Defines:
- Program variables
- Autostart services
- Display settings (gaps, borders, colors)
- Animations and effects
- Input settings
- Sourced other config files

### `binds.conf`
All keybindings organized by category:
- Window management
- Workspace switching
- Application launchers
- Media controls
- Screenshot utilities
- Clipboard history

### `window_rules.conf`
Floating window rules and initial sizes for specific applications.

### `monitor.conf`
Display configuration including resolution, refresh rate, and positioning.

### `hyprpaper.conf`
Wallpaper daemon settings and image paths.

### `scripts/`
Utility scripts for:
- **git_init.sh**: SSH agent setup
- **igpu.sh**: GPU switching
- **WallustSwww.sh**: Generate color schemes from wallpaper
- **WaybarCava.sh**: Audio visualizer
- **WaybarLayout.sh**: Status bar layout
- **WaybarStyles.sh**: Status bar styling

## 🔌 Autostart Services

The following services start automatically with Hyprland:

```bash
nm-applet              # Network manager
waybar                 # Status bar
hyprpaper              # Wallpaper daemon
wl-paste (text)        # Clipboard monitor for text
wl-paste (image)       # Clipboard monitor for images
```

## 🎨 Customization Tips

- **Change colors**: Edit the `col.active_border` and `col.inactive_border` in `hyprland.conf`
- **Adjust gaps/borders**: Modify `gaps_in`, `gaps_out`, and `border_size` values
- **Add window rules**: Append to `window_rules.conf` using `windowrulev2` directives
- **Create new keybinds**: Add to `binds.conf` (see Hyprland wiki for syntax)
- **Modify animations**: Adjust bezier curves and animation speeds in `hyprland.conf`

## 📚 Resources

- [Hyprland Wiki](https://wiki.hypr.land/)
- [Hyprland Configuration](https://wiki.hypr.land/Configuring/Configuring-Hyprland/)
- [Keybinding Documentation](https://wiki.hypr.land/Configuring/Binds/)
- [Window Rules](https://wiki.hypr.land/Configuring/Window-Rules/)

