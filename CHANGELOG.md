# Changelog

Read inside the app too — **About** in the title bar renders this file, so there
is one list rather than two that drift apart.

## Release — 0.1.0
First release
### Added

- **Save reading** — AES-128-ECB decryption, header parsing, account and slot discovery, and the full roster (party, box and farm) with the stride base discovered rather than assumed.
- **Save writing** — every pending edit applied to the decrypted buffer, re-encrypted and written back atomically. The batch is validated before a byte is touched, so a rejected edit is a no-op rather than a half-written save.
- **Automatic backups** — a write always copies the slot first and aborts if that copy fails. How many to keep is a setting (1–100, default 20), read by the backend rather than the caller.
- **Restore** — put any of a slot's backups back. The file is decrypted and parsed *before* anything is overwritten, and the current state is copied out first, so a restore is itself undoable.
- **Confirmation everywhere it matters** — saving, closing over unsaved work, restoring a backup and switching slots all ask first, and itemise what is about to happen.
- **Roster editor** — identity, levels and EXP, HP/SP, bond, talent, personality and its passive skill, food, evolution counters, three editable stat blocks, attachment skills and equipment, plus an Evolution panel that checks each candidate's requirements against this Digimon.
- **Agent editor** — name, money, Anomaly Points and rank, above the five skill trees with prerequisite enforcement and per-tree unlock/refund.
- **Inventory editor** — the full item catalog by category, with quantity steppers and a per-category fill.
- **Scan editor** — the scan-percentage table as a sortable, filterable portrait grid with batch set.
- **Field Guide editor** — the encyclopedia as a portrait grid; cycle a species through unseen, seen and owned, with batch register and clear.
- **Digimon List (Digidex)** — a standalone species browser that works with or without a save, including an interactive evolution graph with per-edge requirements.
- **Extra tab** — roster-wide bulk actions with a scope selector: set level (with the EXP that matches it), bond, talent, evolution counters, and add to or set whole stat blocks. Each button says how many records it would touch before you press it.
- **Overview tab** — a read-only summary of the open save: tamer, roster split, the party trio, and progress bars for agent skills, inventory, scans and the field guide. Figures include unsaved changes, with a dot marking what differs from the file on disk.
- **Changes pane** — every pending edit, grouped by editor and written out in words, each revertable on its own.
- **Undo and redo**, with bulk actions undoing as a single step.
- **Save feedback** — every write and restore reports what landed, or says plainly that nothing was written.


## About the version number

`0.1.0` is the version in `tauri.conf.json`, which is what the installed
binary reports. The About dialog asks the binary for it rather than trusting a
number compiled into the interface.
