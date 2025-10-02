# Configuration Neovim 🚀

Une configuration Neovim moderne et complète, optimisée pour le développement avec LSP, autocomplétion, et une interface utilisateur élégante.

## ✨ Fonctionnalités

- 🎨 **Thème Tokyo Night** - Interface sombre et moderne
- 🔍 **Telescope** - Recherche floue puissante pour fichiers, buffers, et plus
- 🌳 **Nvim-tree** - Explorateur de fichiers avec icônes
- 📝 **LSP intégré** - Support complet du Language Server Protocol
- ⚡ **Autocomplétion intelligente** - nvim-cmp avec snippets
- 🎯 **Treesitter** - Mise en évidence syntaxique avancée
- 🤖 **GitHub Copilot** - Assistant de code IA
- 🔧 **Mason** - Gestionnaire de LSP, DAP, linters et formatters
- ✅ **Conform** - Formatage automatique du code
- 🐙 **Lazygit** - Intégration Git dans Neovim
- 📊 **Lualine** - Barre de statut élégante
- 🎭 **Which-key** - Guide des raccourcis clavier
- 🔔 **Noice** - Interface utilisateur améliorée pour les messages
- 🌈 **Rainbow delimiters** - Coloration des parenthèses
- 💬 **Chat** - Intégration de chat IA
- 📋 **Bufferline** - Gestion des buffers avec onglets
- 🚨 **Trouble** - Liste des diagnostics et quickfix
- 📑 **Markdown** - Support amélioré du Markdown

## 📋 Prérequis

Avant d'installer cette configuration, assurez-vous d'avoir :

- **Neovim >= 0.9.0** (recommandé : dernière version stable)
- **Git** - Pour cloner le dépôt
- **Node.js** - Requis pour certains LSP et GitHub Copilot
- **Python 3** - Pour certains plugins et LSP
- **Ripgrep** - Pour la recherche avec Telescope
- **Une Nerd Font** - Pour l'affichage correct des icônes

### Outils recommandés

