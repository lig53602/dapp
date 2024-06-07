<script setup>
import { createWeb3Modal,defaultWagmiConfig } from '@web3modal/wagmi';
import { mainnet,arbitrum } from 'viem/chains';
import { reconnect } from '@wagmi/core';
const projectId='b972efbc12f56e63497939922d6b1eb1'
const metadata={
  name: 'Web3Modal',
  description: 'Web3Modal Example',
  url: 'https://web3modal.com', // origin must match your domain & subdomain
  icons: ['https://avatars.githubusercontent.com/u/37784886']
}
const chains = [mainnet, arbitrum]
const config = defaultWagmiConfig({
  chains,
  projectId,
  metadata,
  ...wagmiOptions // Optional - Override createConfig parameters
})

reconnect(config)
createWeb3Modal({
    wagmiConfig: config,
    projectId,
    enableAnalytics: true, // Optional - defaults to your Cloud configuration
    enableOnramp: true // Optional - false as default
  })
</script>

<template>
  <span class="read-the-docs">23423</span>
  <w3m-button />
</template>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>
