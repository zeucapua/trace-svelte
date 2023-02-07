<script>
  import Trace from "$lib/Trace.svelte";
  import TLine from "$lib/TLine.svelte";

  let step = 0;
  let highlights = [
    [],
    [1],
    [1,3],
    [2]
  ];

  function increment() {
    step = step === highlights.length - 1 ? step : step += 1;
  }
  function decrement() {
    step = step === 0 ? step : step -= 1;
  }
</script>

<div class="description">
  <h3>Simple Example</h3>
  <button on:click={decrement}>{"<-"}</button>
  <button on:click={increment}>{"->"}</button>
  <p>{step + 1} / {highlights.length}</p>
</div>
<div class="trace">
  <Trace {step} {highlights}>
    <TLine>const name = "Joe"</TLine>
    <TLine>// use that variable!</TLine>
    <TLine>console.log(name)</TLine>
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
</style>
