# dsh-files

> Only the **vk build** ships in this repo: the sidebar "Files" tab and the right-column "Open local file" tab are positions provided by the [dsh-vk-suite](https://github.com/Ln1m/dsh-vk-suite) skeleton (contract + layout), which must be installed first.
> **The vk build is the recommended one** in the two-build model: the sidebar tab switcher (Sessions / Files / Tasks / Extensions) plus the right-column and settings positions live in the skeleton, so only the vk build lands in them.

The files family for the DSH Web left sidebar: two packages, one repo.

| Package | Role |
|---|---|
| `dsh-files-tree` | The "Files" tab in the left sidebar: file tree + in-app directory browser + recent/file list; the composer's `@` references live here too |
| `dsh-files-open` | The "Open local file" tab in the right column (installable on its own) |

Both need the framework (`dsh-vk-contract` + `dsh-vk-layout`); without the skeleton the slots they register are never declared and nothing new appears.

## Install

```powershell
dsh plugin --profile web add file:<path-to-dsh-vk-suite>/dsh-vk-contract
dsh plugin --profile web add file:<path-to-dsh-vk-suite>/dsh-vk-layout
dsh plugin --profile web add file:<this repo>/dsh-files-tree
dsh plugin --profile web add file:<this repo>/dsh-files-open
```

Restart DSH afterwards. The left sidebar gains a "Files" tab and the right column an "Open local file" tab.

## Recommended pairing / possible conflicts

- **Install it together with the skeleton**: the sidebar **tab switcher** (Sessions / Files / Tasks / Extensions) in [dsh-vk-suite](https://github.com/Ln1m/dsh-vk-suite) (`dsh-vk-contract` + `dsh-vk-layout`) is what hosts the file tree — this package alone gives you no sidebar "Files" entry.
- The right-column "Open local file" tab body is registered by the skeleton too: without it the tab keeps its title but shows only the official fallback text.
- **Possible conflicts**: this package deliberately **replaces the official `files` tab type** (so the "new tab" list has no duplicate entry) and claims `conversation.input.left` for the composer's `@` references. A plugin registering the same `files` type, or registering into `conversation.input.left` at the same priority, is mutually exclusive with it: the first registration wins, the second throws and is swallowed, so one of the two never appears.
- Stacked with another "three-column layout" plugin, the sidebar shape follows the highest-priority one.

## Configuration

| Item | Where | Default |
|---|---|---|
| Landing-page roots | `HOME_DIRS` in `dsh-files-tree/lib/client.js` | `[]` — add the directories you want pinned |
| Desktop shortcut entry | `DESKTOP_HINT` in the same file | empty; set your own desktop path to show it |

## Environment

| Variable | Default | Notes |
|---|---|---|
| `DSH_ROOT` | `~/DeepSeek_harness` | DSH install root; the "agent-side directories" derive from it |

## License

MIT
