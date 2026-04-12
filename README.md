# CVIMU

- [CVIMU](#cvimu)
  - [DEPENDENCIES](#dependencies)
  - [HOW](#how)
    - [for Linux](#for-linux)
    - [for MacOS (untested)](#for-macos-untested)
    - [for Windows (untested)](#for-windows-untested)
  - [WORKSPACES](#workspaces)
  - [Github Copilot Chat bug when importing from profile](#github-copilot-chat-bug-when-importing-from-profile)
  - [KEYBINDINGS](#keybindings)
    - [fixes to vscode](#fixes-to-vscode)
    - [navigation](#navigation)
    - [AI](#ai)
    - [GOTOs](#gotos)
    - [hover over code](#hover-over-code)
    - [warnings and diagnostics](#warnings-and-diagnostics)
    - [buffers aka editors](#buffers-aka-editors)
    - [file explorer](#file-explorer)
    - [integrated terminal](#integrated-terminal)
    - [search](#search)
    - [find](#find)
    - [fold](#fold)
    - [code actions](#code-actions)
  - [DONATE](#donate)

CODE-VIM-ULTIMATE aka CVIMU is a Visual Studio Code DISTRO with:

- Vim Extension.
- [LazyVim](https://www.lazyvim.org/keymaps)-like global keybindings.
- Copilot Chat Extension for AI agentic workflow and inline suggestions (you remove extension and it's configs in non-global `settings.json` and `keybindings.json` if you want to use claude code instead)
- Compatible with [Obsidian](https://obsidian.md/), same keybindings like `ctrl o` and `ctrl p` for opening recent files and command palette instead of LazyVim's ones as well as few others.

plus sensible defaults and [fixes to vscode](#fixes-to-vscode) for maximum productivity and comfort.

```bash
├── profiles
│   └── prof.code-profile
├── settings.json
└── Workspaces
    └── PLACE YOUR WORKSPACES HERE
```

Extensions in [profile](./profiles/prof.code-profile):

- ESLint
- Prettier - Code formatter
- GitHub Copilot Chat
- Bash IDE
- Container Tools
- Postman
- Paste JSON as Code
- Code Spell Checker
- vscode-icons
- Vim
- YAML
- markdownlint
- Markdown All in One
- Catppuccin for VSCode
- ES7+ React/Redux/React-Native snippets
- Tailwind CSS IntelliSense

## DEPENDENCIES

`markdownlint`  
required for `markdownlint` extension.
install it or uninstall `markdownlint` extension.

`shfmt` and `shellcheck`  
required for `Bash IDE` extension.
install those or uninstall `Bash IDE` extension.

## HOW

**NOTE:**
Due to how vscode works, you must first open vscode at least once for creation of `Code/User` directory.

1. Clone `CVIMU` directory in your dotfiles.
1. Remove `.git`.
1. Import `prof` profile from [profiles/prof.code-profile](profiles/prof.code-profile).
1. Symlink global settings.json file for keybindings.  
   In my case, on linux, I save dotfiles at `~/.dotfiles`, which is managed with `git` and `stow`.

### for Linux

do everything in [HOW](#how)  
and then

```bash
ln -sf "$HOME/.dotfiles/CVIMU/settings.json" "$HOME/.config/Code/User/settings.json"
```

### for MacOS (untested)

do everything in [HOW](#how)  
and then

```bash
ln -sf "$HOME/.dotfiles/CVIMU/settings.json" "$HOME/Library/Application Support/Code/User/settings.json"
```

### for Windows (untested)

do everything in [HOW](#how)  
and then

```powershell
New-Item -ItemType SymbolicLink `
  -Path "$env:APPDATA\Code\User\settings.json" `
  -Target "$HOME\.dotfiles\CVIMU\settings.json"
```

## WORKSPACES

- Export your workspaces to [workspaces](./workspaces/) via `File > Save Workspace As...`
- go to containing directory of them all
- select them all with `ctrl` + `a`
- drop them all in opened vscode instance

## Github Copilot Chat bug when importing from profile

There is [issue](https://github.com/microsoft/vscode/issues/268852)  
when importing any profile that has `Github Copilot Chat` extension,
workaround is that I have `Github Copilot Chat` removed from [prof.code-profile](./profiles/prof.code-profile)  
and when you finish installing this setup, you must manually search `Github Copilot Chat` in extensions
search and press install there. So basically it comes with `Github Copilot Chat` extension's configurations
configured, but extension itself is not installed, because it crashes vscode upon importing.  
Issue is open at `microsoft/vscode` and getting fixed slowly.

## KEYBINDINGS

### fixes to vscode

`<leader>` is set to `space`.

| Keybinding   | Feature                          |
| ------------ | -------------------------------- |
| `<C-d>`      | Scroll down half page and center |
| `<C-u>`      | Scroll up half page and center   |
| `ctrl n`     | Down (when given a dropdown)     |
| `ctrl p`     | Up (when given a dropdown)       |
| `<leader> e` | Open file explorer (with focus)  |
| `ctrl b`     | Close / open explorer (no focus) |

### navigation

| Keybinding            | Feature                                                                                         |
| --------------------- | ----------------------------------------------------------------------------------------------- |
| `s`                   | Search word (EasyMotion)                                                                        |
| `<leader> <leader> b` | Jump to word (before cursor)(EasyMotion)                                                        |
| `<leader> <leader> w` | Jump to word (after cursor)(EasyMotion)                                                         |
| `ctrl alt r`          | (when file explorer is focused) open containing folder of focused file / dir (same in Obsidian) |

### AI

| Keybinding   | Feature                  |
| ------------ | ------------------------ |
| `ctrl i`     | Copilot inline chat `AI` |
| `ctrl alt i` | Copilot chat `AI`        |

### GOTOs

| Keybinding     | Feature               |
| -------------- | --------------------- |
| `g d`          | Go to definition      |
| `g D`          | Go to declaration     |
| `g i`          | Go to implementation  |
| `g r`          | Go to references      |
| `g h`          | Go to call hierarchy  |
| `g y`          | Go to type definition |
| `<leader> g g` | Focus source control  |

### hover over code

| Keybinding | Feature              |
| ---------- | -------------------- |
| `K`        | Show hover info      |
| `g K`      | Show parameter hints |

### warnings and diagnostics

| Keybinding | Feature             |
| ---------- | ------------------- |
| `] d`      | Next diagnostic     |
| `[ d`      | Previous diagnostic |
| `] e`      | Next error          |
| `[ e`      | Previous error      |
| `] w`      | Next warning        |
| `[ w`      | Previous warning    |

### buffers aka editors

| Keybinding     | Feature                                          |
| -------------- | ------------------------------------------------ |
| `[ b`          | Previous editor tab                              |
| `] b`          | Next editor tab                                  |
| `[ B`          | Move editor left                                 |
| `] B`          | Move editor right                                |
| `alt {NUMBER}` | go to editor {NUMBER} (same in Obsidian)         |
| `ctrl shift t` | Reopen recently closed editor (same in Obsidian) |
| `ctrl w`       | Close current editor (same in Obsidian)          |
| `<leader> b d` | Close current editor                             |
| `<leader> b r` | Close editors to the right                       |
| `<leader> b l` | Close editors to the left                        |
| `<leader> b o` | Close all other editors                          |
| `<leader> e`   | Focus file explorer                              |

### file explorer

| Keybinding | Feature                                  |
| ---------- | ---------------------------------------- |
| `a`        | Create a new file                        |
| `f`        | Create a new directory                   |
| `d`        | Delete selected file/directory           |
| `y`        | Copy selected file/directory             |
| `p`        | Paste into selected directory            |
| `x`        | Cut selected file/directory              |
| `r`        | Rename selected file/directory           |
| `o`        | Reveal file/directory in OS file manager |

### integrated terminal

| Keybinding     | Feature                           |
| -------------- | --------------------------------- |
| `alt {NUMBER}` | go to terminal {NUMBER}           |
| `ctrl t`       | create new terminal               |
| `ctrl w`       | delete active terminal            |
| `ctrl i`       | Copilot inline terminal chat `AI` |

### search

| Keybinding     | Feature                                 |
| -------------- | --------------------------------------- |
| `ctrl p`       | Open command palette (same in Obsidian) |
| `<leader> s d` | Toggle problems panel                   |
| `<leader> s r` | Search and replace                      |
| `<leader> s s` | Go to symbol in current file            |
| `<leader> s S` | Go to symbol in a whole workspace       |
| `<leader> /`   | Quick text search in a whole repository |

### find

| Keybinding     | Feature                            |
| -------------- | ---------------------------------- |
| `<leader> f p` | Open recent projects (Workspaces)  |
| `ctrl o`       | Quick open file (same in Obsidian) |

### fold

| Keybinding | Feature        |
| ---------- | -------------- |
| `za`       | toggle fold    |
| `zc`       | fold           |
| `zo`       | open fold      |
| `zR`       | open all folds |

### code actions

| Keybinding     | Feature               |
| -------------- | --------------------- |
| `<leader> c a` | Quick fix             |
| `<leader> c A` | Source action         |
| `<leader> c r` | Rename symbol         |
| `<leader> c p` | Preview markdown      |
| `<leader> c u` | Remove unused imports |

**Disclaimer**  
This project is purely a community-driven configuration setup and is not officially affiliated with or endorsed by Visual Studio Code (Microsoft), LazyVim, or any other commercial software vendor.
Use this configuration at your own risk. I make no guarantees regarding compatibility, stability, or fitness for any particular purpose.

## DONATE

I've been creating FOSS / GNU/Linux / nvim / web
related software for some time now.  
If you used, forked or took code from one of my projects and you
would like to support me 👍,  
you can donate here:

| type                | address                                    |
| ------------------- | ------------------------------------------ |
| Bitcoin (SegWit)    | bc1ql8sp9shx4svzlwv0ckzv8s7pphw5upvmt8m2m7 |
| Ethereum (Ethereum) | 0xf2FCB0Af39DF7A608b76297e45181aF23fEB939F |
