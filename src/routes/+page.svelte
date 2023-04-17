<script>

        import { connected, provider, chainId, chainData, signer, signerAddress, contracts } from 'svelte-ethers-store'

        

</script>

<main class="container">
    <h1>View your NFTs</h1>
    <p>Connected: {$connected}</p>
    <p>Provider: {$provider}</p>
    <p>Chain ID: {$chainId}</p>
    <p>Chain Data: {JSON.stringify($chainData)}</p>
    <p>Signer: {$signer}</p>
    <p>Signer Address: {$signerAddress}</p>
    <p>Contracts: {JSON.stringify($contracts)}</p>


</main>

