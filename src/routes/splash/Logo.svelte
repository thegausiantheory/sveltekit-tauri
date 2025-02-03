<script lang="ts">
	import { onMount } from 'svelte';
	import { spring } from 'svelte/motion';

	let mounted = false;

	const scale = spring(0.3, {
		stiffness: 0.1,
		damping: 0.4,
	});

	onMount(() => {
		mounted = true;
		scale.set(1);
	});
</script>

<div class="logo-container" style="transform: scale({$scale})">
	<svg
		class="logo"
		width="128"
		height="128"
		viewBox="0 0 128 128"
		fill="none"
		xmlns="http://www.w3.org/2000/svg"
	>
		<!-- You can replace this with your actual logo -->
		<circle class="circle" cx="64" cy="64" r="32" stroke="currentColor" stroke-width="8" />
		<path
			class="arrow"
			d="M64 40v48M48 72l16 16 16-16"
			stroke="currentColor"
			stroke-width="8"
			stroke-linecap="round"
			stroke-linejoin="round"
		/>
	</svg>
</div>

<style lang="postcss">
	.logo-container {
		@apply relative;
	}

	.logo {
		@apply text-primary;
	}

	.circle {
		animation: rotate 2s linear infinite;
		transform-origin: center;
	}

	.arrow {
		animation: bounce 2s ease-in-out infinite;
		transform-origin: center;
	}

	@keyframes rotate {
		from {
			transform: rotate(0deg);
		}
		to {
			transform: rotate(360deg);
		}
	}

	@keyframes bounce {
		0%,
		100% {
			transform: translateY(0);
		}
		50% {
			transform: translateY(-4px);
		}
	}
</style>
