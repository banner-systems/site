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

    // Precompute constants
    const scale = 0.005;
    const threshold = 0.01;

    for (let y = 0; y < canvas.height; y++) {
      const yScaled = (y + offsetY) * scale; // Precompute scaled y-coordinate

      for (let x = 0; x < canvas.width; x++) {
        const xScaled = x * scale; // Precompute scaled x-coordinate
        const noiseValue = simplex(xScaled, yScaled, 0);

        // Draw contour lines based on noise thresholds
        const remainder = Math.abs(noiseValue % contourInterval);
        if (remainder < threshold) {
          ctx.fillStyle = `rgba(255, 255, 255, 0.7)`;
          ctx.fillRect(x, y, 1, 1); // Draw a 1x1 pixel rectangle instead of line segments
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

