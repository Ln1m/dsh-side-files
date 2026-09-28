# dsh-files

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
