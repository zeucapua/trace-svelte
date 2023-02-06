<script lang="ts">
  import { getContext } from "svelte";

  const index = getContext("set_index");
  const highlighted = getContext("highlighted");

  let value = index();

</script>

{#if $highlighted.includes(value)}
  <div id="traced" class="tline_container"> 
    <slot />
  </div>
{:else}
  <div class="tline_container">
    <slot />
  </div>
{/if}

<style>
  .tline_container {
    display: inline-block;  
    margin: 0;
    padding: 0.5rem;
    opacity: 0.5;
  }

  #traced {
    opacity: 1;
  }
</style>
