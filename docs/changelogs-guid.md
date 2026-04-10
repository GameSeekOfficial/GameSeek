# 📝 Changelog Guide

How to write changelog entries for GameSeek.

-----

## File Location

All changelogs go in the `/CHANGELOGS/` folder.

Name the file by date:

```
CHANGELOGS/
├── 2026-04-09.md
├── 2026-04-10.md
└── ...
```

-----

## Format

Use this template:

```markdown
# Changelog — DD.MM.YYYY

## ✨ New Features
- Short description of what was added

## 🐛 Bug Fixes
- Short description of what was fixed

## ⚡ Improvements
- Short description of what was improved

## 🗑️ Removed
- Short description of what was removed (if any)
```

-----

## Emoji Reference

|Emoji|Meaning                  |
|-----|-------------------------|
|✨    |New feature              |
|🐛    |Bug fix                  |
|⚡    |Performance / improvement|
|🔒    |Security fix             |
|🗑️    |Removed                  |
|🚀    |Deployment / release     |
|🎨    |UI / design change       |
|📝    |Docs update              |

-----

## Example Entry

```markdown
# Changelog — 09.04.2026

## ✨ New Features
- Added screen share support with multi-stream grid layout
- Added right-click context menu for message edit/delete

## 🐛 Bug Fixes
- Fixed audio element reference mismatch in VoicePanel
- Fixed memory leak in AudioContext cleanup

## ⚡ Improvements
- Moved speaking detection from rAF to setInterval to prevent flicker
```
