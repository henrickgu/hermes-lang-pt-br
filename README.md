# hermes-lang-pt-br

**Portuguese (Brazil) language pack for [Hermes Agent](https://github.com/NousResearch/hermes-agent)** — the core CLI/gateway, the Ink TUI and the Desktop app, in pt-BR.

Text-only plugin: no code, no network, no permissions. Just catalogs.

## Install

```bash
hermes plugins install henrickgu/hermes-lang-pt-br
hermes plugins enable hermes-lang-pt-br
```

Then pick the language in Desktop settings (or set it in config):

```bash
hermes config set display.language pt-br
```

Restart the Desktop app (or start a new session) for the catalog to take effect.

## What's covered

| Surface | File | Keys | Coverage |
|---|---|---|---|
| Core (CLI, gateway, approvals) | `locales/pt-br.yaml` | 3,438 | 100% of the English core catalog |
| TUI (terminal) | `locales/pt-br.tui.yaml` | 1,301 | 100% of the English TUI catalog |
| Desktop (app) | `locales/pt-br.desktop.yaml` | 4,743 | ~95% of the English desktop catalog |

The core and TUI catalogs mirror the `pt` locale already bundled upstream — `pt-br` is
registered as a real variant so it always wins over the alias. The Desktop catalog is
the original contribution: before this pack, the Desktop app had no Portuguese at all.

## Requirements

- Hermes `>= 0.21` (language packs as plugins landed in 0.21; `provides_locales` support)
- Nothing else. No Python, no build step.

## Validating

```bash
hermes plugins validate .
```

Checks the manifest, the `provides_locales` declaration against the shipped files,
text-only leaves, and every key against the English reference catalogs.

## Placeholders

Function-valued English entries (e.g. `(date) => \`Cancels on ${date}.\``) are expressed as
strings with positional `{0}`, `{1}`, … placeholders in argument order. They are substituted
at runtime — they never reach the screen.

## Regenerating the Desktop catalog

The Desktop catalog is derived from `apps/desktop/src/i18n/en*.ts` on upstream `main`,
with translations reused from an earlier desktop PR ([#98933](https://github.com/NousResearch/hermes-agent/pull/98933))
where the keys still exist. Keys the upstream removed are dropped, so the pack never
carries dead strings.

## License

MIT
