<script>
  // import { onMount } from "svelte";
  // import Konva from "konva";

  import { Stage, Layer, Rect } from "../konva";

  let showCanvas = true;

  let x = 20;
  let widthStage = 300;

</script>

<input type="checkbox" bind:checked={showCanvas} />
<input type="range" bind:value={x} min="0" max="300" />
<input type="range" bind:value={widthStage} min="0" max="1000" />

<Stage width={widthStage} height={950}>
  <Layer draggable>
    {#if showCanvas}
      <Rect x={x} y={20} fill="purple" width={200} height={100} />
    {/if}
    <Rect x={20} y={150} fill="red" width={200} height={100} />
    <Rect x={20} y={280} fill="blue" width={200} height={100} />
  </Layer>

  <Layer {x}>
    <Rect
      x={20}
      y={400}
      fill="green"
      width={200}
      height={100}
      stroke="white"
      strokeWidth={4}
    />
    <Rect x={20} y={520} fill="white" width={200} height={100} />
    <Rect x={20} y={650} fill="yellow" width={200} height={100} />
  </Layer>
</Stage>
