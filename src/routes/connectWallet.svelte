<script>
 
      import { connected,  signerAddress } from 'svelte-ethers-store'

   

    export let connectWallet
  </script>
  

  <button on:click={connectWallet}>
  {#if !$connected}    
  Connect Wallet 
  {/if}
  {#if $connected}
    {$signerAddress.slice(0, 6)}...{$signerAddress.slice(-4)}
  {/if}
  </button>