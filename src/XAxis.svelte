<script>
	export let xScale;
	export let innerHeight;
	export let label;

	const numberOfTicks = (pixelsAvailable, pixelsPerTick = 140) =>
    Math.floor(Math.abs(pixelsAvailable) / pixelsPerTick);

  $: [xMin, xMax] = xScale.range();

  $: ticks = xScale.ticks(numberOfTicks(xMax - xMin));
</script>

<g transform={`translate(0 ${innerHeight})`}>
  <line 
		x1={xMin} 
		x2={xMax} 
		y1={0} 
		y2={0} 
		stroke='#bdc3c7'
	/>
  <text
    x={xScale.range()[1] / 2}
    text-anchor="middle"
    y={25}
		fill='#282828'
  >
    {label}
  </text>
</g>