- [Ripgrep](https://github.com/BurntSushi/ripgrep) - Outil de recherche ultra-rapide
- [Nerd Fonts](https://www.nerdfonts.com) - Polices avec icônes intégrées
- [WezTerm](https://wezterm.org) - Émulateur de terminal moderne
- [mise](https://mise.jdx.dev) - Gestionnaire de versions de runtimes (alternative à asdf, nvm, pyenv, etc.)

## 🚀 Installation

### Installation complète

Clonez le projet dans `~/.config/nvim` :

```bash
git clone https://github.com/stephen-shopopop/neovim ~/.config/nvim
```

Puis lancez Neovim. Les plugins seront automatiquement installés grâce à **lazy.nvim**.

### Installation des dépendances système

#### mise

```bashbash
curl -fsSL https://mise.jdx.dev/install.sh | bash
```

Ajoutez `mise` à votre shell:

```bash
// For Zsh
echo 'eval "$(~/.local/bin/mise activate zsh)"' >> ~/.zshrc

// For Bash
echo 'eval "$(~/.local/bin/mise activate bash)"' >> ~/.bashrc
```

Puis installez les runtimes nécessaires:

```bash
mise install
```

#### macOS

```bash
# Homebrew
brew install neovim ripgrep fd node python3

# Installer une Nerd Font
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

## 📦 Serveurs LSP inclus

Cette configuration installe automatiquement les serveurs LSP suivants via Mason :

- **actionlint** - GitHub Actions
- **biome** - JavaScript/TypeScript (alternative à ESLint/Prettier)
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

## ⌨️ Raccourcis clavier principaux

La touche **Leader** est définie sur **Espace**.

### Généraux

- `;;` - Sortir du mode insertion (au lieu de `<ESC>`)
- `<leader>nh` - Effacer le surlignage de la recherche
- `Shift+I` - Déplacer la ligne/sélection vers le haut (mode visuel)
- `Shift+K` - Déplacer la ligne/sélection vers le bas (mode visuel)

### Navigation et fichiers

- `<leader>ff` - Rechercher un fichier (Telescope)
- `<leader>fg` - Recherche globale dans les fichiers (Telescope)
- `<leader>fb` - Liste des buffers (Telescope)
- `<leader>e` - Toggle l'explorateur de fichiers (Nvim-tree)

### LSP et code

- `gd` - Aller à la définition
- `gr` - Afficher les références
- `K` - Afficher la documentation (hover)
- `<leader>ca` - Actions de code (code actions)
- `<leader>rn` - Renommer le symbole
- `[d` / `]d` - Diagnostic précédent/suivant

### Git

- `<leader>gg` - Ouvrir Lazygit
- `<leader>gd` - Afficher le diff Git

Pour voir tous les raccourcis disponibles, appuyez sur `<leader>` et attendez que **Which-key** affiche le guide.

## 🛠️ Personnalisation

### Structure du projet

```
~/.config/nvim/
├── init.lua                 # Point d'entrée principal
├── lua/
│   ├── core/               # Configuration de base
│   │   ├── init.lua        # Chargement des modules core
│   │   ├── options.lua     # Options Neovim
│   │   └── keymaps.lua     # Raccourcis clavier globaux
│   ├── config/
│   │   └── lazy.lua        # Configuration du gestionnaire de plugins
│   └── plugins/            # Configuration des plugins
│       ├── init.lua
│       ├── lsp/            # Configuration LSP
│       │   ├── mason.lua
│       │   └── lspconfig.lua
│       ├── telescope.lua
│       ├── nvim-tree.lua
│       ├── treesitter.lua
│       └── ...
└── lazy-lock.json          # Verrouillage des versions de plugins
```

### Ajouter un plugin

Créez un nouveau fichier dans `lua/plugins/` :

```lua
return {
  "auteur/nom-du-plugin",
  config = function()
    -- Configuration du plugin
  end,
}
```

### Ajouter un serveur LSP

Éditez `lua/plugins/lsp/mason.lua` et ajoutez le serveur dans `ensure_installed`.

## 🔧 Commandes utiles

### Gestion des plugins (Lazy.nvim)

- `:Lazy` - Ouvrir l'interface Lazy
- `:Lazy sync` - Mettre à jour tous les plugins
- `:Lazy clean` - Supprimer les plugins non utilisés

### LSP et Mason

- `:Mason` - Ouvrir l'interface Mason
- `:LspInfo` - Informations sur les serveurs LSP actifs
- `:LspRestart` - Redémarrer le serveur LSP

### Diagnostics

- `:Trouble` - Ouvrir la liste des diagnostics
- `:TroubleToggle` - Toggle la fenêtre Trouble

## 📚 Ressources

- [Documentation Neovim](https://neovim.io/doc/)
- [Guide de configuration Neovim](https://vincent.jousse.org/blog/fr/tech/configurer-neovim-comme-ide-a-partir-de-zero-tutoriel-guide/#tldr)
- [Awesome Neovim](https://github.com/rockerBOO/awesome-neovim) - Liste de plugins

## 🗑️ Désinstallation (Linux / macOS)

Pour supprimer complètement Neovim et cette configuration :

```bash
rm -rf ~/.config/nvim
rm -rf ~/.local/state/nvim
rm -rf ~/.local/share/nvim
rm -rf ~/.cache/nvim
```

## 📝 Notes

- Cette configuration utilise **lazy.nvim** comme gestionnaire de plugins
- Les plugins sont installés automatiquement au premier lancement
- La configuration est compatible avec Neovim 0.9.0+
- Les LSP sont gérés via **Mason** pour une installation simplifiée

## 🤝 Contribution

N'hésitez pas à ouvrir une issue ou une pull request pour proposer des améliorations !

## 📄 Licence

Cette configuration est libre d'utilisation et de modification.
