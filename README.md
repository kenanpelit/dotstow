# dotstow

A powerful dotfiles manager built with GNU Stow for efficient configuration management

> **Note**: This dotfiles manager is used to manage [kenanpelit/dotfiles](https://github.com/kenanpelit/dotfiles)

## Features
- 🎯 **Group-based Configuration**: Manage related dotfiles together using groups defined in `groups.conf`
- 🔄 **Smart Symlinking**: Automated symlinking using GNU Stow
- 📁 **Flexible Structure**: Support for both `~/.config` and home directory files
- 🎨 **Multiple Config Support**: Handle multiple configuration files per group
- 🔍 **Dry Run**: Preview changes before applying them
- 🚀 **Easy Import/Export**: Selectively import configurations based on groups
- 📋 **Organized Management**: Clear organization of your dotfiles with a structured approach

## Requirements

- GNU Stow
- Bash 4.0+

## Installation

1. Clone the repository:
```bash
git clone https://github.com/yourusername/dotstow.git ~/.dotstow
```

2. Make the script executable:
```bash
chmod +x ~/.dotstow/dotfiles-manager.sh
```

3. (Optional) Create a symlink to make it globally available:
```bash
sudo ln -s ~/.dotstow/dotfiles-manager.sh /usr/local/bin/dotstow
```

## Directory Structure

```
~/.dotfiles/                    # Main dotfiles directory
├── groups.conf                 # Group definitions file
├── zsh/                        # Example group directory
│   ├── .zshrc                 # Home directory files
│   ├── .zprofile
│   └── .config/               # .config directory files
│       └── zsh/
│           └── aliases
└── starship/                  # Example with multiple configs
    └── .config/
        ├── starship.toml      # Main config
        └── starship/          # Theme directory
            ├── theme1.toml
            └── theme2.toml
```

## Usage

### Basic Commands

```bash
# Add a single configuration file
dotstow add .zshrc

# Remove a configuration
dotstow rm zsh

# Synchronize all dotfiles
dotstow sync

# List existing dotfiles
dotstow ls
```

### Group Management

```bash
# Add a new group
dotstow group add zsh '.zshrc,.zprofile' zsh

# Add a config-only group
dotstow group add nvim '' nvim

# List all groups
dotstow group ls

# Remove a group definition
dotstow group rm zsh
```

### Import/Export

```bash
# Import all configurations from groups.conf
dotstow import

# Import specific groups
dotstow import nvim zsh

# Preview import (dry-run)
dotstow import --dry-run zsh
```

## groups.conf Format

The `groups.conf` file uses the following format:
```
group_name:home_files:config_dir
```

Example entries:
```
zsh:.zshrc,.zprofile,.zshenv:zsh
nvim::nvim
bash:.bashrc,.bash_profile:
starship:.config/starship.toml,.config/starship:starship
```

- `group_name`: Name of the configuration group
- `home_files`: Comma-separated list of files in home directory (optional)
- `config_dir`: Directory name in .config (optional)

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
