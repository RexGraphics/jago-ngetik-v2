<script lang="ts">
	import { faker } from '@faker-js/faker';
	import { onMount } from 'svelte';

	let words: string[] = [];

	function generateNewWords() {
		// Menghasilkan 20 kata acak dalam bahasa Inggris
		// .toLowerCase() agar standar untuk tes ketik
		const randomString = faker.word.words(20).toLowerCase();
		words = randomString.split(' ');
	}

	// Generate kata pertama kali saat halaman dibuka
	onMount(() => {
		generateNewWords();
	});
</script>

<div class="container">
	<div class="word-box">
		{#each words as word}
			<span class="word">{word}</span>
		{/each}
	</div>

	<button on:click={generateNewWords}>
		Acak Kata Lagi
	</button>
</div>

<style>
	.word-box {
		display: flex;
		flex-wrap: wrap;
		gap: 10px;
		font-size: 1.5rem;
		margin-bottom: 20px;
	}
	.word {
		color: #555;
	}
	button {
		padding: 10px 20px;
		cursor: pointer;
	}
</style>