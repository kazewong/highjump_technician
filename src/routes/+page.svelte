

<script>
    import anime from 'animejs';

    let scrollY = $state(0);
    let old_scrollY = $state(0);
    let trigger = $state(false);

    let video;
    let seekTime = $state(0.0);

    let text = 'The Straight';

    $effect(() => {
        if (scrollY < 100) {
        anime({
            targets: text,
            opacity: [0, 1],
            duration: 1000,
            easing: 'easeInOutQuad',
        });
    };
    });

    function seekToTime() {
      if (video){
        video.currentTime = seekTime;
      }
    }

    function updateSeekTime(event) {
      seekTime = parseFloat(event.target.value);
    }
</script>

<svelte:window on:scroll={() => {
    scrollY = window.scrollY;
    if (scrollY > old_scrollY) {
        trigger = true;
    } else {
        trigger = false;
    }
    old_scrollY = scrollY;
    }
} />

<header class="fixed flex items-center justify-center h-screen mb-12 overflow-hidden">
  <input type="range" min="0" max="5" bind:value={seekTime} on:input={updateSeekTime} step=0.5/>
  <button on:click={seekToTime}>Seek to {seekTime} seconds</button>

  <video class="min-h-screen h-screen" bind:this={video} src="/test.mp4" type="video/mp4"></video>
    <!-- <source bind:this={video} src="/test.mp4" type="video/mp4" controls> -->
  <!-- </video> -->
  
</header>

<!-- <header class="fixed top-0 left-0 right-0 z-50 bg-black shadow-md">
    <div class="container mx-auto px-4">
        <div class="py-4">
            <p class="text-center text-lg">Scroll Y: {scrollY}</p>
            <p class="text-center text-lg">Old Scroll Y: {old_scrollY}</p>
            <p class="text-center text-lg">Trigger: {trigger}</p>

        </div>
    </div>
</header> -->


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