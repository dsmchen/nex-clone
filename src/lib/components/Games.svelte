<script lang="ts">
	import IconPlaypass from './IconPlaypass.svelte';
	import { games } from '#lib/data/games.ts';

	const rotates = ['rotate-6', '-rotate-6', 'rotate-3'];

	const categories = $derived([...new Set(games.map((g) => g.category))]);
	const activeGames = $derived(games.filter((g) => g.category === categories[activeIndex]));

	let activeIndex = $state(0);

	function selectCategory(i: number) {
		activeIndex = i;
	}
</script>

<section
	id="games"
	class="flex flex-col items-center overflow-hidden bg-checkpoint py-40 text-center"
>
	<h2 class="font-display text-8xl/20 text-bone uppercase">Endless<br />New Ways<br />To Play.</h2>
	<div class="mt-5 w-56">
		<IconPlaypass />
	</div>
	<p class="mt-2.5 text-bone">Unlocks 60+ games</p>
	<div class="rows my-4" aria-hidden="true">
		{#each rotates as rotate, i (i)}
			<div class={`row flex ${rotate}`}>
				{#each games as game, i (i)}
					<div
						class={`card text-9xl z-${i} -mr-10 rounded-4xl border-8 border-checkpoint bg-bone p-4`}
					>
						{game.emoji}
					</div>
				{/each}
			</div>
		{/each}
	</div>
	<div class="mt-40 flex gap-3">
		{#each categories as cat, i (i)}
			<button
				class="px-5 py-3 font-display text-lg text-checkpoint uppercase {i === activeIndex
					? 'bg-heart'
					: 'cursor-pointer bg-bone'}"
				onclick={() => selectCategory(i)}>{cat}</button
			>
		{/each}
	</div>
	<div class="grid grid-cols-3 gap-3 p-6">
		{#each activeGames as game, i (i)}
			<article class="w-sm rounded-2xl bg-bone p-6 text-checkpoint">
				<span aria-hidden="true">{game.emoji}</span>
				<h3 class="font-display text-lg uppercase">{game.title}</h3>
				<p>{game.description}</p>
			</article>
		{/each}
	</div>
</section>
