<script>
  import Konva from "konva";
  import { onDestroy, onMount, setContext } from "svelte";
  import { stageKey } from "./context-keys";

  // props
  // export let width;
  // export let height;

  let container;
  let stage; // Stage can be undefined if not mounted

  $: if(stage) stage.setAttrs($$props); // Update stage attributes

  setContext(stageKey, {
    getStage: () => stage,
  });

  onMount(() => {
    stage = new Konva.Stage({
      container: container,
      // width: width ,
      // height: height ,
      ...$$props
    });
  });

  onDestroy(() => {
    if (stage) stage.destroy();
  });
</script>

<div bind:this={container}>
    <!-- Only render if stage is defined -->
    {#if stage} 
        <slot />
    {/if}
</div>
