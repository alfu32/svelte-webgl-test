<script lang="ts">
import {onMount} from "svelte"
import { drawScene, fsSource, getProgramInfo, initBuffers, initShaderProgram, vsSource } from "./shaders";
export let width = 640
export let height = 640
  let canvas:HTMLCanvasElement
  let gl:WebGL2RenderingContext
  onMount(()=>{
    console.log(canvas)
    gl = canvas.getContext('webgl2')!!;
    console.log(gl)
    // gl?.useProgram(program); 
    // Set clear color to black, fully opaque
    //gl.clearColor(0.0, 0.0, 0.0, 1.0);
    // Clear the color buffer with specified clear color
    //gl.clear(gl.COLOR_BUFFER_BIT);

    // Here's where we call the routine that builds all the
    // objects we'll be drawing.
    const buffers = initBuffers(gl)!;
    const shaderProgram = initShaderProgram(gl,vsSource,fsSource)!;
    const programInfo = getProgramInfo(gl,shaderProgram);
    // Draw the scene
    console.log({
      buffers,
      shaderProgram,
      programInfo,
    })
    drawScene(gl, programInfo, buffers);
  })
</script>

<canvas bind:this={canvas} {width} {height}>
  Please use a browser that supports "canvas"
</canvas>