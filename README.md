# TCAdmin 3 — Community Plugin Repository

This repository contains community-contributed plugins for TCAdmin v3, including game configs, Docker blueprints, scripts, themes, language packs, and more.

> Looking for official plugins? See the [Official Plugin Repository](https://github.com/TotalControlAdmin/TCA3PluginRepo).

## Repository Structure

```
manifests/
├── games/                  # Game server configurations
├── docker-blueprints/      # Docker service blueprints
├── languages/              # Language/translation packs
├── script-modules/         # Reusable script modules
├── scripts/                # Standalone scripts
├── themes/                 # UI themes
└── manifest-schema.json    # JSON schema for manifest validation
```

Each plugin lives in its own folder under the appropriate category, organized by name and version:

```
manifests/games/YourGame/1.0.0/
├── manifest.yaml           # Required — describes your plugin
├── YourGame - Windows.json # Config file(s) referenced by the manifest
└── YourGame - Linux.json   # (optional additional configs)
```

## How to Submit a Plugin

### 1. Fork and Clone This Repository

Click the **Fork** button at the top of this page, then clone your fork:

```bash
git clone https://github.com/YOUR-USERNAME/TCA3CommunityRepo.git
cd TCA3CommunityRepo
```

### 2. Create Your Plugin Folder

Choose the correct category folder and create a directory for your plugin with a version number:

```bash
mkdir -p manifests/games/YourGame/1.0.0
```

### 3. Export and Add Your Config Files

Export the config from your TCAdmin panel and copy the JSON file(s) into the version folder:

```
manifests/games/YourGame/1.0.0/YourGame - Windows.json
manifests/games/YourGame/1.0.0/YourGame - Linux.json
```

### 4. Create a `manifest.yaml`

Every version folder **must** include a `manifest.yaml` that describes your plugin. Here's the format:

```yaml
# Unique identifier for your plugin (use a consistent prefix, e.g., Community.Games.YourGame)
identifier: Community.Games.YourGame

# Version of this release (should match the folder name)
version: 1.0.0

# Your name or username
author: YourName

# Display name shown in TCAdmin
name: Your Game

# One-line summary shown in the plugin browser
shortDescription: Your Game config for TCAdmin 3

# Detailed description (supports Markdown)
longDescription: |
  # Your Game

  A longer description of your game or plugin.
  You can use **Markdown** here for formatting.

  ## Features
  - Feature 1
  - Feature 2

# URL to an icon/logo image
icon: https://example.com/your-game-icon.png

# URLs to screenshot or preview images
images:
  - https://example.com/screenshot1.png

# Tags help users find your plugin (include the category and OS)
tags:
  - Game
  - Windows
  - Linux

# List of config files included in this version
files:
  - identifier: "game_config_windows"
    path: YourGame - Windows.json    # Filename relative to this folder
    type: GameConfig                  # File type (GameConfig, DockerBlueprint, Script, Theme, etc.)
    optional: false                   # Set to true if users can skip this file during install

  - identifier: "game_config_linux"
    path: YourGame - Linux.json
    type: GameConfig
    optional: true
```

### 5. Commit and Push

Create a new branch, commit your files, and push to your fork:

```bash
git checkout -b add-yourgame
git add .
git commit -m "Add YourGame config v1.0.0"
git push origin add-yourgame
```

### 6. Open a Pull Request

Go to your fork on GitHub and click **New Pull Request** to submit your plugin to this repository. In your PR description, briefly explain what the plugin does and confirm that you've tested it.

A maintainer will review your submission and merge it once everything looks good.

## Updating an Existing Plugin

To release a new version, create a new version folder alongside the existing one:

```
manifests/games/YourGame/
├── 1.0.0/
│   ├── manifest.yaml
│   └── YourGame - Windows.json
└── 1.1.0/                          # New version
    ├── manifest.yaml                # Updated version field
    └── YourGame - Windows.json      # Updated config
```

Then open a PR the same way.

## Guidelines

- **Test your configs** before submitting — make sure they work on a clean TCAdmin v3 installation.
- **Use clear names** for your plugin and files so other users can easily identify them.
- **Keep descriptions helpful** — include what the game/plugin does and any setup steps users should know about.
- **One plugin per PR** makes reviews faster and easier.

## Questions or Feedback

Have questions or want to discuss ideas? Visit the [TCAdmin v3 Discussions](https://github.com/TotalControlAdmin/TCAdmin-V3-Issues-and-Feedback/discussions).
