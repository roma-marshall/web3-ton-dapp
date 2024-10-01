# Web3 TON dApp

The TON-based dApp shows the initialization of a smart contract on the TON Virtual Machine for an asset transaction to another smart contract.

## Code snippets

1. Creating `tonconnect-manifest.json` and define the config object

```json
{
  "url": "<app-url>",                        // required
  "name": "<app-name>",                      // required
  "iconUrl": "<app-icon-url>",               // required
  "termsOfUseUrl": "<terms-of-use-url>",     // optional
  "privacyPolicyUrl": "<privacy-policy-url>" // optional
}
```

2. Initialization of `TonConnectUIProvider` in `App.vue`-component

```html
<template>
    <TonConnectUIProvider :options="options">
       <!-- Your dApp -->
    </TonConnectUIProvider>
</template>
```

```javascript
import { TonConnectUIProvider } from '@townsquarelabs/ui-vue'

const options = ref({ manifestUrl: 'https://<YOUR_APP_URL>/tonconnect-manifest.json' })
```

3. Importing useTonConnectUI to access a TonConnectUI instance and send transactions
```javascript
import { useTonConnectUI } from '@townsquarelabs/ui-vue'

const [tonConnectUI, setOptions] = useTonConnectUI()
```

4. Send TON coins (in nanotons) to a specific address

```javascript
const tx = {
  validUntil: Math.floor(Date.now() / 1000) + 60, // 60 sec
  
  messages: [
    {
      address: receiver.value,
      amount: amount.value * 10**9 // 1 ton = 1.000.000.000 nanotons
    }
  ]
}

const sendTransaction = () => {
  tonConnectUI.sendTransaction(tx)
}
```

## Recommended Installation

```
git clone https://github.com/roma-marshall/web3-ton-blockchain.git
cd web3-ton-blockchain
npm run dev
```

## License

MIT License
