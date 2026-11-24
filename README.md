# MeshOMatic translations

Language files for [map.meshomatic.net](https://map.meshomatic.net). This repo holds only translation
strings; the site code lives elsewhere and pulls merged changes from here.

## How to help

1. Pick a language folder (`fr/`, `de/`, ...). `en/` is the source text; do not edit it here.
2. Edit the JSON values, never the keys.
3. Keep every `{placeholder}` and ICU block (`{count, plural, ...}`) exactly as in English.
   Context for each string is in `_meta/en.context.json`; agreed terms are in `glossary.json`.
4. In `_status/<lang>.json`, set the string's `state` to `reviewed` and `by` to your GitHub handle.
5. Open a pull request. One language per PR, please.

Most strings start as machine drafts (`state: machine`); the site shows a banner on those.
A fluent speaker marking them `reviewed` removes it.

Want a new language? Open an issue, or ask in the MeshOMatic Discord.

## How this repo stays in sync with MeshOMatic

English is the source. Nothing here runs on GitHub Actions; a maintainer
syncs by hand with `scripts/i18n/translations_sync.py` in the MeshOMatic repo.

**English goes out.** When English text changes on the site, a maintainer
opens a branch here that updates `en/*.json`, `_meta/en.context.json`,
`languages.json` and `glossary.json`. In `_status/<lang>.json`:

- an entry whose English changed is marked `"state": "stale"`; its old
  `src_hash` and `by` are kept, so you can see which English it was made from;
- a brand-new English key appears as `"state": "missing"`.

Your translations are never changed by this step.

**Translations come in.** Merged translations are copied back into the site
one language at a time, and only if the whole language passes the checks:

- every file is valid JSON;
- every key exists in the English files (no extra keys);
- every `{placeholder}`, `plural` / `select` argument and `<0>...</0>` tag
  in the English message is present, unchanged, in the translation;
- product terms in `glossary.json` (MeshCore, MeshOMatic, ...) stay verbatim;
- on-air (mesh) messages fit their byte limit from `_meta/en.context.json`;
- text is NFC-normalised, with no invisible or bidi control characters.

If any message fails, the whole language waits for a fix and nothing from it
is copied, so please run through the list above before opening a PR. When you
review a translation, set its `_status` entry to
`{"state": "reviewed", "src_hash": "<hash>", "by": "<you>"}`, where `<hash>`
is the first 12 hex digits of the SHA-256 of the English message's UTF-8 text
(for a `stale` entry, recompute it from the current English).

## License

Contributions are released under CC0 1.0 (public domain dedication); see `LICENSE`.
