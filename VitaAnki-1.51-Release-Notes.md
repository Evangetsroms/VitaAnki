# VitaAnki 1.51 — public preview

This release updates the Vita source and VPK to 1.51 and includes Android companion source 0.4.1.

## Vita updates

- Add persistent deck folders, folder filtering, and per-deck folder assignment.
- Add a folder-wide All Due Reviews queue while keeping each deck's own progress and scheduling.
- Show review and learning counts in the deck picker; expose Study More in batches after the learning queue is clear.
- Persist each deck's daily new-card limit and its Again, Hard, Good, and Easy scheduling settings.
- Refine themes and folder views, improve deck create and rename workflows, and fix folder-browser deletion.
- Keep local study state recoverable across file replacement operations.

## Android

The combined source archive includes Android 0.4.1 source and a generic sample deck. It does not include an installable APK because a current APK could not be verified.

## Public package contents

The VPK and source archive use a generic five-card sample deck. Personal decks, soundtrack files, sync credentials, and backups are excluded. Background music and click sounds are disabled in the VPK. AnkiWeb login and direct AnkiWeb synchronization are not implemented; desktop live review uses AnkiConnect.
