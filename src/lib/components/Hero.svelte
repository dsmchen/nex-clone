<script lang="ts">
	import { resolve } from '$app/paths';
	import IconLogo from './IconLogo.svelte';
</script>

<section class="relative flex min-h-[70vh] flex-col items-center text-center">
	<enhanced:img src="#lib/assets/screentime.webp" alt="Family sitting on couch on their devices" />
	<div class="absolute z-10 flex h-full flex-col items-center px-6">
		<div class="my-8 w-28">
			<a href={resolve('/')} aria-label="Homepage"> <IconLogo /> </a>
		</div>
		<h1 class="mt-16 max-w-xl font-display text-7xl font-bold text-checkpoint uppercase">
			What happened to family time?
		</h1>
		<p class="mt-3 text-checkpoint">Maybe it's time we changed things.</p>
		<div class="absolute bottom-24 flex">
			<a
				href="#meet"
				class="flex size-12 items-center justify-center bg-portal text-3xl text-white"
				aria-hidden="true"
				tabindex="-1"><span class="icon-[mdi--arrow-right-bold]"></span></a
			>
			<a href="#meet" class="inline-block bg-white px-5 py-3 text-portal">Learn More</a>
		</div>
	</div>
</section>
