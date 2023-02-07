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

  let playing = false;
  let play_interval : ReturnType<typeof setInterval>; 

  function increment() {
    if (step < highlights.length - 1) {
      step += 1;
    }
    else {
      togglePlaying();
      step = 0;
    }
  }

  function togglePlaying() { playing = !playing; }

  $: {
    if (!playing) { clearInterval(play_interval); }
    else {
      play_interval = setInterval(increment, 1250); 
    }
  }
</script>

<div class="description">
  <h3>Autoplay Example</h3>
  <button on:click={togglePlaying}>
    {#if playing}
      Pause
    {:else}
      Play
    {/if}
  </button>
  <p>{step + 1} / {highlights.length}</p>
</div>
<p>
  Since controlling the step only requires changing the value, you can use functions to have an autoplay function.
</p>
<div class="trace">
  <Trace {step} {highlights}>
    <TLine>const name = "Joe"</TLine>
    <TLine>// use that variable</TLine>
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

  p { margin: 0 auto; }
</style>


