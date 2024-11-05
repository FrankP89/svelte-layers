<script>
  import Konva from "konva";
  import { getContext, onDestroy, setContext, createEventDispatcher } from "svelte";
  import { stageKey, layerKey } from "./context-keys";

  // export let draggable = undefined;

  const { getStage } = getContext(stageKey);
  const stage = getStage();
  const layer = new Konva.Layer(
    {
    // draggable: true,
    ...$$props
    }
  );

  const dispatch = createEventDispatcher();

  // Multiple events can be added to the same listener
  layer.on("dragmove click mousedown", (e) => {
    
    dispatch(e.type, e);
  });

  // layer.on("click", (e) => {
  //   dispatch("click", e);
  // });

  

  $: if (layer) layer.setAttrs($$props);

  onDestroy(() => {
    if (layer) layer.destroy();
  });

  setContext(layerKey, layer); // Since layer is not undefined at any point, there's no need to create a getLayer function

  stage.add(layer);
</script>

<slot />
