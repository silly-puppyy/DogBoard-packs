# DogBoard language packs

Dictionaries for [DogBoard](https://github.com/silly-puppyy/DogBoard), the Android keyboard. The app downloads them
itself when you add a language; you don't need anything from this page.

This repository holds **releases only**. The code that builds the packs lives in DogBoard (`tools/i18n/auto_pack.py`,
`tools/i18n/dist_pack.py`), and each pack's `manifest.json` names the sources it was built from.

## Releases

| Tag | What |
|---|---|
| `index` | `index.json`: every pack, its version and its download link, and `index.json.sig`, its signature. The app reads only this address. |
| `packs-<format>.<content>.<fix>` | One `<language>.tar.xz` per language: the word list, word-sequence model and letter model the keyboard uses. |
| `models-<format>.<content>.<fix>` | Larger optional models (neural language models, language-specific swipe models), when there are any. |

The first number is the pack format: an app only installs packs whose format it knows. A pack can stay in an older
release while other languages move on; the index says where each one is.

## Integrity

The app installs a pack only when `index.json` verifies against the maintainers' public key built into the app (ECDSA
P-256 / SHA-256), the archive matches the SHA-256 in the index, and every file in it matches the size and SHA-256 in
its manifest. A pack that fails any check is not installed, and the one already on the phone stays.

## Licences and sources

The packs are derived from:

- [Leipzig Corpora Collection](https://wortschatz.uni-leipzig.de/en/download) (CC BY 4.0): word lists, word-sequence
  models and letter models;
- [wordfreq](https://github.com/rspeer/wordfreq) 3.1.1 (CC BY-SA 4.0): word frequencies, where a language has a list;
- [Tatoeba](https://tatoeba.org) (CC BY 2.0 FR): word pairs, where a language has enough sentences;
- Hunspell dictionaries for a few hand-built packs (each named with its licence in that pack's manifest).

Where wordfreq data is used, the pack is shared under **CC BY-SA 4.0**; each pack's `manifest.json` lists exactly
which sources and licences apply to it.
