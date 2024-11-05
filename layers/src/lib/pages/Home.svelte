<script>
  // import { onMount } from "svelte";
  // import Konva from "konva";

  import { Stage, Layer, Rect } from "../konva";

  let showCanvas = true;

  let x = 20;
  let widthStage = 300;

  let rect1, rect2;  

</script>

<input type="checkbox" bind:checked={showCanvas} />
<input type="range" bind:value={x} min="0" max="300" />
<input type="range" bind:value={widthStage} min="0" max="1000" />

<button on:click={() => {
  console.log(rect1.rect.getAttrs())
  console.log(rect2.rect.getAttrs())
  console.log(rect1.rect.getStage())
  rect2.rect.x(0);
}}>
  Get Rect info
</button>


<Stage width={widthStage} height={950}>
  <Layer draggable 
  on:click={(e) => {
    console.log('click')
  }}
  on:dragmove={(e) => {
    console.log(e)
  }}>
    {#if showCanvas}
      <Rect bind:this={rect1} x={x} y={20} fill="purple" width={200} height={100} />
    {/if}
    <Rect x={20} y={150} fill="red" width={200} height={100} />
    <Rect x={20} y={280} fill="blue" width={200} height={100} />
  </Layer>

  <Layer {x}>
    <Rect
      bind:this={rect2}
      x={20}
      y={400}
      fill="green"
      width={200}
      height={100}
      stroke="white"
      strokeWidth={4}
      on:click={(e) => {
        console.log('click green')
      }}
      on mousedown={(e) => {
        console.log('mousedown green')
      }}
    />
    <Rect x={20} y={520} fill="white" width={200} height={100} />
    <Rect x={20} y={650} fill="yellow" width={200} height={100} />
  </Layer>
</Stage>
