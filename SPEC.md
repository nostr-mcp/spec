# nostr-mcp spec v0.1.0

## Purpose

Define a canonical, cross-language tool naming and schema standard for MCP tool servers that operate on Nostr data.

## Scope

- Canonical tool names for the nostr-mcp ecosystem.
- JSON Schemas for tool inputs and outputs.
- Tool status lifecycle (stable, planned, experimental, deprecated).
- Error semantics for tool invocation.
- Versioning and deprecation policy.

## Non-goals

- MCP-over-Nostr transport layers.
- Discovery networks or public announcement protocols.

## Canonical Naming

- All tools are snake_case.
- All tools are prefixed with `nostr_`.
- Names follow `nostr_<domain>_<verb>[_<object>]`.
- See `docs/tool-naming.md` for details.

## Registry

The canonical registry lives at `registry/tools.json`.

- The registry is the single source of truth for tool names.
- Each tool entry must include `name`, `status`, `summary`, `nip`, `input_schema`, and `output_schema`.
- Schemas must be valid JSON Schema (draft-07 compatible).
- `schemas/registry.schema.json` and `schemas/tool.schema.json` define validation rules for the registry.

## Error Semantics

Tool errors follow MCP JSON-RPC error conventions:

- Invalid parameters: `-32602`
- Internal errors: `-32603`

Servers should include a human-readable `message` and an optional `data` object.

## Versioning

- Spec versions are tagged in `CHANGELOG.md`.
- `spec_version` and `registry_version` in `registry/tools.json` must match the published spec.

## Deprecation Policy

- Deprecated tools remain listed with `status: "deprecated"`.
- No aliases are required in this spec; legacy names are removed when deprecated.
- Migration guidance is tracked in `MIGRATIONS.md`.

## Conformance

An SDK is conformant if it:

- implements the canonical tool names in `registry/tools.json`
- accepts and validates inputs against the defined schemas
- returns outputs conforming to the defined schemas

## Repository Layout

- `SPEC.md`: canonical spec
- `registry/tools.json`: tool registry
- `schemas/`: registry and tool JSON Schemas
- `docs/`: naming rules and roadmap
- `examples/`: registry and tool call examples
