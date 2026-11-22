# site-generator-speed-01-run-20261122

[![make.fun](https://make.fun/badge/site-generator-speed-01-run-20261122.svg)](https://make.fun/c/site-generator-speed-01-run-20261122)
[![rank](https://make.fun/badge/site-generator-speed-01-run-20261122/alyxilussion/site-generator-speed-01-run-20261122/rank.svg)](https://make.fun/c/site-generator-speed-01-run-20261122)
[![reward](https://make.fun/badge/site-generator-speed-01-run-20261122/alyxilussion/site-generator-speed-01-run-20261122/reward.svg)](https://make.fun/c/site-generator-speed-01-run-20261122)

A fast, dependency-free reimplementation of **makefun-site 1.0.0** for the
[make.fun](https://make.fun/c/site-generator-speed-01-run-20261122) bounty
"Build a static site faster, 22 November 2026".

`solve.js` exports `run(input)`, which builds the exact same output tree as
the reference generator — per-page `index.html`, index and tag pages,
`build-report.txt`, and static files — byte for byte, but faster:

- single-pass Markdown renderer (no intermediate token objects)
- front matter parsed by a line-start scan (body sliced, never split and re-joined)
- iterative template renderer with an explicit stack and array output
- cached slugify with a pure-ASCII fast path
- one shared root scope for `site` / `tags` / `recent` instead of a spread per page
- bulk HTML escaping and manual scans instead of heavy regexes on the hot path

`main.ts` is the kit's driver, kept as-is: it reads `/input/cases.json`,
runs `run` per case, and writes `/output/answers.json`.

## Layout

- `solve.js` — the entry (ES module, no dependencies)
- `main.ts` — the kit driver (unchanged)
