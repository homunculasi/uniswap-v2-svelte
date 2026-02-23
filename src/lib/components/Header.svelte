<script lang="ts">
  import { page } from '$app/stores';

  let currentPath = $derived($page.url.pathname);
  
  const navItems = [
    { name: 'Swap', path: '/' },
    { name: 'Pool', path: '/pool' }
  ];
</script>

<header class="flex items-center justify-between px-4 py-4 w-full">
  <!-- Logo section -->
  <div class="flex items-center gap-2">
    <div class="text-uni-pink font-bold text-xl flex items-center gap-2">
      <!-- Simple SVG logo placeholder for Uniswap -->
      <svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path d="M12 2L2 22H22L12 2Z" fill="var(--color-uni-pink)"/>
      </svg>
      Uniswap
    </div>
  </div>

  <!-- Navigation -->
  <nav class="hidden md:flex bg-uni-card rounded-[1.25rem] p-1 border border-uni-border items-center absolute left-1/2 transform -translate-x-1/2">
    {#each navItems as item}
      <a 
        href={item.path} 
        class="px-4 py-2 rounded-xl text-base font-medium transition-colors {currentPath === item.path ? 'bg-uni-input text-uni-text' : 'text-uni-text-secondary hover:text-uni-text hover:bg-uni-input/50'}"
      >
        {item.name}
      </a>
    {/each}
  </nav>

  <!-- Right section (Network / Wallet) -->
  <div class="flex items-center gap-2">
    <button class="bg-uni-card border border-uni-border hover:border-uni-text-tertiary transition-colors text-uni-text px-3 py-2 rounded-xl text-sm font-medium flex items-center gap-2">
      <div class="w-2 h-2 rounded-full bg-green-500"></div>
      Ethereum
    </button>
    <button class="bg-uni-pink hover:bg-uni-pink-hover text-white px-4 py-2 rounded-xl font-medium text-sm transition-colors">
      Connect Wallet
    </button>
  </div>
</header>
