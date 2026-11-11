# escape-compat

Compatibility manifest for escape's engines: **Codex**, **Claude Code**, and **OpenCode**.

escape checks the remote [manifest.json](manifest.json), served by `raw.githubusercontent.com`,
at most once per hour.

## Manifest format

| Field | Description |
| --- | --- |
| `version` | Manifest version, incremented with every change. |
| `updatedAt` | Timestamp of the latest update. |
| `compatibility` | List of engine compatibility entries. |
| `compatibility[].engine` | Engine identifier: `codex`, `claude`, or `opencode`. |
| `compatibility[].escapeRange` | escape versions to which the entry applies. |
| `compatibility[].recommendedVersion` | Recommended engine version. |
| `compatibility[].recommendedRange` | Recommended engine version range. |
| `compatibility[].ranges` | List of version ranges and their compatibility statuses. |
| `compatibility[].ranges[].range` | Engine version range. |
| `compatibility[].ranges[].status` | One of `supported`, `graceful`, `unsupported`, `broken`, or `unknown`. |

Version ranges use T3 Code-style syntax: `>=`, `<`, `=`, `^`, spaces, and `||`.

## Update rules

- **Increment `version` with every manifest change.** escape ignores manifests with a lower version
  than the one it already knows.
- **Remote updates can only restrict compatibility.** An engine version can run only if the manifest
  embedded in the escape build marks it as `supported`.
- Mark engine versions as `broken` or `unsupported`, update the recommended version, and adjust
  messages without releasing a new version of escape.

## Privacy

The manifest contains no personal data or secrets.
