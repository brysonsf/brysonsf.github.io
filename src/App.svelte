<script>
  import svelteLogo from './assets/svelte.svg';
  import Counter from './lib/Counter.svelte';
  import { draw } from 'svelte/transition';
	import { sineInOut } from 'svelte/easing';
  import { onMount } from "svelte";
  import HoverDrawSVG from 'svelte-hover-draw-svg';

  let condition = false;

    let icons = [

    ]
  
    // Attach media query listener on mount hook
    onMount(async () => {
      const res = await fetch(`/assets/`);
		  icons = await res.json();
    });
</script>
<header>
  <div class="nav">
    <div class="nav-links">
    <a href="/" class="link">Home</a>
    <a href="/index" class="link">index</a>
    <a href="/about" class="link">About</a>
    <a href="/projects" class="link">Projects</a>
  </div>

</div>
  
</header>
<main>
  
  <div class="card">
    <button on:click={() => condition = !condition}>
      show svg
    </button>
    
  <HoverDrawSVG --duration="2"> 
      <svg viewBox="0 0 20 5" xmlns="http://www.w3.org/2000/svg" stroke="#000" stroke-width="2">
      {#if condition}
        <path transition:draw="{{duration: 2000, delay:300, easing: sineInOut}}"
            d="M 0 0 Q 1 0 0 9 A 1 1 0 0 0 0 4 A 1 1 0 0 0 0 4 M 3 6 V 9 C 4 8 2 3 5 6 L 3 5 L 3 5 M 6 5 L 7 7 V 7 L 6 9 L 8 5 M 8 9 A 1 1 0 0 0 10 7 C 8 5 8 5 10 4 M 12 6 A 1 1 0 0 0 12 9 A 1 1 0 0 0 12 6 M 14 5 L 14 6 V 9 Q 14 3 16 9"
            fill="none"
            stroke="cornflowerblue"
            stroke-width="0.1px"
            />
     {/if}
      </svg>
  </HoverDrawSVG>
   
  </div>

    <div class="">
    <h3>Built Using Vite + Svelte</h3>
    <a href="https://vitejs.dev" target="_blank"> 
      <img src="/vite.svg" class="logo" alt="Vite Logo" />
    </a>
      <a href="https://svelte.dev" target="_blank"> 
    <img src={svelteLogo} class="logo svelte" alt="Svelte Logo" />
  </a>
  </div>


  <hr>
  
  <div class="slots">
    <slot></slot>
  </div>

  <hr>

  <div class="card">
    <Counter />
  </div>

  <p>
    Check out <a href="https://github.com/sveltejs/kit#readme" target="_blank">SvelteKit</a>, the official Svelte app framework powered by Vite!
  </p>
</main>

<style>
  path{
    stroke: green;
    fill:black;
    transition: 2s;
  }
  svg {
		display: block;
		height: 150px;
		width: 150px;
    padding: 1.5em;
	}
  .logo {
    height: 6em;
    padding: 1.5em;
    will-change: filter;
  }
  .logo:hover {
    filter: drop-shadow(0 0 2em #646cffaa);
  }
  .logo.svelte:hover {
    filter: drop-shadow(0 0 2em #ff3e00aa);
  }

  /*
  Navbar styling,
  */
  .nav {
      background-color: rgba(255, 0, 100, 0.8);
      font-family: "Helvetica Neue", "Helvetica", "Arial", sans-serif;
      height: 45px;
    }
</style>
