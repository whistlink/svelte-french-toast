<!-- Adapted from https://github.com/timolins/react-hot-toast -->
<script lang="ts">
	import type { IconTheme } from '../core/types';

	interface Props {
		primary?: IconTheme['primary'];
		secondary?: IconTheme['secondary'];
	}

	let { primary = '#ff4b4b', secondary = '#fff' }: Props = $props();
</script>

<div style:--primary={primary} style:--secondary={secondary}></div>

<style>
	div {
		width: 20px;
		height: 20px;
		border-radius: 50%;
		background: rgba(255, 75, 75);
		position: relative;
		transform: rotate(45deg);
		opacity: 0;
		backdrop-filter: blur(2px);
		-webkit-backdrop-filter: blur(2px);
		box-shadow: 0 2px 6px rgba(0, 0, 0, 0.1);
		animation: circleAnimation 0.3s cubic-bezier(0.175, 0.885, 0.32, 1.275) forwards;
		animation-delay: 100ms;
	}

	div::after,
	div::before {
		content: '';
		position: absolute;
		bottom: 9px;
		left: 4px;
		width: 12px;
		height: 2px;
		border-radius: 1px;
		opacity: 0;
		background: rgba(255, 255, 255, 0.8);
		box-shadow: 0 0 2px rgba(255, 255, 255, 0.6);
		animation: firstLineAnimation 0.15s ease-out forwards;
		animation-delay: 150ms;
	}

	div:before {
		transform: rotate(90deg);
		animation: secondLineAnimation 0.15s ease-out forwards;
		animation-delay: 180ms;
	}

	@keyframes circleAnimation {
		from {
			transform: scale(0) rotate(45deg);
			opacity: 0;
		}
		to {
			transform: scale(1) rotate(45deg);
			opacity: 1;
		}
	}

	@keyframes firstLineAnimation {
		from {
			transform: scale(0);
			opacity: 0;
		}
		to {
			transform: scale(1);
			opacity: 1;
		}
	}

	@keyframes secondLineAnimation {
		from {
			transform: scale(0) rotate(90deg);
			opacity: 0;
		}
		to {
			transform: scale(1) rotate(90deg);
			opacity: 1;
		}
	}
</style>
