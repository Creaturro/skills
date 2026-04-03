---
name: playground
description: Creates interactive HTML playgrounds — self-contained single-file explorers with live preview and controls. Use when the user asks to make a playground, explorer, or interactive tool for a topic.
---

# Playground Builder

A playground is a self-contained HTML file with interactive controls on one side, a live preview on the other, and a prompt output at the bottom with a copy button. The user adjusts controls, explores visually, then copies the generated prompt back into Claude.

## When to use this skill

When the user asks for an interactive playground, explorer, or visual tool for a topic — especially when the input space is large, visual, or structural and hard to express as plain text.

## How to build a playground

1. **Identify the playground type** from the user's request
2. **Build a single HTML file** with:
   - Controls panel (inputs, sliders, selects, toggles)
   - Live preview area (updates instantly on every change)
   - Prompt output with copy button
3. **Open in browser** after writing the file

## Core requirements (every playground)

- **Single HTML file.** Inline all CSS and JS. No external dependencies.
- **Live preview.** Updates instantly on every control change. No "Apply" button.
- **Prompt output.** Natural language, not a value dump. Only mentions non-default choices. Includes enough context to act on without seeing the playground. Updates live.
- **Copy button.** Clipboard copy with brief "Copied!" feedback.
- **Sensible defaults + presets.** Looks good on first load. Include 3-5 named presets.
- **Dark theme.** System font for UI, monospace for code/values. Minimal chrome.

## State management pattern

Keep a single state object. Every control writes to it, every render reads from it.

```javascript
const state = { /* all configurable values */ };
function updateAll() {
  renderPreview();
  updatePrompt();
}
// Every control calls updateAll() on change
```

## Common mistakes to avoid

- Prompt output is just a value dump — write it as a natural instruction
- Too many controls at once — group by concern, hide advanced in collapsible section
- Preview doesn't update instantly — every control must trigger immediate re-render
- No defaults or presets — starts empty or broken on load
- External dependencies — playground must be fully self-contained
