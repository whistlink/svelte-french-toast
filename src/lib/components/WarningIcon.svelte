<script lang="ts">
	import type { IconTheme } from '../core/types';

	interface Props {
		primary?: IconTheme['primary'];
		secondary?: IconTheme['secondary'];
	}

	let { primary = '#f59e0b', secondary = '#fef3c7' }: Props = $props();
</script>

<div class="warning-icon" style:--primary={primary} style:--secondary={secondary}>
	<div class="mark"></div>
	<div class="dot"></div>
</div>

<style>
	.warning-icon {
		position: relative;
		width: 20px;
		height: 20px;
	}

	/* Triangle */
	.warning-icon::before {
		content: '';
		position: absolute;
		left: 0;
		right: 0;
		top: 0;
		bottom: 0;
		margin: auto;
		width: 0;
		height: 0;
		border-left: 10px solid transparent;
		border-right: 10px solid transparent;
		border-bottom: 18px solid var(--primary, #f59e0b);
	}

	.mark {
		position: absolute;
		left: 50%;
		top: 4px;
		width: 2px;
		height: 8px;
		background: var(--secondary, #fff);
		transform: translateX(-50%);
		border-radius: 1px;
	}

	.dot {
		position: absolute;
		left: 50%;
		bottom: 3px;
		width: 2px;
		height: 2px;
		background: var(--secondary, #fff);
		transform: translateX(-50%);
		border-radius: 50%;
	}
</style>
