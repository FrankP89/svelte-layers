<script>
  import Konva from "konva";
  import { getContext, onDestroy, setContext } from "svelte";
  import { stageKey, layerKey } from "./context-keys";

  export let draggable = undefined;

  const { getStage } = getContext(stageKey);
  const stage = getStage();
  const layer = new Konva.Layer({
    draggable: true,
  });

  onDestroy(() => {
    if (layer) layer.destroy();
  });

  setContext(layerKey, layer); // Since layer is not undefined at any point, there's no need to create a getLayer function

  stage.add(layer);
</script>

<slot />
