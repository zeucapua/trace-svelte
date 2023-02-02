<script lang="ts">
  import { getContext } from "svelte";

  const index = getContext("set_index");
  const highlighted = getContext("highlighted");

  let value = index();

</script>

{#if value >= $highlighted[0] && value <= $highlighted[1]}
  <div id="tline_container" class="traced">
    <slot />
  </div>
{:else}
  <div id="tline_container">
    <slot />
  </div>
{/if}

<style>
  #tline_container {
    display: inline-block;  
  }

  .traced {
    background-color: lightblue;
  }
</style>
