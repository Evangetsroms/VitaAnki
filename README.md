<div align="center">
  <img src="VitaAnki-icon.png" alt="VitaAnki icon" width="128" />
  <h1>VitaAnki</h1>
  <p><strong>Flashcards for PlayStation Vita.</strong><br />Bring compatible Anki decks, study offline, and optionally review with Anki Desktop.</p>
  <p>
    <a href="https://github.com/Evangetsroms/VitaAnki/releases/latest"><strong>Download the Vita preview</strong></a>
    ·
    <a href="https://github.com/Evangetsroms/VitaAnki/blob/main/VitaAnki-1.26-Public-Source.zip">Get the source bundle</a>
  </p>
  <sub>Independent community project · Alpha preview · Not affiliated with Anki</sub>
</div>

---

## What it does

- Study tab-separated decks and compatible `.apkg` decks offline.
- Review cards with spaced repetition and save progress on the Vita.
- Browse cards and display supported card images.
- Optionally connect to Anki Desktop through AnkiConnect on your local network.
- Android companion app in development, with local Wi-Fi deck transfer to the Vita planned.

Direct AnkiWeb sync is not implemented. Live PC review requires Anki Desktop and AnkiConnect.

## Try the Vita preview

1. Download the `.vpk` from [Releases](https://github.com/Evangetsroms/VitaAnki/releases/latest).
2. Install it with VitaShell.
3. Copy a `.tsv` or compatible `.apkg` deck into `ux0:data/VitaAnki/decks/`.
4. Open **Import a deck**, choose **Rescan**, then select the deck.

The preview includes a small generic sample deck. It contains no personal decks, credentials, or background music.

> **Alpha notice:** APKG import still produces SQLite error 7 on some Vita setups. The latest diagnostics have not yet been confirmed to fix it on hardware. Keep a separate backup of your decks and study progress.

## Android companion APK

The Android companion app is in development for phones and tablets, with deck study and transfer to VitaAnki over local Wi-Fi planned.

**APK download:** No Android APK is published yet. A tested Android build will be posted on the [Releases](https://github.com/Evangetsroms/VitaAnki/releases) page when it is ready.

## Connect to Anki Desktop

Live PC review is optional. It requires Anki Desktop and the AnkiConnect add-on running on the same private Wi-Fi network. Copy `sync.example.ini` to `ux0:data/VitaAnki/sync.ini`, then enter your PC's local address, exact deck name, and your AnkiConnect key.

Keep `sync.ini` private. Never upload it or post its API key in an issue.

## Build from source

Install VitaSDK, CMake, and the VitaSDK libraries used by this project (`libvita2d`, `libzip`, `curl`, and `jansson`). From the project directory:

```sh
cmake -S . -B build -DCMAKE_TOOLCHAIN_FILE="$VITASDK/share/vita.toolchain.cmake" -DVITA_BUNDLE_PICTURE_DECK=OFF -DVITAANKI_ENABLE_MUSIC=OFF
cmake --build build
```

The build creates `vitaanki.vpk`. Background music is disabled by default; no music file is included. The optional player expects your own `audio/aquatic_ambience.mp3` file.

## Limitations

- The APKG importer supports a limited set of Anki note and card types. Complex templates and audio are not rendered.
- Image cards show the first supported image on the question side; the answer side is text-only.
- Offline review progress is stored locally and does not automatically merge into Anki Desktop.
- Live sync is to Anki Desktop, not AnkiWeb.
- This alpha has not been confirmed stable on all Vita models and decks.

## Report a bug

Include the VitaAnki version, Vita system software version, the action you took, and the full error text. Do not attach `sync.ini`, personal decks, or private media.
