# MCP Tools Hub releases

Public distribution point for MCP Tools Hub: signed catalog, signed package manifests, revocation list, delegation documents and package artifacts.

Everything here is **static content produced by `mth-release`** from the private `mcp-hub` repository. Nothing in this repository is a secret, and nothing here is trusted by itself: the Hub verifies every document against an IT-provisioned root key (Ed25519, `mth-sig/1`) and every artifact against its SHA-256 before it extracts or runs anything.

Layout (see the design note `DISTRIBUTION.md` in the private repository):

- `catalog/catalog.json` and `.sig`
- `trust/revocation.json`, `trust/delegations/<key_id>.json`, `trust/root-rotation-<n>.json` (each with a `.sig`)
- `manifests/<package>-<version>-<channel>.json` (each with a `.sig`)
- `artifacts/<name>.zip` are published as GitHub Release assets

Do not edit files here by hand; a hand-edited file fails verification and is ignored by the Hub.