<script lang="ts">
	import toast, { Toaster } from '../lib';
	import 'prismjs';
	import 'prism-svelte';
	import demoCode from '../www/demo-code';
	import Copy from '../www/Copy.svelte';
	import Examples from '../www/Examples.svelte';
	import pkg from '../../package.json';

	function launchToast() {
		toast.promise(
			new Promise((resolve, reject) => {
				setTimeout(Math.random() < 0.8 ? resolve : reject, 1000);
			}),
			{
				loading: 'Toasting bread...',
				success: 'Here’s your toast!',
				error: 'Your toast burned :('
			}
		);
	}

	const installers = [
		{ name: 'npm', cmd: 'npm install @whistlin/svelte-french-toast' },
		{ name: 'pnpm', cmd: 'pnpm install @whistlin/svelte-french-toast' },
		{ name: 'yarn', cmd: 'yarn add @whistlin/svelte-french-toast' },
		{ name: 'bun', cmd: 'bun add @whistlin/svelte-french-toast' }
	];
	let installer = $state(installers[0].name);
</script>

<Toaster />

<div class="py-24 bg-[rgba(250,246,244,0.4)] backdrop-blur-lg border-b border-white/20 ease-in-out">
	<div class="container max-w-xl flex flex-col items-center mx-auto text-center">
		<img class="h-16 mb-10" src="favicon.png" alt="" />
		<div
			class="flex flex-col md:flex-row items-center space-y-3 md:space-y-0 md:space-x-3 mb-10 text-white"
		>
			<div
				class="p-4 text-xl md:text-2xl font-extrabold bg-white/20 backdrop-blur-md text-gray-900 uppercase tracking-widest rounded-xl -rotate-2 shadow-lg border border-white/30"
			>
				Svelte
			</div>
			<div
				class="p-4 text-xl md:text-2xl font-extrabold bg-white/30 backdrop-blur-md text-gray-900 uppercase tracking-widest rounded-xl rotate-3 shadow-lg border border-white/20"
			>
				French
			</div>
			<div
				class="p-4 text-xl md:text-2xl font-extrabold bg-white/20 backdrop-blur-md text-gray-900 uppercase tracking-widest rounded-xl -rotate-2 shadow-lg border border-white/30"
			>
				Toast
			</div>
		</div>
		<h1 class="font-bold text-3xl md:text-5xl text-gray-900">
			Buttery smooth toast notifications.
		</h1>
		<p class="mt-10 text-lg md:text-xl max-w-prose text-gray-700">
			Lightweight, customizable, and beautiful by default.<br />
			Inspired by
			<a
				href="https://react-hot-toast.com"
				class="font-medium underline decoration-dotted underline-offset-4 text-gray-900"
				>React Hot Toast</a
			>.
		</p>
		<div class="flex items-center mt-10 space-x-4">
			<button
				onclick={launchToast}
				class="flex items-center space-x-2 text-lg py-2 font-bold px-5 rounded-xl bg-white/30 backdrop-blur-md text-gray-900 border border-white/20 shadow hover:bg-white/40 transition"
			>
				<svg
					xmlns="http://www.w3.org/2000/svg"
					class="h-5 w-5"
					viewBox="0 0 20 20"
					fill="currentColor"
				>
					<path
						fill-rule="evenodd"
						d="M5 2a1 1 0 011 1v1h1a1 1 0 010 2H6v1a1 1 0 01-2 0V6H3a1 1 0 010-2h1V3a1 1 0 011-1zm0 10a1 1 0 011 1v1h1a1 1 0 110 2H6v1a1 1 0 11-2 0v-1H3a1 1 0 110-2h1v-1a1 1 0 011-1zM12 2a1 1 0 01.967.744L14.146 7.2 17.5 9.134a1 1 0 010 1.732l-3.354 1.935-1.18 4.455a1 1 0 01-1.933 0L9.854 12.8 6.5 10.866a1 1 0 010-1.732l3.354-1.935 1.18-4.455A1 1 0 0112 2z"
						clip-rule="evenodd"
					/>
				</svg>
				<span>Launch toast</span>
			</button>
			<a
				href="https://github.com/whistlink/svelte-french-toast.git"
				class="flex items-center space-x-2 text-gray-500 hover:text-gray-900 transition"
			>
				<svg class="h-5 w-5" role="img" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
					<title>GitHub</title>
					<path fill="currentColor" d="M12 .297c-6.63 0-12 5.373-12 12..." />
				</svg>
				<span>Source</span>
			</a>
		</div>
		<p
			class="mt-5 text-sm border rounded-full px-2 py-1 text-gray-500 bg-white/20 backdrop-blur-md border-white/20"
		>
			<a href="https://npmjs.com/package/@whistlindev/svelte-french-toast">Version {pkg.version}</a>
		</p>
		<div class="grid grid-cols-2 md:grid-cols-3 gap-4 self-stretch mt-10 font-medium">
			{#each ['Emoji Support', 'Customizable', 'Promise API', 'Pause on hover', 'Accessible', 'Headless use'] as feature}
				<div
					class="flex space-x-2 items-center bg-white/20 backdrop-blur-md rounded-lg p-2 border border-white/20 shadow-sm"
				>
					<svg
						xmlns="http://www.w3.org/2000/svg"
						width="24"
						height="24"
						viewBox="0 0 24 24"
						fill="none"
						stroke="#55aa88"
						stroke-width="2"
						stroke-linecap="round"
						stroke-linejoin="round"
					>
						<polyline points="20 6 9 17 4 12" />
					</svg>
					<p class="text-gray-900">{feature}</p>
				</div>
			{/each}
		</div>
	</div>
</div>
<div class="container mx-auto max-w-2xl py-10">
	<section>
		<div class="flex flex-col sm:flex-row sm:items-center justify-between mb-4 gap-4">
			<p class="text-xl font-bold text-gray-900">1. Install</p>
			<div class="space-x-1">
				{#each installers as i}
					<label for={i.name} class:checked={i.name === installer} class="text-gray-800">
						<input
							type="radio"
							id={i.name}
							name="installers"
							value={i.name}
							bind:group={installer}
						/>
						{i.name}
					</label>
				{/each}
			</div>
		</div>

		{#each installers as i}
			<div class:hidden={installer !== i.name}>
				<code
					class="language-shell bg-white/20 backdrop-blur-md border border-white/20 rounded-lg p-2 block"
					>{i.cmd}</code
				>
				<Copy text={i.cmd} />
			</div>
		{/each}
	</section>
	<section class="mt-10">
		<p class="text-xl font-bold mb-4 text-gray-900">2. Mount and use</p>
		<pre
			class="language-html bg-white/20 backdrop-blur-md border border-white/20 rounded-lg p-4"><code
				>{demoCode}</code
			></pre>
		<Copy text={demoCode} />
	</section>

	<hr class="my-10 border-white/20" />
	<h1 class="text-4xl font-bold mb-5 text-gray-900">Examples</h1>
	<Examples />
	<p class="mt-24 mb-2 text-center">
		<a href="https://github.com/whistlink/svelte-french-toast.git" class="underline text-gray-900"
			>GitHub</a
		>
	</p>
	<p class="text-center text-gray-500">
		© {new Date().getFullYear()} whistlin-svelte-french-toast · Built by
		<a class="text-gray-800" href="https://whistlin.dev">whistlin</a>
	</p>
</div>

<style lang="postcss">
	:not(pre) > code,
	pre {
		@apply p-5 block;
	}

	input[type='radio'] {
		@apply appearance-none hidden;
	}
	label {
		cursor: pointer;
		@apply px-3 py-1 rounded-full;
	}
	label.checked {
		@apply bg-gray-200 font-bold;
	}
</style>
