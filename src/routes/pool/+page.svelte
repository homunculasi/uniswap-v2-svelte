<script lang="ts">
  let hasLiquidity = $state(false);
</script>

<div class="flex flex-col items-center justify-center w-full px-4 mt-16 md:mt-24">
  <div class="bg-uni-card w-full max-w-[480px] rounded-[1.5rem] p-6 shadow-uni border border-uni-border relative text-uni-text">
    
    <div class="flex justify-between items-center mb-6">
      <h2 class="text-xl font-medium">Pools</h2>
      <a 
        href="/pool/add" 
        class="bg-uni-pink hover:bg-uni-pink-hover text-white px-4 py-2 rounded-xl font-medium text-sm transition-colors"
      >
        + New Position
      </a>
    </div>

    <div class="bg-uni-input rounded-[1.25rem] p-6 text-center border border-uni-border flex flex-col items-center justify-center min-h-[200px]">
      {#if hasLiquidity}
        <div class="text-uni-text-secondary">Your liquidity positions will appear here.</div>
      {:else}
        <svg width="48" height="48" viewBox="0 0 24 24" fill="none" class="mb-4 text-uni-text-secondary opacity-50">
          <path d="M12 22C17.5228 22 22 17.5228 22 12C22 6.47715 17.5228 2 12 2C6.47715 2 2 6.47715 2 12C2 17.5228 6.47715 22 12 22Z" stroke="currentColor" stroke-width="2"/>
          <path d="M12 8V16M8 12H16" stroke="currentColor" stroke-width="2" stroke-linecap="round"/>
        </svg>
        <p class="text-uni-text-secondary font-medium mb-2">Your active V2 liquidity positions will appear here.</p>
        <button class="text-uni-pink hover:underline font-medium text-sm" onclick={() => hasLiquidity = !hasLiquidity}>
          Connect a wallet to view your liquidity.
        </button>
      {/if}
    </div>

  </div>
</div>
