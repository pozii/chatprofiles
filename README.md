# ChatProfiles

A Paper/Purpur plugin that keeps a searchable history of what every player says in chat. Built for one reason: when someone gets reported, staff can actually check what was said instead of guessing.

## Commands

Operator-only, console works too.

- `/chatprofile <player> [page]` — scroll through a player's past messages, 10 per page
- `/chatprofile export <player>` — save the full history to a `.txt` file under `plugins/ChatProfiles/exports/`
- `/chatprofile clear <player>` — wipe a player's history; asks you to run it twice so it never happens by accident

## Install

1. Grab the jar from [Modrinth](https://modrinth.com/mod/chatprofiles)
2. Drop it in `plugins/`
3. Restart the server

Needs Java 21. No database to set up — it uses a local SQLite file (`plugins/ChatProfiles/messages.db`).

## Performance

Chat events never hit the disk directly. Messages go into a memory queue and get written to SQLite in batches every few seconds by a single background thread. Viewing and exporting are paged and async, so nothing blocks the game thread. Default retention is 1000 messages or 60 days per player, cleaned up daily — all adjustable in `config.yml`.

```bash
mvn package
```

## Config

Everything lives in `config.yml`: retention limits, purge interval, batch size and timing, cache size, page size. Defaults are sane for most servers — you can run it untouched.
