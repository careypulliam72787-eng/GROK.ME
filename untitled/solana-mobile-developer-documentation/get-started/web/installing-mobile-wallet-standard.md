# Installing Mobile Wallet Standard

Use the **Mobile Wallet Standard** library to register Mobile Wallet Adapter as a wallet option into your web application.

## Installation

{% stepper %}
{% step %}
### Install the package

You can add Mobile Wallet Adapter to your web application by installing:

```bash
npm install @solana-mobile/wallet-standard-mobile
```
{% endstep %}

{% step %}
### Register the wallet

In the root of your web application, invoke the `registerMwa` function.

{% hint style="warning" %}
`registerMwa` must run in the browser, not during server-side rendering. If you’re using a framework with Server Side Rendering (e.g. Next.js), ensure it is invoked in a non-SSR context - for example, inside a `'use client'` component.
{% endhint %}

```javascript
// 'use client' - If using Next.js, ensure it is registered in a non-SSR context.

import {
  createDefaultAuthorizationCache,
  createDefaultChainSelector,
  createDefaultWalletNotFoundHandler,
  registerMwa,
} from "@solana-mobile/wallet-standard-mobile";

registerMwa({
  appIdentity: {
    name: "My app",
    uri: "https://myapp.io",
    icon: "relative/path/to/icon.png", // resolves to https://myapp.io/relative/path/to/icon.png
  },
  authorizationCache: createDefaultAuthorizationCache(),
  chains: ["solana:devnet", "solana:mainnet"],
  chainSelector: createDefaultChainSelector(),
  onWalletNotFound: createDefaultWalletNotFoundHandler(),
});
```

Once registered, MWA will appear as a wallet option for users browsing on Android Chrome. The connection is handled locally via Android Intents (same as native Android apps).
{% endstep %}
{% endstepper %}
