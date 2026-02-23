<script lang="ts">
	import '../app.css';
	let { children } = $props();
</script>

<div class="min-h-screen bg-[--color-uniswap-dark] text-[--color-uniswap-text]">
	{@render children()}
</div>
