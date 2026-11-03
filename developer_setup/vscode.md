# 1. VS Code

VS Code is our standard editor because everyone gets the same extensions, formatting, and debugging setup. You are welcome to use another IDE if you are faster in it.

## Install

### macOS

```bash
brew install --cask visual-studio-code
```

No Homebrew? Download the macOS zip from <https://code.visualstudio.com/download>, unzip it, and drag **Visual Studio Code** into Applications.

### Windows

```powershell
winget install --id Microsoft.VisualStudio.Code -e
```

Or download the Windows installer from <https://code.visualstudio.com/download>.

## Open the repo

```bash
code /path/to/hackathon-1
```

On macOS, if `code` is not found: open VS Code, press `Cmd+Shift+P`, run **Shell Command: Install 'code' command in PATH**, then reopen the terminal.

## Install these extensions

Open the Extensions panel (`Cmd/Ctrl+Shift+X`) and install:

| Extension | Why |
| --- | --- |
| **ESLint** | Catches JavaScript/TypeScript mistakes |
| **Prettier** | Formats your code on save |
| **Python** | Python support, debugging, environments |
| **Ruff** | Fast Python linting and formatting |
| **Docker** | Manage containers, if you use them |
| **GitLens** | See who changed what, inline |

Or from the terminal:

```bash
code --install-extension dbaeumer.vscode-eslint \
  --install-extension esbenp.prettier-vscode \
  --install-extension ms-python.python \
  --install-extension charliermarsh.ruff \
  --install-extension ms-azuretools.vscode-docker \
  --install-extension eamodio.gitlens
```

## Turn on format on save

Open Settings (`Cmd/Ctrl+,`), search **Format On Save**, and enable it. Pick Prettier as the default formatter for JS/TS and Ruff for Python. This avoids style arguments later.

## Useful shortcuts

| Action | macOS | Windows/Linux |
| --- | --- | --- |
| Command palette | `Cmd+Shift+P` | `Ctrl+Shift+P` |
| Find in files | `Cmd+Shift+F` | `Ctrl+Shift+F` |
| Go to file | `Cmd+P` | `Ctrl+P` |
| Toggle terminal | ``Ctrl+` `` | ``Ctrl+` `` |
| Format document | `Shift+Alt+F` | `Shift+Alt+F` |

## Using another editor

That is fine. Install the equivalents of ESLint/Prettier (or Ruff for Python), make sure format-on-save works, and confirm you can run the project's `npm run dev` or `uv run ...` command from a terminal.
