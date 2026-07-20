# plugin-blast-radius

First-party OpenLeash plugin that guards destructive tools and broad data operations.

When it detects a destructive operation, the plugin also publishes a short-lived typed session annotation through the Island Contribution API. OpenLeash renders that annotation in Live Sessions; this plugin does not own or inject UI.

This is a first-party OpenLeash plugin repository. The plugin owns its domain logic, prompts, schemas, parsing, and local fallbacks. OpenLeash provides only primitive runtime capabilities such as evaluator LLM calls, plugin-scoped storage, signals, logs, usage records, notifications, and selected host context.

## Source

- `src/manifest.ts` declares events, permissions, settings, ordering, and metadata.
- `src/index.ts` implements the plugin.
- `src/openleash-plugin-runtime.ts` contains tiny local helper types used by this standalone repo.

## Configuration scope

The plugin defines one manifest schema and consumes one request-scoped effective configuration. OpenLeash, not this plugin, merges organization defaults, matching organization agent profiles, and permitted user/global or per-agent settings. A mandatory organization install cannot be disabled by an employee, but its configuration may remain editable when the admin leaves it unlocked. The same plugin code runs in Individual Open Source, personal or organization OpenLeash Cloud, and Private Cloud.

## Development

```bash
npm install
npm run typecheck
```

## Runtime

OpenLeash loads reviewed plugins by manifest metadata and executes their handlers inside the managed plugin runtime.
