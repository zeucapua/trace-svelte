<script lang="ts">
  import { setContext } from "svelte";
  import { writable } from "svelte/store";

  // props
  export let step : number = 0;
  export let highlights : number[][] = [[0]];

  // for context to TLine
  let start_index = 0;
  let highlighted = writable(highlights[0]); 
  let setIndex = () => { start_index += 1; return start_index; };

  setContext("set_index", setIndex);
  setContext("highlighted", highlighted);

  $: $highlighted = highlights[step];
</script>

<div id="trace_container">
  <slot />
</div>


<style>
  #trace_container {
    display: flex;
    flex-direction: column;
    width: 100%;
    gap: 0.5rem;
    padding:0.5rem;
  }
</style>
