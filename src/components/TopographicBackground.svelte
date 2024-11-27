<script>
  import { onMount } from 'svelte';
  import { createNoise3D } from 'simplex-noise';

  let canvas;
  let ctx;
  let simplex;

  const contourInterval = 0.2; // Determines density of contour lines
  const scrollSpeed = 0.000; // Controls the scrolling speed
  let offsetY = 0; // Used for infinite scrolling

  const resizeCanvas = () => {
    canvas.width = window.innerWidth;
    canvas.height = window.innerHeight;
  };

  const drawTopography = () => {
    ctx.clearRect(0, 0, canvas.width, canvas.height);

    for (let y = 0; y < canvas.height; y++) {
      for (let x = 0; x < canvas.width; x++) {
        const noiseValue = simplex(x * 0.005, (y + offsetY) * 0.005, 0);

        // Draw contour lines based on noise thresholds
        if (Math.abs(noiseValue % contourInterval) < 0.01) {
          ctx.beginPath();
          ctx.strokeStyle = `rgba(255, 255, 255, 0.7)`;
          ctx.lineWidth = 0.5;
          ctx.moveTo(x, y);
          ctx.lineTo(x + 1, y + 1); // Tiny line segment for each noise value
          ctx.stroke();
        }
      }
    }
  };

  const animate = () => {
    offsetY += scrollSpeed * canvas.height; // Simulate downward scrolling
    drawTopography();
    //requestAnimationFrame(animate);
  };

  onMount(() => {
    ctx = canvas.getContext('2d');
    simplex = new createNoise3D();

    resizeCanvas();
    window.addEventListener('resize', resizeCanvas);

    animate();

    return () => {
      window.removeEventListener('resize', resizeCanvas);
    };
  });
</script>

<canvas bind:this={canvas} style="position: fixed; top: 0; left: 0; width: 100%; height: 100%;"></canvas>

<style>
  canvas {
    z-index: -1; /* Place behind content */
    background: #000; /* Black background */
  }
</style>

