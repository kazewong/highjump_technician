

<script>
    import { onMount } from 'svelte';
    import anime from 'animejs';

    let myDiv;

    onMount(() => {
        anime.timeline({loop: true}).add({
            targets: myDiv,
            translateX: 250,
            rotate: '1turn',
            backgroundColor: '#FF0000',
            duration: 800,
            easing: 'easeInOutQuad'
        });
    });
</script>

<div bind:this={myDiv} style="width: 100px; height: 100px; background-color: #0000FF;"></div>

<div class="hero bg-red-400 min-h-screen">
    <div class="hero-content text-center">
      <div class="max-w-md">
        <h1 class="text-5xl font-bold">The Straight</h1>
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