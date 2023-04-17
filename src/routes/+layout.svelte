<script>
    import { onMount } from 'svelte';
    import { connected, provider, chainId, chainData, signer, signerAddress, contracts } from 'svelte-ethers-store'
    import { defaultEvmStores } from 'svelte-ethers-store'
    import { etherscan } from 'etherscan-api'

    import ConnectWallet from "./connectWallet.svelte";

    import '@picocss/pico'

    const connectWallet = () => { 
      defaultEvmStores.setProvider()
    }

    const apiKey = 'ICMMJ7TE43MSCPR69KXYSNX1GIIRRF912Q'
    
 
    // const etherscanBaseUrl = 'https://api.etherscan.io/api';
    // const etherscanApiVersion = 'v1';

    //     let getNFTsByAddress = async ($signerAddress) =>{
    //         try {
    //             const response = await fetch(`${etherscanBaseUrl}/${etherscanApiVersion}?module=account&action=tokennfttx&address=${$signerAddress}&startblock=0&endblock=999999999&sort=asc&apikey=${apiKey}`);
    //             const data = await response.json();
    //             if (data.status === '1' && data.message === 'OK') {
    //             return data.result;
    //             } else {
    //             throw new Error(`Failed to fetch NFTs: ${data.message}`);
    //             }
    //         } catch (error) {
    //             console.error(`Error fetching NFTs: ${error.message}`);
    //             throw error;
    //         }
    //     }
onMount(
    () => {
      // add a test to return in SSR context
      defaultEvmStores.setProvider()
      etherscan.account.tokennfttx($signerAddress, apiKey)
    .then(result => {
      // Handle the result
      console.log('NFTs:', result);
    })
    .catch(error => {
      // Handle errors
      console.error('Error fetching NFTs:', error);
    }).then(nfts => {
    console.log('NFTs:', nfts);
  })
  .catch(error => {
    console.error(error);
  });
    }
  )
</script>



<main class='container-fluid'>
  <nav>
    <ul>
      <h3>View your NFTs</h3>
    </ul>
    <ul>
      <li><a href="/">Home</a></li>
      <li><button>{$chainData.shortName}</button></li>
      <li><ConnectWallet {connectWallet} />
      </li>
    </ul>
  </nav>

</main>

  <slot />