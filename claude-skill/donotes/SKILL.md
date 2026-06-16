---
name: donotes
description: Open or edit Markdown in offline-notes — a private, offline, single-file Markdown editor. Use when the user wants to view or edit Markdown (notes, a draft, a generated doc) in a real editor instead of the terminal, or says "open this in offline-notes" / "put these notes somewhere I can edit". Works fully offline.
---

# donotes — open Markdown in offline-notes

[offline-notes](https://github.com/nocodework/offline-notes) is a single-file, offline Markdown editor. This skill opens Markdown in it, preloaded, so the user can read and edit it visually instead of in the terminal.

The note is loaded into the browser's local storage. The file on disk is **not** modified by editing in the browser — if the user wants to save changes back, tell them to use **Export → .md** in the app.

## How to open Markdown in offline-notes

1. Get the Markdown text. If the user pointed at a file, use it. If you just generated the content, write it to a temp file first (e.g. `/tmp/donote.md`).
2. Base64-encode the UTF-8 bytes and open the editor with the content in the URL hash (`#md64=`):

```bash
# macOS
B64=$(base64 < /tmp/donote.md | tr -d '\n')
open "https://nocodework.github.io/offline-notes/#md64=$B64"
```

```bash
# Linux
B64=$(base64 -w0 < /tmp/donote.md)
xdg-open "https://nocodework.github.io/offline-notes/#md64=$B64"
```

```powershell
# Windows (PowerShell)
$B64 = [Convert]::ToBase64String([IO.File]::ReadAllBytes("note.md"))
Start-Process "https://nocodework.github.io/offline-notes/#md64=$B64"
```

The editor decodes `#md64=` as UTF-8 and creates a new note from it. There is also `#md=<uri-encoded>` if you prefer not to base64.

## Fully offline (no internet)

Download the editor once, then open the local file instead of the hosted URL:

```bash
curl -O https://raw.githubusercontent.com/nocodework/offline-notes/main/index.html
B64=$(base64 < /tmp/donote.md | tr -d '\n')
open "file://$(pwd)/index.html#md64=$B64"   # macOS; use xdg-open / start elsewhere
```

## Caveats

- Editing in the browser doesn't touch the file on disk. Export from the app to save.
- Very large documents can exceed the OS command-line length limit for the URL. For big files, open the editor and drag the `.md` file onto the window (or use Import) instead.
