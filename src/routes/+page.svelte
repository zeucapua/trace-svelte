<script lang="ts">
  import Trace from "$lib/Trace.svelte"; 
  import TLine from "$lib/TLine.svelte";

  let step = 0;
  let highlights = [
    [0,0],
    [1,2],
    [0,0],
    [2,2]
  ];

  function increment() { step = step === highlights.length - 1 ? step : step += 1; }
  function decrement() { step = step === 0 ? step : step -= 1; }
</script>


<Trace {step} {highlights}>
  <TLine>One</TLine>
  <TLine>Two</TLine>
</Trace>


<button on:click={increment}>+</button>
<button on:click={decrement}>-</button>
