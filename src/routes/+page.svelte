<script lang="ts">
	import { onMount } from 'svelte';
	import { animate, createTimer, utils } from 'animejs';

  // Loading images
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

  // Create scroll progress and heading state
	let scroll_progress = $state(0);
	let heading = $state('The Straight');
	let section_counter = $state(0);
	const scrollSensitivity = 0.01;

	function handleWheel(event: WheelEvent) {
		scroll_progress += event.deltaY * scrollSensitivity;
		scroll_progress = Math.max(-30, Math.min(30, scroll_progress));
		if (scroll_progress == 30) {
			section_counter += 1;
			scroll_progress = 0;
		} else if (scroll_progress == -30) {
			section_counter -= 1;
			scroll_progress = 0;
		}
		section_counter = Math.max(0, Math.min(2, section_counter));

	}

  // Animate images

  let index: number = $state(0);
  var counter = {
    value: 0,
  };
  function animateImages() {
		animate(counter, {
			value: 45,
			duration: 3000,
			easing: 'easeOutCirc',
			modifier: utils.round(1),
			onUpdate: function() {
				index = counter.value;
			},
		})
    }
  onMount(() => {
    animateImages();
  });

</script>

<svelte:window on:wheel={handleWheel} />

<header class="fixed mb-12 h-screen flex-row items-center justify-center overflow-hidden">
	<div class="container mx-auto px-4">
		<div class="py-4">
			<p class="text-center text-lg">Scroll Y: {scroll_progress} | Section: {section_counter}</p>
		</div>
	</div>
</header>

<!-- <enhanced:img
	src={imageModules[Object.keys(imageModules)[index]].default}
	alt="Preloaded Image"
	class="fixed top-0 left-0 -z-5 h-full w-full object-cover"
/> -->

<div class="hero bg-opacity-0 min-h-screen">
	<div class="hero-content text-center">
		<div class="max-w-md">
			<h1 class="text-5xl font-bold">{heading}</h1>
		</div>
	</div>
</div>
