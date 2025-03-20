

<script lang="ts">
  import { onMount } from 'svelte';
  import anime from 'animejs';

  let pageHeight = 0;

  onMount(() => {
    pageHeight = document.body.clientHeight;
  });


  let scrollY = $state(0);

  let video: HTMLVideoElement;
  let text = 'The Straight';

  $effect(() => {
      if (scrollY < pageHeight / 4) {
      anime({
          targets: video,
          currentTime: 1,
      });
    } else if (scrollY < pageHeight / 2 && scrollY > pageHeight / 4) {
      anime({
          targets: video,
          currentTime: 2,
      });
    } else if (scrollY > pageHeight / 2 && scrollY < 3 * pageHeight / 4) {
      anime({
          targets: video,
          currentTime: 3,
      });
    } else {
      anime({
          targets: video,
          currentTime: 4,
      });
    }
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
  <video class="min-h-screen h-screen" bind:this={video} src="/test.mp4" type="video/mp4"></video>
    <!-- <source bind:this={video} src="/test.mp4" type="video/mp4" controls> -->
  <!-- </video> -->
  
</header>

<header class="fixed top-0 left-0 right-0 z-50 bg-black shadow-md">

</header>


<div class="hero bg-red-400 min-h-screen">
    <div class="hero-content text-center">
      <div class="max-w-md">
        <h1 class="text-5xl font-bold" bind:this={text}>The Straight</h1>
      </div>
    </div>
</div>

<div class="hero bg-red-400 min-h-screen">
    <div class="hero-content text-center">
      <div class="max-w-md">
        <h1 class="text-5xl font-bold">Transition</h1>
      </div>
    </div>
</div>

<div class="hero bg-red-400 min-h-screen">
    <div class="hero-content text-center">
      <div class="max-w-md">
        <h1 class="text-5xl font-bold">The Curve</h1>
      </div>
    </div>
</div>

<div class="hero bg-red-400 min-h-screen">
    <div class="hero-content text-center">
      <div class="max-w-md">
        <h1 class="text-5xl font-bold">Take-off</h1>
      </div>
    </div>
</div>

<div class="hero bg-red-400 min-h-screen">
    <div class="hero-content text-center">
      <div class="max-w-md">
        <h1 class="text-5xl font-bold">The Arch</h1>
      </div>
    </div>
</div>