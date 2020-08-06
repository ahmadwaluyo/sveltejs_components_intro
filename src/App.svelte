<script>
	import EmojiDisplay from './EmojiDisplay.svelte';
	import EmojiDescription from './EmojiDescription.svelte';
	import Button from './Button.svelte';
	import { fade, fly } from 'svelte/transition'

	let isLoaded = false;
	let currentEmoji = '😇';
	const emojis = ['😍', '😇', '😐', '😡', '😚'];
	let a = { x:0, y:0 }

	function randomEmoji () {
		return emojis[Math.floor(Math.random() * emojis.length)];
	}

	function handleRandomButton () {
		currentEmoji = randomEmoji()
	}

	function handleMouseMove (event) {
		a.x = event.clientX;
		a.y = event.clientY;
	}

	setTimeout(() => {
		isLoaded = true;
	}, 3000);
</script>

<style>
	div {
		margin: 2em;
	}
</style>

<svelte:head>
	<link rel="stylesheet" href="/terminal.min.css">
</svelte:head>
<div class="container" on:mousemove={handleMouseMove}>
	<p>
		The mouse position: {a.x} x {a.y}
	</p>
	<h1>Randomize Emoji</h1>
	{ #if isLoaded === true }
	<div in:fly={{ y: 200, duration: 2000 }} out:fade>
		<EmojiDisplay {currentEmoji} />
		<EmojiDescription />
	</div>
	{:else}
	<h2>Loading...</h2>
	{/if}
	<Button on:click={handleRandomButton} title={'Randomize'}/>
	<Button title={'Toggle'} on:click={() => isLoaded = !isLoaded} />
</div>