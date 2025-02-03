<script lang="ts">
  import { onMount } from 'svelte';
  import { goto } from '$app/navigation';
  import Logo from './Logo.svelte';

  let ready = false;

  onMount(() => {
    // Show animation for 2.5 seconds then redirect
    setTimeout(() => {
      ready = true;
      setTimeout(() => {
        goto('/');  // Redirect to main page
      }, 500); // Wait for fade out animation
    }, 2500);
  });
</script>

<div class="splash-container" class:fade-out={ready}>
  <Logo />
  <p class="loading-text">Loading...</p>
</div>

<style lang="postcss">
  .splash-container {
    @apply fixed inset-0 flex flex-col items-center justify-center bg-background;
    opacity: 1;
    transition: opacity 0.5s ease-in-out;
  }

  .fade-out {
    opacity: 0;
  }

  .loading-text {
    @apply mt-4 text-lg font-medium text-foreground/80;
    animation: pulse 2s cubic-bezier(0.4, 0, 0.6, 1) infinite;
  }

  @keyframes pulse {
    0%, 100% {
      opacity: 1;
    }
    50% {
      opacity: 0.5;
    }
  }
</style> 