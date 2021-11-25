<script>
	import { quintOut } from 'svelte/easing';
	import { fade, draw, fly } from 'svelte/transition';
	import { expand } from '../js/custom-transitions.js';
	import { inner, outer } from '../js/shape.js';

</script>

<div class="logoWrapper">
	<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 103 124" width="100px" height="100px">
		<g out:fade="{{duration: 200}}" opacity=0.2>
			<path
				in:expand="{{duration: 400, delay: 1000, easing: quintOut}}"
				style="stroke: #ff3e00; fill: #ff3e00; stroke-width: 50;"
				d={outer}
			/>
			<path
				in:draw="{{duration: 1000}}"
				style="stroke:#ff3e00; stroke-width: 1.5"
				d={inner}
			/>
		</g>
	</svg>

	<div class="centered" out:fly="{{y: -20, duration: 800}}">
		{#each 'SVELTE' as char, i}
			<span
				in:fade="{{delay: 1000 + i * 150, duration: 800}}"
			>{char}</span>
		{/each}
	</div>

<link href="https://fonts.googleapis.com/css?family=Overpass:100,400" rel="stylesheet">

</div>

<style>
	svg {
		width: 100%;
		height: 100%;
	}

	path {
		fill: white;
		opacity: 1;
	}

	.centered {
		font-size: 30px;
		position: absolute;
		left: 50%;
		top: 50%;
		transform: translate(-50%,-50%);
		font-family: 'Overpass';
		letter-spacing: 0.12em;
		color: #676778;
		font-weight: 400;
	}

	.centered span {
		will-change: filter;
	}

    .logoWrapper {
        max-width: 500px;
        width: 100%;
        height: 500px;
        position: relative;
        margin: 100px auto;
    }
</style>