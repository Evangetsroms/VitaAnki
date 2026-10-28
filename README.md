<div align="center">
  <img src="VitaAnki-icon.png" alt="VitaAnki icon" width="116" />
  <h1>VitaAnki</h1>
  <p>Flashcard study for PS Vita, with Android companion source.</p>
  <p><a href="https://github.com/Evangetsroms/VitaAnki/releases/tag/v1.36-preview">Get the Vita 1.36 preview</a> · <a href="VitaAnki-1.36-Public-Source.zip">Download current source</a></p>
</div>

VitaAnki is an independent flashcard app for PS Vita. It supports offline study, compatible Anki deck imports, and optional local-network connections to Anki Desktop.

**Current public preview:** [VitaAnki 1.36 for PS Vita](https://github.com/Evangetsroms/VitaAnki/releases/tag/v1.36-preview). Android 0.4.0 source is included; a verified Android APK is not available in this release.

VitaAnki is not affiliated with Anki.

## Downloads

- **PS Vita:** install the .vpk from the [1.36 preview release](https://github.com/Evangetsroms/VitaAnki/releases/tag/v1.36-preview) with VitaShell.
- **Android:** the 0.4.0 companion source is included in the source archive. No installable APK is published yet.
- **Source:** [download the combined Vita and Android source archive](VitaAnki-1.36-Public-Source.zip), also attached to the release.

The public VPK and source archive include a short generic sample deck. Personal decks, music, sync credentials, and user backups are excluded.

## PS Vita

VitaAnki 1.36 supports offline spaced review, card browsing, deck creation and management, compatible image cards, deck transfer with Android over local Wi-Fi, and optional live review against Anki Desktop through AnkiConnect. It starts offline; choose **Sync with PC** to connect. See the vita/README.md inside the source archive for build and usage notes.

## Android companion

Android 0.4.0 source includes offline study, compatible deck import, supported image cards, AnkiConnect review, and local Wi-Fi deck transfer with the Vita. See the android/README.md inside the source archive for build and usage notes. This release does not include a verified APK.

## Anki Desktop connection

Live PC review uses the AnkiConnect add-on while Anki Desktop is running. It is not an AnkiWeb login or direct AnkiWeb sync. Keep AnkiConnect on a trusted private network and use a strong API key. Keep sync.ini and its key private.

Offline review progress stays on the device and does not automatically merge into Anki Desktop. APKG support is limited; complex templates and audio may not render. The Vita app remains an alpha preview and may have stability problems with some decks or Vita setups. Keep backups of decks and study progress.

## Source layout

The source archive contains the vita/ and android/ source trees, their README files, and a generic sample deck.

- No license has been selected yet, so reuse and redistribution terms remain undecided.
