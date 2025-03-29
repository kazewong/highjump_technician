

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
  )
  console.log(imageModules);
  console.log(imageModules[Object.keys(imageModules)[0]]);

  let scrollY = $state(0);
  let heading = $state("The Straight");


  onMount(() => {
    pageHeight = document.body.clientHeight;
  });

</script>

<svelte:window on:scroll={() => {
    scrollY = window.scrollY;

    }} />

<header class="fixed flex-row items-center justify-center h-screen mb-12 overflow-hidden">
  <div class="container mx-auto px-4">
    <div class="py-4">
        <p class="text-center text-lg">Scroll Y: {scrollY}</p>
    </div>
  </div>
</header>

<enhanced:img src={imageModules[Object.keys(imageModules)[25]].default} alt="Preloaded Image" class="fixed top-0 left-0 w-full h-full object-cover z-0" />

<div class="hero bg-red-400 min-h-screen">
  
  <div class="hero-content text-center">
    <div class="max-w-md">
      <h1 class="text-5xl font-bold">{heading}</h1>
    </div>
  </div>
</div>

