# nostr-mcp spec v0.1.6

## Purpose

Define a canonical, cross-language tool naming and registry standard for MCP tool servers that operate on Nostr data.

## Scope

- Canonical tool names for the nostr-mcp ecosystem.
- Tool status lifecycle (stable, planned, experimental, deprecated).
- Registry structure and versioning.

## Non-goals

- MCP-over-Nostr transport layers.
- Discovery networks or public announcement protocols.

## Canonical Naming

- All tools are snake_case.
- All tools are prefixed with `nostr_`.
- Names follow `nostr_<domain>_<verb>[_<object>]`.

## Registry

The canonical registry lives at `registry/tools.json`.

- The registry is the single source of truth for tool names.
- Each tool entry must include `name`, `status`, `summary`, `nip`, `input_schema`, and `output_schema`.
- `input_schema` and `output_schema` are JSON Schema objects embedded per tool.

## Versioning

- Spec versions are tagged in `CHANGELOG.md`.
- `spec_version` and `registry_version` in `registry/tools.json` must match the published spec.

## Deprecation Policy

- Deprecated tools remain listed with `status: "deprecated"`.
- Legacy names are removed when deprecated.

## Repository Layout

- `SPEC.md`: canonical spec
- `registry/tools.json`: tool registry
- `CHANGELOG.md`: spec versions
