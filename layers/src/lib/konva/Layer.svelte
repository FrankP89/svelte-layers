<script>
  import Konva from "konva";
  import { getContext, setContext } from "svelte";
  import { stageKey, layerKey } from "./context-keys";

  const { getStage } = getContext(stageKey);
  const stage = getStage();
  const layer = new Konva.Layer();

  setContext(layerKey, layer); // Since layer is not undefined at any point, there's no need to create a getLayer function

  stage.add(layer);
</script>

<slot />
