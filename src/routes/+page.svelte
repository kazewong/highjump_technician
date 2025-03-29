<script lang="ts">
	import { onMount } from 'svelte';
	import anime from 'animejs';

	import test_image from '$lib/assets/straight/ezgif-frame-017.jpg';
	let pageHeight = 0;

	const imageModules = import.meta.glob(
		'$lib/assets/straight//*.{avif,gif,heif,jpeg,jpg,png,tiff,webp,svg}',
		{
			eager: true,
			query: {
				enhanced: true
			}
		}
	);
	console.log(imageModules);

	let scrollProgress = $state(0);
	let heading = $state('The Straight');
	const scrollSensitivity = 0.01;

	function handleWheel(event) {
		scrollProgress += event.deltaY * scrollSensitivity;
		scrollProgress = Math.max(0, Math.min(100, scrollProgress));
	}
	onMount(() => {
		pageHeight = document.body.clientHeight;
	});
</script>

<svelte:window on:wheel={handleWheel} />

<header class="fixed mb-12 h-screen flex-row items-center justify-center overflow-hidden">
	<div class="container mx-auto px-4">
		<div class="py-4">
			<p class="text-center text-lg">Scroll Y: {scrollProgress}</p>
		</div>
	</div>
</header>

<enhanced:img
	src={imageModules[Object.keys(imageModules)[25]].default}
	alt="Preloaded Image"
	class="fixed top-0 left-0 -z-5 h-full w-full object-cover"
/>

<div class="hero bg-opacity-0 min-h-screen">
	<div class="hero-content text-center">
		<div class="max-w-md">
			<h1 class="text-5xl font-bold">{heading}</h1>
		</div>
	</div>
</div>
