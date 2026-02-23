<script lang="ts">
  import CurrencyInputPanel from '$lib/components/CurrencyInputPanel.svelte';

  let amountA = $state('');
  let amountB = $state('');

  let tokenA = $state({
    symbol: 'ETH',
    logoURI: 'https://raw.githubusercontent.com/trustwallet/assets/master/blockchains/ethereum/info/logo.png',
  });
  
  let tokenB = $state({
    symbol: 'USDC',
    logoURI: 'https://raw.githubusercontent.com/trustwallet/assets/master/blockchains/ethereum/assets/0xA0b86991c6218b36c1d19D4a2e9Eb0cE3606eB48/logo.png',
  });
</script>

<div class="flex items-center justify-center w-full px-4 mt-16 md:mt-24">
  <div class="bg-uni-card w-full max-w-[480px] rounded-[1.5rem] p-2 shadow-uni border border-uni-border relative text-uni-text">
    
    <!-- Header with Back Button -->
    <div class="flex items-center px-4 py-3 text-uni-text mb-2">
      <a href="/pool" aria-label="Go back" class="hover:text-uni-pink transition-colors p-2 -ml-2 rounded-xl">
        <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
          <line x1="19" y1="12" x2="5" y2="12"></line>
          <polyline points="12 19 5 12 12 5"></polyline>
        </svg>
      </a>
      <h2 class="text-base font-medium mx-auto -ml-2">Add Liquidity</h2>
      <button aria-label="Settings" class="hover:bg-uni-input p-2 rounded-xl transition-colors">
        <svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
          <circle cx="12" cy="12" r="3"></circle>
          <path d="M19.4 15a1.65 1.65 0 0 0 .33 1.82l.06.06a2 2 0 0 1 0 2.83 2 2 0 0 1-2.83 0l-.06-.06a1.65 1.65 0 0 0-1.82-.33 1.65 1.65 0 0 0-1 1.51V21a2 2 0 0 1-2 2 2 2 0 0 1-2-2v-.09A1.65 1.65 0 0 0 9 19.4a1.65 1.65 0 0 0-1.82.33l-.06.06a2 2 0 0 1-2.83 0 2 2 0 0 1 0-2.83l.06-.06a1.65 1.65 0 0 0 .33-1.82 1.65 1.65 0 0 0-1.51-1H3a2 2 0 0 1-2-2 2 2 0 0 1 2-2h.09A1.65 1.65 0 0 0 4.6 9a1.65 1.65 0 0 0-.33-1.82l-.06-.06a2 2 0 0 1 0-2.83 2 2 0 0 1 2.83 0l.06.06a1.65 1.65 0 0 0 1.82.33H9a1.65 1.65 0 0 0 1-1.51V3a2 2 0 0 1 2-2 2 2 0 0 1 2 2v.09a1.65 1.65 0 0 0 1 1.51 1.65 1.65 0 0 0 1.82-.33l.06-.06a2 2 0 0 1 2.83 0 2 2 0 0 1 0 2.83l-.06.06a1.65 1.65 0 0 0-.33 1.82V9a1.65 1.65 0 0 0 1.51 1H21a2 2 0 0 1 2 2 2 2 0 0 1-2 2h-.09a1.65 1.65 0 0 0-1.51 1z"></path>
        </svg>
      </button>
    </div>

    <!-- Currency Panels -->
    <div class="flex flex-col gap-1 relative">
      <CurrencyInputPanel 
        id="amountA"
        bind:value={amountA}
        currency={tokenA}
        label="Deposit"
        balance="1.50"
      />

      <!-- Plus Icon between -->
      <div class="absolute top-[50%] left-[50%] transform -translate-x-[50%] -translate-y-[50%] z-10 p-1 bg-uni-card rounded-xl">
        <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="text-uni-text-secondary">
          <line x1="12" y1="5" x2="12" y2="19"></line>
          <line x1="5" y1="12" x2="19" y2="12"></line>
        </svg>
      </div>

      <CurrencyInputPanel 
        id="amountB"
        bind:value={amountB}
        currency={tokenB}
        label="Deposit"
        balance="1500.00"
      />
    </div>

    <button class="w-full mt-2 bg-uni-pink hover:bg-uni-pink-hover text-white py-4 rounded-xl text-lg font-semibold transition-colors disabled:opacity-50">
      {#if !amountA || !amountB}
        Enter an amount
      {:else}
        Supply
      {/if}
    </button>

  </div>
</div>
