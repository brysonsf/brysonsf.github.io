<!-- Parallax adapted from: https://www.npmjs.com/package/svelte-parallax -->

<script>
	import { Parallax, ParallaxLayer } from 'svelte-parallax';
	import AnimatedElement from './AnimatedElement.svelte';
	let parallax;
	let fancy = 'Front-End Developer'.split('');	
	let fancy2 = 'Full-Stack Skills'.split('');
	
	const [red, green, blue] = [57, 250, 175];
  let backgroundColor = `rgb(${red}, ${green}, ${blue})`;
  const handleProgress = (progress) => {
    const p = 1 + progress;
    backgroundColor = `rgb(${red * p}, ${green * p}, ${blue * p})`;
		// console.log("R:" + red*p + "G:" +  green*p +"B:" +  blue*p);
		// ends on 114 500 350
  };
	
</script>
<main>
	<Parallax sections={4} bind:this={parallax} style="background-color: {backgroundColor}" onProgress={handleProgress}>
		<!--section 1, offset 0-->
		<ParallaxLayer 
			rate=1 span=1
			style="display: flex; flex-direction: column;">
				<div class="hero" style="">
					<h1>User-Centered Web Development</h1>
					<h2><strong>Developing & Designing for People First</strong></h2>
					<p>Simple pleasures in simple packages.</p>
				</div>
		</ParallaxLayer>
		
		<!--section 2, offset 1-->
		{#each fancy as char, index (index)}
			<ParallaxLayer
				rate={(index + 1) / (fancy.length - 1)}
				offset={1} span=1
				style="margin-left: {1+(index * 5)}%; margin-bottom: {1+(index * 5)}%; display: flex; justify-content: flex-start; align-items: center;">		 
				<p class="fancy">
					{char}
				</p>
			</ParallaxLayer>
		{/each}
		{#each fancy2 as char, index (index)}
				<ParallaxLayer
					rate={(index + 1) / (fancy.length - 1)}
					offset={1} span=1
					style="margin-left: {1 + (index * 5)}%; margin-top: {15 + (index * 5)}%; margin-bottom: {1 + (index * 5)}%; display: flex; justify-content: flex-start; align-items: center;">
					<p class="fancy">
						{char}
					</p>
				</ParallaxLayer>
			{/each}
		<!--section 2 moving pieces-->
		<ParallaxLayer offset={1} rate={-2.5} style="display: flex; justify-content: flex-end;">
			<div style="background-color: black; opacity: 0.5; width: 50%; height: 100%;"/>
		</ParallaxLayer>
		
		<ParallaxLayer offset={1} rate={2.5} style="display: flex; justify-content: flex-start;">
			<div style="background-color: white; opacity: 0.5; width: 50%; height: 100%;"/>
		</ParallaxLayer>

		<ParallaxLayer offset={1} rate={0.5} style="display: flex; justify-content: flex-end;">
			<div style="background-color: light green; opacity: 0.5; width: 50%; height: 100%;"/>
			<h1>
				 Code Skills + Knowledge
			</h1>
		</ParallaxLayer>
		
		<ParallaxLayer 
			offset=2 
			rate=2 span=1
			style="background-color: beige; display: flex; justify-content: center; align-items: center;">
					<AnimatedElement />
		</ParallaxLayer>
	</Parallax>
</main>
<style>
	:global(body) {
		padding: 0;
    background-color: #0bdb8c;
    color: #313131;
    font-family: monospace;
  }
	
  h1 {
    font-size: 3rem;
  }
	
	.fancy {
		font-size: 2.5rem;
	}
	:root {
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen,
      Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
  }

  main {
    text-align: center;
    margin: 0 auto;
  }

  p {
    margin-top: 0;
  }

  .hero {
    height: calc(100vh - 16px);
    display: flex;
    flex-direction: column;
    align-items: center;
  }

</style>