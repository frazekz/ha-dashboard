# AI-assisted workflow (example)

This public edition is maintained with help from an AI assistant. The assistant can draft YAML, templates and documentation. A human still decides what is applied to a live Home Assistant.

The steps below are the method we actually use on this project. They are not a claim that every other dashboard is built carelessly — only that we want the method written down next to the config.

## Principles

1. **Read first.** Study the running system in read-only mode before proposing a change.
2. **Backup first.** Take a copy of the files that will change, so a rollback is possible.
3. **Draft locally.** Write the change in a local draft, not directly on the live instance.
4. **One change at a time.** Keep each proposal small enough to review and to undo.
5. **Explicit human yes.** Nothing is written to a live Home Assistant until a person approves that specific change.
6. **Rollback.** Keep the previous copy and a short note of how to restore it.
7. **Log.** Record what changed, at a high level, in a changelog (no secrets, no personal data, no live entity ids).

## What the assistant may do on its own

- Read existing YAML, templates and documentation
- Draft a new or updated file in a local folder
- Point out risks (secrets, cameras, personal names, network details)
- Prepare a rollback note

## What the assistant must not do without a yes

- Modify a live Home Assistant
- Install or delete integrations
- Publish a repository, a post, or a comment
- Commit or push to a remote
- Read or copy `secrets.yaml`, `.storage`, backups, databases, camera snapshots or other credentials

## A typical change

```
read (live or local copy)
        ↓
backup of the files that will change
        ↓
local draft (one topic)
        ↓
human review
        ↓
approve or reject
        ↓
apply the approved change, or stop
        ↓
check, and roll back if needed
        ↓
short entry in the log
```

If a draft would require copying a real floor plan, a camera frame, a person's name, or a network address, stop and replace those with generic examples before anything is published.
