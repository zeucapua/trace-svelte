<script lang="ts">
  import Trace from "$lib/Trace.svelte"; 
  import TLine from "$lib/TLine.svelte";

  let step = 0;
  let highlights = [
    [],
    [1],
    [1,3],
    [2]
  ];

  function increment() { step = step === highlights.length - 1 ? step : step += 1; }
  function decrement() { step = step === 0 ? step : step -= 1; }
</script>

<main>
  <div class="trace">
    <Trace {step} {highlights}>
      <TLine>
        <p style:margin="0" style:font-family="monospace" style:font-size="16px">
          const name = "Joe";
        </p>
      </TLine>
      <TLine>
        <p style:margin="0" style:font-family="monospace" style:font-size="16px">
          // use that variable!
        </p>
      </TLine>
      <TLine>
        <p style:margin="0" style:font-family="monospace" style:font-size="16px">
          console.log(name);
        </p>
      </TLine>
    </Trace>
  </div>

  <div class="control">
    <button on:click={decrement}>{"<-"}</button>
    <button on:click={increment}>{"->"}</button>
  </div>
</main>

<style>
  main {
    display: flex;
    gap: 0.5rem;
    flex-direction: column;
    justify-content: center;
    align-content: center;
  }

  .trace {
    width: 33%; 
    margin: 0 auto;
  }

  .control {
    display: inline-flex;
    flex-direction: row;
    margin: 0 auto;
    gap: 0.5rem;
  }
</style>
