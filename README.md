# Neovim Configuration 🚀

A modern and complete Neovim configuration, optimized for development with LSP, autocompletion, and an elegant user interface.

## ✨ Features

- 🎨 **Tokyo Night Theme** - Modern dark interface
- 🔍 **Telescope** - Powerful fuzzy finder for files, buffers, and more
- 🌳 **Nvim-tree** - File explorer with icons
- 📝 **Built-in LSP** - Full Language Server Protocol support
- ⚡ **Intelligent Autocompletion** - nvim-cmp with snippets
- 🎯 **Treesitter** - Advanced syntax highlighting
- 🤖 **GitHub Copilot** - AI code assistant
- 🔧 **Mason** - LSP, DAP, linters and formatters manager
- ✅ **Conform** - Automatic code formatting
- 🐙 **Lazygit** - Git integration in Neovim
- 📊 **Lualine** - Elegant status line
- 🎭 **Which-key** - Keyboard shortcuts guide
- 🔔 **Noice** - Enhanced UI for messages
- 🌈 **Rainbow delimiters** - Colored parentheses
- 💬 **Chat** - AI chat integration
- 📋 **Bufferline** - Buffer management with tabs
- 🚨 **Trouble** - Diagnostics and quickfix list
- 📑 **Markdown** - Enhanced Markdown support

## 📋 Prerequisites

- https://github.com/BurntSushi/ripgrep
- https://www.nerdfonts.com
- https://wezterm.org
- https://mise.jdx.dev
- https://vincent.jousse.org/blog/fr/tech/configurer-neovim-comme-ide-a-partir-de-zero-tutoriel-guide/#tldr

Before installing this configuration, make sure you have:

- **Neovim >= 0.9.0** (recommended: latest stable version)
- **Git** - To clone the repository
- **Node.js** - Required for some LSP servers and GitHub Copilot
- **Python 3** - For some plugins and LSP servers
- **Ripgrep** - For searching with Telescope
- **A Nerd Font** - For proper icon display

### Recommended tools

