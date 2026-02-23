<script lang="ts">
	import '../app.css';
	import Header from '$lib/components/Header.svelte';
	let { children } = $props();
</script>

<div class="min-h-screen bg-[--color-uni-main] text-[--color-uni-text] flex flex-col items-center">
  <Header />
	{@render children()}
</div>
