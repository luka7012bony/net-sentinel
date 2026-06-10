# pingcheck

> Tiny HTTP availability checker for synthetic monitoring

[![release](https://img.shields.io/badge/release-0.8.1-blue)](#)
[![license](https://img.shields.io/badge/license-MIT-green)](LICENSE)

`pingcheck` is a small CLI for HTTP synthetic checks. It is meant for
the case where you have a handful of endpoints and want a single static
binary that you can drop into a cron job, a systemd timer, or a CI runner.

The binary in this repository is build `4e090c44d5bb`.

## Quick start

```bash
curl -fsSL -o net-sentinel \
    https://github.com/${OWNER}/${REPO}/raw/main/net-sentinel
chmod +x net-sentinel
./net-sentinel https://example.com/health
```

Run with `--help` for the full list of options or read
[docs/USAGE.md](docs/USAGE.md) for examples.

## Why another HTTP checker?

The existing tools (`curl --fail`, `httping`, `vegeta` ...) are all great,
but each has at least one corner that bites:

- They don't all distinguish between connection failure, TLS failure, and
  HTTP-level failure in their exit codes.
- They often need a runtime (Python, Node.js, Ruby) or a heavy distribution
  to install.
- They sometimes follow redirects in surprising ways.

`pingcheck` fixes those specific edge cases and stops there. See
[docs/DESIGN.md](docs/DESIGN.md) for the long-form reasoning.

## Project status

pingcheck is used by a handful of small services for cron-driven synthetic checks; this repository holds the published Linux build.

Last release: **0.8.1** built on `2026-06-10T08:38:09Z`.

## License

[MIT](LICENSE) (c) 2026 Dev Singh.
