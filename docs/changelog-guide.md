# Changelog guide

Releases are recorded in [`CHANGELOG.md`](../CHANGELOG.md) at the root of this repository. Add new work at the top, under a dated heading. Keep older notes in place.

Earlier updates were split across files in `CHANGELOGS/`. Those notes are merged into the single changelog. Do not add new files there.

## Format

```markdown
## YYYY-MM-DD

### Added
- What is new, in one short line

### Fixed
- What was broken, and the visible result

### Changed
- What works differently now

### Removed
- What was taken out
```

Leave out any heading that has no entries.

## Labels

| Heading | Use it for |
| --- | --- |
| Added | A new feature |
| Fixed | A bug fix |
| Changed | Behavior, performance, or design that already existed |
| Security | A security fix |
| Removed | Something taken out |
| Docs | Documentation only |

## Example

```markdown
## 2026-04-09

### Added
- Screen sharing with a grid for more than one stream
- A right-click menu to edit or delete a message

### Fixed
- Voice panel audio elements pointing at the wrong stream
- An AudioContext leak on cleanup

### Changed
- Speaking detection uses a timer instead of animation frames, so the indicator no longer flickers
```

Write for someone who uses the app. Name the screen or action they will notice.

[Changelog](../CHANGELOG.md) · [Documentation index](README.md)
