# TODO

Outstanding tasks before ingest points or pipeline features can be activated.

## Karakeep Ingest Point

- [ ] **Clean up Karakeep tags** — normalize tag names, remove duplicates, and establish a consistent taxonomy before the pipeline depends on them.
  - Dashboard: https://karakeep.kevininscoe.com/dashboard/tags
- [ ] **Create Karakeep API credentials** — generate a read-only API token and store it per `~/ai/directives/storing-secrets.md`.
  - Once done, update `ingest-points/karakeep.md` to remove the PENDING status and add the credential location.

## Glean Ingest Point

- [ ] **Migrate Glean API token from 1Password to OpenBao** — upsert the token into OpenBao at `app/glean` → field `api_token`, consistent with other secrets (see `~/ai/directives/storing-secrets.md`).
  ```bash
  bao kv put -mount=app glean api_token="PASTE_TOKEN_FROM_1PASSWORD"
  bao kv get -mount=app glean   # verify
  ```
  Once done, update `ingest-points/glean.md` credential location to reflect OpenBao path.

## KnowledgeVault Manual Ingest — Tracking Strategy

- [ ] **Decide how processed files are tracked** — no SQLite exists for this ingest point. Choose one before first pipeline run:
  - **A — delete after processing** (simplest)
  - **B — move to `processed/` subtree** (preserves originals)
  - **C — manifest file** (`.processed-manifest` at ingest root)
  - See `ingest-points/knowledgevault-ingest.md` for full description of each option.

## Interest / Relevance Criteria

- [ ] Define how the AI agent selects which items to ingest from each source (tag rules, keyword filters, scoring, etc.).
