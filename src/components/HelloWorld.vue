<script setup>
import { ref } from 'vue';
import { createWeb3Modal,defaultWagmiConfig } from '@web3modal/wagmi';
import { mainnet,arbitrum } from 'viem/chains';
import { reconnect } from '@wagmi/core';
import { useWeb3Modal } from '@web3modal/wagmi/vue'
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
  metadata

})

reconnect(config)
createWeb3Modal({
    wagmiConfig: config,
    projectId,
    enableAnalytics: true, // Optional - defaults to your Cloud configuration
    enableOnramp: true // Optional - false as default
  })

// 4. Use modal composable
const modal = useWeb3Modal()
defineProps({
  msg: String,
});

const count = ref(0);


</script>

<template>
  <h1>{{ msg }}{{ count }}22</h1>
  <button @click="modal.open()">Open Connect Modal</button>
  <button @click="modal.open({ view: 'Networks' })">Open Network Modal</button>
</template>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>
