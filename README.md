# opencode-context-progress

Compact context usage widget for the OpenCode sidebar.

## What it shows

- **Line 1:** context progress bar + percentage used
- **Line 2:** consumed tokens / model context window / session cost

## How it works

- Uses the latest assistant response with token data
- Token count formula: `input + output + reasoning + cache.read + cache.write`
- Context window is read from the active provider/model metadata
- Bar color changes with usage:
  - normal: `< 70%`
  - warning: `>= 70%`
  - danger: `>= 90%`

## Install

Requires OpenCode 2.0 or newer.

```sh
opencode plugin add craig-dougan-maersk/opencode-context-progress
```

Project-only: add `"craig-dougan-maersk/opencode-context-progress"` to `plugins` in `opencode.jsonc`.

### Collapsed by default

The panel starts collapsed so the sidebar stays quiet; click the header arrow to expand it. Pass the option as `false` to start expanded:

```jsonc title="opencode.jsonc"
{
  "plugins": [
    { "package": "craig-dougan-maersk/opencode-context-progress", "options": { "collapsedByDefault": true } }
  ]
}
```

## Credits

Derived from [streetturtle/opencode-better-sidebar](https://github.com/streetturtle/opencode-better-sidebar) (MIT), split into a standalone repository so OpenCode can install it directly.
