# Direct AnkiWeb sync: implementation plan

## Current state

VitaAnki is a Vita2D C prototype. It can read a limited set of cards from an
`.apkg`, apply a simplified offline schedule, and optionally send live answers
to Anki Desktop through AnkiConnect. It does **not** sync with AnkiWeb.

The `.apkg` importer flattens notes into front/back text. That representation
does not retain Anki's note types, templates, collection changes, review log,
or media, so it cannot safely serve as the collection for AnkiWeb sync.

## Why direct sync needs a backend port

Anki's sync client is part of its Rust backend (`rslib`). Sync involves login,
collection upload/download and merge, media upload/download, and conflict
handling. Implementing only the HTTP requests would leave collection state
inconsistent and could overwrite reviews or deck changes. The protocol also
changes over time, so the implementation should track a specific upstream
Anki release and be reviewed when updating it.

Rust has a PS Vita target (`armv7-sony-vita-newlibeabihf`) and VitaSDK-based
cross-compilation. This makes a Rust/C bridge a plausible route to reuse Anki
code, but it does not guarantee that Anki's backend dependencies compile or
run on Vita. The target has partial `std` support and no dynamic linking, so
we need an early build spike before committing the app to that architecture.

## Proposed milestones

1. **Toolchain spike:** install VitaSDK and the Rust Vita target; build a tiny
   Rust static library for Vita and link it into the existing C/Vita2D app.
   Record the exact Rust and VitaSDK versions.
2. **Backend feasibility:** pin an Anki source release, identify the smallest
   upstream collection, scheduler, and sync components that can build for
   Vita, and resolve SQLite, TLS, compression, protobuf, and C-ABI needs.
   Do not send account credentials during this stage.
3. **Local collection:** replace the flattened card list with an Anki
   collection database and media directory. Import decks without discarding
   note types, templates, scheduling, or review history.
4. **Safe sync:** add AnkiWeb login, an explicit first-sync upload/download
   choice, transactional collection merge, media sync, backups before
   replacement, retryable offline changes, and clear conflict/error messages.
5. **Device validation:** build a VPK, install it on the homebrewed Vita, and
   validate login, first sync, repeated sync, offline review, and recovery from
   an interrupted sync against a backed-up test account.

## Keep the prototype safe to use

- Keep APKG offline review available while direct sync is being developed.
- Do not claim an answer was synced until AnkiWeb confirms it.
- Never store an Anki password in source control or an example config.
- Require TLS certificate validation for AnkiWeb requests.
- Keep a recoverable local collection backup before any full download or
  collection replacement.

## Immediate prerequisite

The development workspace now has a working VitaSDK, CMake, and Ninja setup
that produces the current VPK. The Rust Vita target and Anki backend build
spike in milestone 1 are still unverified. The next step for direct AnkiWeb
sync remains checking whether a pinned Anki backend release and its
dependencies can be cross-compiled and linked into this app.
