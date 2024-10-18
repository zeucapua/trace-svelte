# trace-svelte: A line by line highlighter for Svelte

**STATUS**: alpha.

Visit [trace-svelte.vercel.app](https://trace-svelte.vercel.app) to check more examples and a live editor

## Components:
- **Trace.svelte**: A wrapper around the lines that control what is highlighted.
- **TLine.svelte**: Used for each individual line inside the Trace component.

## Usage:
```svelte
<!-- App.svelte -->
<script>
  import { Trace, TLine } from "trace-svelte";

  let step = 0; // based on the highlights array below
  let highlights = [
    [], // no highlights = empty array
    [1], // to highlight a line, add to array (starts at 1) 
    [1,3], // include multiple lines
    [2]
  ]
</script>

<Trace {step} {highlights}>
  <TLine>const name = "Joe";</TLine>
  <TLine>// use that variable</TLine>
  <TLine>console.log(variable)</TLine>
</Trace>
```
