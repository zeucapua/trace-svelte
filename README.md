# Trace: A line by line highlighter for Svelte

**STATUS**: barely alpha, like a sad omegaverse protagonist.

## Components:
- **Trace.svelte**: A wrapper around the lines that control what is highlighted.
- **TLine.svelte**: Used for each individual line inside the Trace component.

## Usage:
```svelte
<!-- App.svelte -->
<script>
  let step = 0; // based on the highlights array below
  let highlights = [
    [0,0], // lines start at 1, so for no highlights, use 0
    [1,1], // to highlight a single line, use same number on both
    [0,0], // another empty highlight step
    [1,2], // use a range to select multiple lines (inclusive)
  ]
</script>

<Trace {step} {highlights}>
  <TLine>const variable = 1;</TLine>
  <TLine>console.log(variable)</TLine>
</Trace>
```
