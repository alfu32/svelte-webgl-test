<script lang="ts">
import {onMount} from "svelte"
  let canvas:HTMLCanvasElement
  onMount(()=>{
    
  })
</script>

<canvas bind:this={canvas}>
  Please use a browser that supports "canvas"
</canvas>