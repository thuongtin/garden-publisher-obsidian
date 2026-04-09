# Garden Publisher

Obsidian plugin to publish notes marked with `publish: true` to a shared Notes Garden.

This repository is the BRAT/manual-install release package for the plugin. The source code lives in the main Notes Garden monorepo and is exported here as a plugin-only build.

## Install with BRAT

1. Install the BRAT plugin in Obsidian.
2. Open `BRAT: Add a beta plugin for testing`.
3. Paste this repository URL:

```text
https://github.com/thuongtin/garden-publisher-obsidian
```

4. Confirm the install.
5. Enable `Garden Publisher` in Community Plugins if Obsidian does not enable it automatically.

## Manual install

Download these files from the latest GitHub release:

- `manifest.json`
- `main.js`
- `styles.css`

Copy them into:

```text
<your-vault>/.obsidian/plugins/garden-publisher/
```

Then enable `Garden Publisher` in Obsidian Community Plugins.

## Plugin settings

Fill in:

- `Server URL`
- `Publisher token`
- `Display author`
- `Author slug`

Optional:

- `Publish scope folder`
- `Auto sync on startup`
- `Sync on save`
- `Include attachments`
- `Max asset size (MB)`

## How to get a publisher token

Send a DM to the Notes Garden Telegram bot:

```text
https://t.me/Notes_Garden_Bot
```

Typical flow:

1. Send `/start`
2. Send `/register`
3. Choose your username/slug
4. Wait for admin approval
5. Send `/token` after approval

Each username is bound to one Telegram account.

## Frontmatter

Minimum:

```yaml
---
publish: true
---
```

Optional:

```yaml
---
publish: true
slug: custom-note-slug
excerpt: Short summary for cards
tags:
  - ai
  - research
garden_id: auto-generated-by-plugin
---
```

## Commands

- `Garden: Sync published notes`
- `Garden: Publish current note`
- `Garden: Unpublish current note`
- `Garden: Show publish status`
- `Garden: Open public URL`

## Status bar

The plugin adds a Notes Garden status item to the Obsidian status bar for the active note.

Possible states:

- `Private note`
- `Still public`
- `Never synced`
- `Syncing`
- `Queued on server`
- `Processing on server`
- `Processing longer than usual`
- `Synced … ago`
- `Failed … ago`
- `Unpublish queued`
- `Removing from garden`
- `Unpublished`
- `Hidden`

Click the status item to open the quick action menu:

- `Refresh status`
- `Sync this note`
- `Sync all published notes`
- `Open public note`
- `Copy public URL`
- `Copy garden_id`
- `Unpublish this note`

## Route format

Published URLs use this format:

```text
https://notes-garden.ecom.io.vn/<author-slug>/<note-slug>
```

## Notes

- `garden_id` is the stable identity of a note. Do not remove it after the first publish.
- If a sync fails, the previous live version can remain public until the next successful publish or explicit unpublish.
- Large notes with many attachments, Mermaid blocks, or heavy link resolution can stay in `Processing on server` longer than usual.

