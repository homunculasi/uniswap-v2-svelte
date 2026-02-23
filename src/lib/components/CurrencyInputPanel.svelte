<script lang="ts">
  let { 
    id = '', 
    value = $bindable(''), 
    currency = null as { symbol: string, logoURI: string } | null, 
    onSelect = () => {},
    balance = '0.00',
    label = 'Input'
  } = $props();

</script>

<div class="rounded-[1.25rem] bg-uni-input p-4 border border-uni-input hover:border-uni-border transition-colors">
  <div class="flex justify-between mb-2">
    <span class="text-uni-text-secondary text-sm font-medium">{label}</span>
    <span class="text-uni-text-secondary text-sm font-medium">Balance: {balance}</span>
  </div>
  
  <div class="flex justify-between items-center">
    <input 
      {id}
      type="number" 
      class="bg-transparent text-uni-text text-3xl font-medium w-full outline-none placeholder-uni-text-tertiary"
      placeholder="0.0"
      bind:value
    />
    
    <button 
      onclick={onSelect}
      aria-label="Select token"
      class="flex items-center gap-2 bg-uni-card rounded-[1rem] py-1 px-2 text-uni-text font-medium text-lg shadow-uni hover:bg-uni-border transition-colors"
    >
      {#if currency}
        <img src={currency.logoURI} alt={currency.symbol} class="w-6 h-6 rounded-full" />
        {currency.symbol}
      {:else}
        Select a token
      {/if}
      <svg width="12" height="7" viewBox="0 0 12 7" fill="none" class="ml-1">
        <path d="M0.97168 1L6.20532 6L11.439 1" stroke="#AEB1B8" stroke-width="1.5"/>
      </svg>
    </button>
  </div>
</div>
