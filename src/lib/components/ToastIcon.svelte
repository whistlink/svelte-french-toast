<script lang="ts">
	import type { Toast } from '../core/types';
	import CheckmarkIcon from './CheckmarkIcon.svelte';
	import ErrorIcon from './ErrorIcon.svelte';
	import LoaderIcon from './LoaderIcon.svelte';
	import WarningIcon from './WarningIcon.svelte';

	interface Props {
		toast: Toast;
	}

	let { toast }: Props = $props();
	let { type, icon, iconTheme } = $derived(toast);
</script>

{#if typeof icon === 'string'}
	<div class="_sft-animated">{icon}</div>
{:else if typeof icon !== 'undefined'}
	{@const IconComponent = icon}
	<IconComponent />
{:else if type !== 'blank'}
	<div class="_sft-indicator">
		{#if type === 'loading'}
			<LoaderIcon {...iconTheme} />
		{:else}
			<div class="_sft-status">
				{#if type === 'error'}
					<ErrorIcon {...iconTheme} />
				{:else if type === 'warning'}
					<WarningIcon {...iconTheme} />
				{:else}
					<CheckmarkIcon {...iconTheme} />
				{/if}
			</div>
		{/if}
	</div>
{/if}

<style>
	._sft-indicator {
		position: relative;
		display: flex;
		justify-content: center;
		align-items: center;
		min-width: 20px;
		min-height: 20px;
	}

	._sft-status {
		position: absolute;
		top: 50%;
		left: 50%;
		transform: translate(-50%, -50%);
	}

	._sft-animated {
		position: relative;
		transform: scale(0.6);
		opacity: 0.4;
		min-width: 20px;
		animation: enter 0.3s 0.12s cubic-bezier(0.175, 0.885, 0.32, 1.275) forwards;
	}

	@keyframes enter {
		from {
			transform: scale(0.6);
			opacity: 0.4;
		}
		to {
			transform: scale(1);
			opacity: 1;
		}
	}
</style>
