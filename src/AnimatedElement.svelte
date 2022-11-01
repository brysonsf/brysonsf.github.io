<script lang="ts">
  import { fade } from 'svelte/transition';
  import { inview } from 'svelte-inview';
	import Skills from './Skills.svelte';
	
  let isInView;
</script>

<div
  class="wrapper"
  use:inview={{ unobserveOnEnter: true, rootMargin: '-20%' }}
  on:change={({ detail }) => {
    isInView = detail.inView;
  }}
>
  {#if isInView}
    <Skills />
  {/if}
</div>

<style>
  .wrapper {
    margin-top: 30px;
  }
</style>