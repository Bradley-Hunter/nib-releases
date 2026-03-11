# Nib

A context-aware clipboard manager for Windows that replaces the built-in Win+V clipboard history with a smarter alternative.

Nib remembers **where** you copied something. When you open the popup, it defaults to showing only clips from the app you're currently pasting into — so if you're working in VS Code, you see your VS Code copies first. Toggle to see everything.

## Features

- **Context-aware sorting** — clips filtered by the app you're pasting into, with toggles for all clips and pinned-only views
- **Full format fidelity** — stores all clipboard formats (text, HTML, RTF, images, files) and restores them on paste
- **Pin clips and apps** — pin frequently used clips; pin apps to the sidebar for quick filtering
- **Three view modes** — This App, All Clips, and Pinned, with left/right arrow keys to cycle between them
- **Keyboard-driven** — arrow keys to navigate clips and views, Enter to paste, Escape to dismiss
- **Smart positioning** — popup appears near your text cursor using a multi-layer detection strategy
- **Auto-updater** — checks GitHub Releases daily, downloads updates in the background, applies on restart
- **Dark/light theme** — follows your Windows system theme automatically
- **Export/import** — back up your clipboard history as JSON
- **Lightweight** — single binary, SQLite storage, minimal resource usage

## Installation

1. Download the latest `NibSetup-x.x.x.exe` from [Releases](https://github.com/Bradley-Hunter/nib-releases/releases)
2. Run the installer
3. Restart your computer (required for the clipboard policy change to take effect)

The installer will:

- Install Nib to Program Files
- Disable the built-in Windows clipboard history via system policy (restored on uninstall)
- Optionally add Nib to startup

## Usage

1. **Launch Nib** — it runs in the system tray.
2. **Copy things** as you normally would. Nib records each clip along with its source app.
3. **Press Win+V** to open the popup near your cursor.
4. **Click or press Enter** on a clip to paste it.

### Popup controls

| Action | Effect |
|--------|--------|
| **Click** / **Enter** | Paste the selected clip |
| **Up/Down arrows** | Navigate the clip list |
| **Left/Right arrows** | Cycle between views (This App, All Clips, Pinned) |
| **Escape** | Dismiss without pasting |
| **Right-click** | Pin/unpin, delete, copy, or pin the source app |

### Views

- **This App** (default) — shows clips from the same app you're pasting into, sorted by recency
- **All Clips** — shows everything, sorted by recency
- **Pinned** — shows only pinned clips, sorted by recency

Use left/right arrow keys to cycle between views. If a sidebar tab is selected, it becomes part of the cycle.

### Pinned apps sidebar

Pin frequently-used apps to the left sidebar for one-click filtering. Right-click any clip and select "Pin App", or manage pinned apps in Settings.

## Configuration

Nib stores its config at `%APPDATA%\Nib\config.toml`. You can edit it directly or use the Settings GUI (right-click the tray icon → Settings).

| Setting | Default | Description |
|---------|---------|-------------|
| `hotkey` | `Win+V` | Global hotkey to open the popup |
| `max_clips` | `200` | Maximum stored clips (0 = unlimited) |
| `max_storage_mb` | `100` | Maximum disk usage in MB |
| `max_clip_size_mb` | `50` | Maximum size of a single clip in MB |
| `theme` | `system` | `dark`, `light`, or `system` |
| `default_view` | `app_only` | `app_only`, `all`, or `pinned` |
| `excluded_apps` | `[]` | Apps to ignore (e.g., password managers) |
| `pinned_apps` | `[]` | Apps pinned to the sidebar |
| `auto_start` | `true` | Launch on Windows startup |
| `auto_update_check` | `true` | Enable automatic daily update checks |
| `auto_install_updates` | `false` | Download and stage updates automatically (applies on restart) |

## Uninstalling

Use the standard Windows "Add or remove programs" to uninstall. The uninstaller will:

- Remove all Nib files and user data (`%APPDATA%\Nib`)
- Restore the built-in Windows clipboard history
- Remove the startup entry

## License

All rights reserved.
