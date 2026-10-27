<script lang="ts">
	import IconPlaypass from './IconPlaypass.svelte';

	interface Game {
		title: string;
		description: string;
		emoji: string;
		category: string;
	}

	const rotates = ['rotate-6', '-rotate-6', 'rotate-3'];

	const games: Game[] = [
		{
			title: 'Fruit Ninja',
			description: 'Slice your way to the top while avoiding bombs.',
			emoji: '🍉',
			category: 'Get Moving'
		},
		{
			title: 'Whack-a-Mole Deluxe',
			description: 'Swing and strike — but watch out for the bombs!',
			emoji: '🔨',
			category: 'Get Moving'
		},
		{
			title: 'Starri',
			description: 'Move to the music you love with no controllers.',
			emoji: '🎵',
			category: 'Get Moving'
		},
		{
			title: 'Zumba Fitness Party',
			description: 'Turn your workouts into a dance party.',
			emoji: '💃',
			category: 'Get Moving'
		},
		{
			title: 'Family Fitness Challenge',
			description: 'Jump, hit, kick, and dodge to reach your goals.',
			emoji: '💪',
			category: 'Get Moving'
		},

		{
			title: 'Go Keeper',
			description: 'Dive, catch, and save in this soccer goalkeeping challenge.',
			emoji: '🥅',
			category: 'Sports & Action'
		},
		{
			title: 'NFL FLAG',
			description: 'Get your competitive edge with active football plays.',
			emoji: '🏈',
			category: 'Sports & Action'
		},
		{
			title: 'NBA Versus',
			description: 'Rise from park rookie to playground icon.',
			emoji: '🏀',
			category: 'Sports & Action'
		},
		{
			title: 'Sword Slash Adventure',
			description: 'Whimsical action with monster fights and boss battles.',
			emoji: '⚔️',
			category: 'Sports & Action'
		},
		{
			title: 'PAC-MAN',
			description: 'The classic, reimagined for full-body movement.',
			emoji: '🟡',
			category: 'Sports & Action'
		},

		{
			title: 'Party Fowl',
			description: 'Flap and dodge in this fast-paced chicken chaos.',
			emoji: '🐔',
			category: 'Characters & Party'
		},
		{
			title: 'Mirrorama',
			description: 'The silly mirror that gets everyone laughing.',
			emoji: '🪞',
			category: 'Characters & Party'
		},
		{
			title: 'Bluey: Bust-a-Move',
			description: 'Active adventures with the whole family.',
			emoji: '🐾',
			category: 'Characters & Party'
		},
		{
			title: 'Cookie Monster\u2019s Cookie Factory',
			description: 'Team up and solve sweet puzzles with Sesame Street.',
			emoji: '🍪',
			category: 'Characters & Party'
		},
		{
			title: 'Elmo Says',
			description: 'Listen, follow, and move with your favourite red monster.',
			emoji: '🔴',
			category: 'Characters & Party'
		}
	];

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
				class=" px-5 py-3 font-display text-lg text-checkpoint uppercase {i === activeIndex
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
