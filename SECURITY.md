# Security

- The worker has **no authentication**. Bind it to `127.0.0.1` or a private interface, never the public internet.
- The guard is a classifier, not an authorization boundary. Do not use a classifier verdict as the only control for destructive actions.
- `run_pinned` executes a script after a hash check and denies symlinks; it is not a sandbox. Use OS sandboxing for untrusted code.
- Prototype and text caches live in `~/.cache/gamai_guard/` and contain no secrets.
- The antibody store defaults to `~/.local/state/gamai-guard/antibodies.db` (mode `0700`);
  override with `GAMAI_GUARD_DB`. Symlinked, non-regular and world-writable stores are
  refused, so a local user cannot silently disable detection by rewriting the DB.
- Report vulnerabilities privately via GitHub Security Advisories.