- [Ripgrep](https://github.com/BurntSushi/ripgrep) - Ultra-fast search tool
- [Nerd Fonts](https://www.nerdfonts.com) - Fonts with integrated icons
- [WezTerm](https://wezterm.org) - Modern terminal emulator
- [mise](https://mise.jdx.dev) - Runtime version manager (alternative to asdf, nvm, pyenv, etc.)

## 🚀 Installation

### Complete installation

Clone the project into `~/.config/nvim`:

```bash
git clone https://github.com/stephen-shopopop/neovim ~/.config/nvim
```

Then launch Neovim. Plugins will be automatically installed thanks to **lazy.nvim**.

### System dependencies installation

#### mise

```bashbash
curl -fsSL https://mise.jdx.dev/install.sh | bash
```

Add `mise` to your shell:

```bash
// For Zsh
echo 'eval "$(~/.local/bin/mise activate zsh)"' >> ~/.zshrc

// For Bash
echo 'eval "$(~/.local/bin/mise activate bash)"' >> ~/.bashrc
```

Then install the required runtimes:

```bash
mise install
```

#### macOS

```bash
# Homebrew
brew install neovim ripgrep fd node python3

# Install a Nerd Font
brew tap homebrew/cask-fonts
brew install --cask font-jetbrains-mono-nerd-font
```

#### Linux (Debian/Ubuntu)

```bash
sudo apt update
sudo apt install neovim ripgrep fd-find nodejs npm python3 python3-pip
```

#### Arch Linux

```bash
sudo pacman -S neovim ripgrep fd nodejs npm python python-pip
```

## 📦 Included LSP servers

This configuration automatically installs the following LSP servers via Mason:

- **actionlint** - GitHub Actions
- **biome** - JavaScript/TypeScript (alternative to ESLint/Prettier)
- **markdownlint** - Markdown
- **cssls** - CSS
- **elmls** - Elm
- **graphql** - GraphQL
- **html** - HTML
- **lua_ls** - Lua
- **pylsp** - Python
- **ruff** - Python linter
- **rust_analyzer** - Rust
- **sqlls** - SQL
- **svelte** - Svelte
- **ts_ls** - TypeScript/JavaScript
- **yamlls** - YAML
- **vacuum** - OpenAPI

## ⌨️ Main keyboard shortcuts

The **Leader** key is set to **Space**.

### General

- `;;` - Exit insert mode (instead of `<ESC>`)
- `<leader>nh` - Clear search highlighting
- `Shift+I` - Move line/selection up (visual mode)
- `Shift+K` - Move line/selection down (visual mode)

### Navigation and files

- `<leader>ff` - Find a file (Telescope)
- `<leader>fg` - Global search in files (Telescope)
- `<leader>fb` - List buffers (Telescope)
- `<leader>e` - Toggle file explorer (Nvim-tree)

### LSP and code

- `gd` - Go to definition
- `gr` - Show references
- `K` - Show documentation (hover)
- `<leader>ca` - Code actions
- `<leader>rn` - Rename symbol
- `[d` / `]d` - Previous/next diagnostic

### Git

- `<leader>gg` - Open Lazygit
- `<leader>gd` - Show Git diff

To see all available shortcuts, press `<leader>` and wait for **Which-key** to display the guide.

## 🛠️ Customization

### Project structure

```bash
~/.config/nvim/
├── init.lua                 # Main entry point
├── lua/
│   ├── core/               # Base configuration
│   │   ├── init.lua        # Loading core modules
│   │   ├── options.lua     # Neovim options
│   │   └── keymaps.lua     # Global keybindings
│   ├── config/
│   │   └── lazy.lua        # Plugin manager configuration
│   └── plugins/            # Plugin configurations
│       ├── init.lua
│       ├── lsp/            # LSP configuration
│       │   ├── mason.lua
│       │   └── lspconfig.lua
│       ├── telescope.lua
│       ├── nvim-tree.lua
│       ├── treesitter.lua
│       └── ...
└── lazy-lock.json          # Plugin version lockfile
```

### Adding a plugin

Create a new file in `lua/plugins/`:

```lua
return {
  "author/plugin-name",
  config = function()
    -- Plugin configuration
  end,
}
```

### Adding an LSP server

Edit `lua/plugins/lsp/mason.lua` and add the server to `ensure_installed`.

## 🔧 Useful commands

### Plugin management (Lazy.nvim)

- `:Lazy` - Open Lazy interface
- `:Lazy sync` - Update all plugins
- `:Lazy clean` - Remove unused plugins

### LSP and Mason

- `:Mason` - Open Mason interface
- `:LspInfo` - Information about active LSP servers
- `:LspRestart` - Restart LSP server

### Diagnostics

- `:Trouble` - Open diagnostics list
- `:TroubleToggle` - Toggle Trouble window

## 📚 Resources

- [Neovim Documentation](https://neovim.io/doc/)
- [Neovim Configuration Guide](https://vincent.jousse.org/blog/fr/tech/configurer-neovim-comme-ide-a-partir-de-zero-tutoriel-guide/#tldr)
- [Awesome Neovim](https://github.com/rockerBOO/awesome-neovim) - Plugin list

## 🗑️ Uninstallation (Linux / macOS)

To completely remove Neovim and this configuration:

```bash
rm -rf ~/.config/nvim
rm -rf ~/.local/state/nvim
rm -rf ~/.local/share/nvim
rm -rf ~/.cache/nvim
```

## 📝 Notes

- This configuration uses **lazy.nvim** as plugin manager
- Plugins are installed automatically on first launch
- The configuration is compatible with Neovim 0.9.0+
- LSP servers are managed via **Mason** for simplified installation

## 🤝 Contributing

Feel free to open an issue or pull request to suggest improvements!

## 📄 License

This configuration is free to use and modify.
