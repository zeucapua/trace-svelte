<script>
  import Trace from "$lib/Trace.svelte";
  import TLine from "$lib/TLine.svelte";

  let step = 0;
  let highlights = [
    [],
    [3],
    [4,5,6,7,8,9],
    [12,14],
    [13,15,16,17,18]
  ];
  let code = [
    "<script>",
    "  import { Trace, TLine } from \"trace-svelte\"",
    "  let step = 0; // control outside of component like a button",
    "  let highlights = [",
    "    [], // no highlights = empty array",
    "    [1], // to highlight a single line, (starts at 1)",
    "    [1,3], // include multiple lines",
    "    [2]",
    "  ]",
    "<\/script>",
    "",
    "// use step and highlights variables",
    "// and define the lines",
    "<Trace {step} {highlights}>",
    "  <TLine>const name = \"Joe\";</TLine>",
    "  <TLine>// use that variable!</TLine>",
    "  <TLine>console.log(name)</TLine>",
    "</Trace>"
  ];

  function increment() { if (step < highlights.length - 1) step += 1; }
  function decrement() { if (step > 0) step -= 1; }
</script>

<div class="description">
  <h3>How It Works</h3>
  <button on:click={decrement}>{"<-"}</button>
  <button on:click={increment}>{"->"}</button>
  <p>{step + 1} / {highlights.length}</p>
</div>
<p>This is a basic example. Still requires a way to increment/decrement the step.</p>
<div class="trace">
  <Trace {step} {highlights}>
    {#each code as line}
      <TLine>{line}</TLine>
    {/each}
  </Trace>
</div>

<style>
  .trace {
    width: 33%;
    margin: 0 auto;
    font-family: monospace;
    border: 2px solid black; 
  }

  .description {
    display: inline-flex;
    margin: 0 auto;
    flex-direction: row;
    gap: 16px;
    align-items: center;
  }

  button {
    width: fit-content;
    height: fit-content;
    padding: 4px;
  }

  p { margin: 0 auto; } 
</style>
