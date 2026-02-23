<script lang="ts">
  import CurrencyInputPanel from '$lib/components/CurrencyInputPanel.svelte';

  let amountIn = $state('');
  let amountOut = $state('');
  
  let tokenA = $state({
    symbol: 'ETH',
    logoURI: 'https://raw.githubusercontent.com/trustwallet/assets/master/blockchains/ethereum/info/logo.png',
  });
  
  let tokenB = $state({
    symbol: 'DAI',
    logoURI: 'https://raw.githubusercontent.com/trustwallet/assets/master/blockchains/ethereum/assets/0x6B175474E89094C44Da98b954EedeAC495271d0F/logo.png',
  });

  function handleSwapSwitch() {
    let tempAmount = amountIn;
    amountIn = amountOut;
    amountOut = tempAmount;

    let tempToken = tokenA;
    tokenA = tokenB;
    tokenB = tempToken;
  }
</script>

<div class="flex items-center justify-center w-full px-4 mt-16 md:mt-24">
  <div class="bg-uni-card w-full max-w-[480px] rounded-[1.5rem] p-2 shadow-uni border border-uni-border relative">
    
    <div class="flex justify-between items-center px-4 py-3 text-uni-text mb-2">
      <h2 class="text-base font-medium">Swap</h2>
      <button aria-label="Settings" class="hover:bg-uni-input p-2 rounded-xl transition-colors">
        <svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
          <path fill-rule="evenodd" clip-rule="evenodd" d="M13.2359 2.5C13.2359 1.67157 12.5643 1 11.7359 1H11.2359C10.4075 1 9.7359 1.67157 9.7359 2.5V3.36446C9.13076 3.52627 8.56385 3.76672 8.04631 4.07223L7.43501 3.46093C6.84922 2.87515 5.89947 2.87515 5.31369 3.46093L4.96013 3.81448C4.37435 4.40027 4.37435 5.35002 4.96013 5.9358L5.57143 6.54711C5.26591 7.06465 5.02546 7.63156 4.86366 8.23672H4C3.17157 8.23672 2.5 8.90829 2.5 9.73672V10.2367C2.5 11.0651 3.17157 11.7367 4 11.7367H4.86366C5.02546 12.3419 5.26591 12.9088 5.57143 13.4263L4.96013 14.0376C4.37435 14.6234 4.37435 15.5732 4.96013 16.159L5.31369 16.5125C5.89947 17.0983 6.84922 17.0983 7.43501 16.5125L8.04631 15.9012C8.56385 16.2067 9.13076 16.4472 9.7359 16.609V17.5C9.7359 18.3284 10.4075 19 11.2359 19H11.7359C12.5643 19 13.2359 18.3284 13.2359 17.5V16.609C13.841 16.4472 14.4079 16.2067 14.9255 15.9012L15.5368 16.5125C16.1226 17.0983 17.0723 17.0983 17.6581 16.5125L18.0117 16.159C18.5974 15.5732 18.5974 14.6234 18.0117 14.0376L17.4004 13.4263C17.7059 12.9088 17.9463 12.3419 18.1081 11.7367H18.9718C19.8002 11.7367 20.4718 11.0651 20.4718 10.2367V9.73672C20.4718 8.90829 19.8002 8.23672 18.9718 8.23672H18.1081C17.9463 7.63156 17.7059 7.06465 17.4004 6.54711L18.0117 5.9358C18.5974 5.35002 18.5974 4.40027 18.0117 3.81448L17.6581 3.46093C17.0723 2.87515 16.1226 2.87515 15.5368 3.46093L14.9255 4.07223C14.4079 3.76672 13.841 3.52627 13.2359 3.36446V2.5ZM11.4859 12.4867C12.8666 12.4867 13.9859 11.3674 13.9859 9.98672C13.9859 8.60601 12.8666 7.48672 11.4859 7.48672C10.1052 7.48672 8.9859 8.60601 8.9859 9.98672C8.9859 11.3674 10.1052 12.4867 11.4859 12.4867Z" fill="currentColor"/>
        </svg>
      </button>
    </div>

    <div class="flex flex-col gap-1 relative">
      <CurrencyInputPanel 
        id="amountIn"
        bind:value={amountIn}
        currency={tokenA}
        label="You pay"
        balance="1.50"
      />

      <div class="absolute top-[50%] left-[50%] transform -translate-x-[50%] -translate-y-[50%] z-10 border-4 border-uni-card rounded-xl">
        <button 
          aria-label="Switch tokens"
          class="bg-uni-input hover:bg-uni-border p-2 rounded-xl transition-colors text-uni-text-secondary hover:text-uni-text"
          onclick={handleSwapSwitch}
        >
          <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
            <line x1="12" y1="5" x2="12" y2="19"></line>
            <polyline points="19 12 12 19 5 12"></polyline>
          </svg>
        </button>
      </div>

      <CurrencyInputPanel 
        id="amountOut"
        bind:value={amountOut}
        currency={tokenB}
        label="You receive"
        balance="1500.00"
      />
    </div>

    <button class="w-full mt-2 bg-uni-pink hover:bg-uni-pink-hover text-white py-4 rounded-xl text-lg font-semibold transition-colors disabled:opacity-50">
      {#if !amountIn || Number(amountIn) <= 0}
        Enter an amount
      {:else}
        Swap
      {/if}
    </button>
  </div>
</div>
