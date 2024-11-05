<script>
    import Konva from 'konva';
    import { onDestroy, onMount } from 'svelte';

    // props
    export let width;
    export let height;

    let container;
    let stage;

    onMount(() => {
        stage = new Konva.Stage({
            container: container,
            width: {width},
            height: {height}
        })
    });

    onDestroy(() => {
        if(stage) stage.destroy();
    });

</script>

<div bind:this={container}>
    <slot/>
</div>