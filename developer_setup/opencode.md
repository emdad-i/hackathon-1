# 4. OpenCode + DeepSeek

[OpenCode](https://opencode.ai) is the AI coding agent we use for the hackathon. We use the **OpenCode CLI** in the terminal: it reads your repo, writes code, and runs commands.

We use **DeepSeek V4.1 Flash (free)**. If the free tier is rate-limited, backup credits for the same model are available on **Hugging Face** (setup below).

## Install

### macOS

```bash
curl -fsSL https://opencode.ai/v2/install | bash
```

Or with Homebrew:

```bash
brew install anomalyco/tap/opencode-v2
```

### Windows

Windows package managers are not supported, so install the standalone CLI binary:

1. Download the zip for your machine:
   - x64: <https://opencode.ai/update/api/latest/cli/opencode/opencode-windows-x64.zip>
   - ARM64: <https://opencode.ai/update/api/latest/cli/opencode/opencode-windows-arm64.zip>
2. Extract it to `%LOCALAPPDATA%\opencode`, so that `opencode.exe` sits directly in that folder.
3. Add `%LOCALAPPDATA%\opencode` to your `PATH` (Settings → System → About → Advanced system settings → Environment Variables → Path).
4. Open a **new** PowerShell window and check:

```powershell
opencode --version
```

If Windows blocks the download, right-click the zip → **Properties** → **Unblock** before extracting.

> Using WSL? Skip this and run the macOS/Linux install command inside your WSL terminal instead.

### Verify

```bash
opencode --version
```

## Use the free DeepSeek model

The repo ships [`opencode.jsonc`](../opencode.jsonc), which sets `model` to `opencode/deepseek-v4.1-flash-free`. OpenCode selects the free model automatically when it starts.

**No OpenCode account or API key is needed for the free model.** You do not need to run `/connect` or `/models`.

1. Open a terminal in the repo and start OpenCode:

   ```bash
   cd /path/to/hackathon-1
   opencode
   ```

2. Ask it something small to confirm it works:

   ```text
   Explain what this repository does in two sentences.
   ```

The free model is the default, so leave it selected for normal work. It is a limited-time offer and may be rate-limited during the event.

## Backup: Hugging Face credits

If the free model is unavailable or you hit a rate limit, switch to the same model through Hugging Face. **You do not need to create a Hugging Face account** — organisers will provide the token if it is needed. Ask in the Discord `#help` channel.

The Hugging Face provider is already defined in [`opencode.jsonc`](../opencode.jsonc), so there is no file to edit.

1. Export the token in your shell (do not commit it):

   ```bash
   export HF_TOKEN=hf_your_token_here
   opencode service restart
   ```

2. Use the backup for one run:

   ```bash
   opencode run --model huggingface/deepseek-v4.1-flash "hello"
   ```

   Or start `opencode`, run `/models`, and pick **DeepSeek V4.1 Flash (HF)**.

## Context and compaction

Both the free model and the Hugging Face backup are configured with a **200k context window** and a **200k output cap** in [`opencode.jsonc`](../opencode.jsonc).

OpenCode compacts automatically when a session gets close to the limit:

| Setting | Default | What it means |
| --- | ---: | --- |
| Context | 200,000 | Total tokens the model can see |
| Buffer | 15% (30,000) | Room kept free for the next request |
| Compaction starts | ~170,000 | When the conversation reaches this, older messages are summarised |
| `keep.tokens` | 15,000 | Recent conversation kept verbatim beside the summary |

So compaction triggers at **200k − 15% ≈ 170k tokens**, not at 200k. The 15k `keep.tokens` value is separate: it controls how much recent detail survives the summary.

If you need more recent detail preserved, change `compaction.keep.tokens` in `opencode.jsonc`:

```jsonc
"compaction": {
  "keep": { "tokens": 30000 }
}
```

A larger `keep.tokens` leaves less room for new work, so it may cause more frequent compaction.

## Rules for using OpenCode

- **Never paste secrets** (API keys, tokens, `.env` contents) into a prompt.
- **Read the diff** before accepting a change. You have to debug it later.
- **Check package names** it suggests — only install ones you recognise.
- **Commit often** so you can undo bad AI edits with Git.
- **You own the demo.** Do not ship code you cannot explain.

## Useful commands

| Command | What it does |
| --- | --- |
| `opencode` | Start in the current folder |
| `/models` | Switch models |
| `/connect` | Add a provider or account |
| `/help` | See all commands |
| `opencode run "..."` | One-shot task without the TUI |

## Troubleshooting

| Problem | Fix |
| --- | --- |
| `opencode: command not found` | Open a new terminal; confirm the install directory is on `PATH` |
| No models listed | Open OpenCode from inside the repo, then run `/models` |
| Free model unavailable | Wait a minute, or switch to the Hugging Face backup |
| `401` from Hugging Face | Token is wrong, expired, or not exported in this shell |
| Windows blocks the download | Right-click the zip → **Properties** → **Unblock**, then extract again |
| Config not applied | Confirm `opencode.jsonc` is in the repo root and is valid JSON |
