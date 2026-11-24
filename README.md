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

## License

Contributions are released under CC0 1.0 (public domain dedication); see `LICENSE`.
