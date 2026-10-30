# Quickstart

Install Seeker Connect and add a branded wallet connect flow to your app.

Connect your app directly to a Solana Mobile certified device’s own wallet. The web SDK is available today; React Native and Android are planned. Most apps use the Wallet Standard entry point, which discovers and drives Seeker Connect like any other [Wallet Standard](https://github.com/wallet-standard/wallet-standard) wallet — no Seeker-specific code in your connect flow.

## Install

{% tabs %}
{% tab title="npm" %}
```bash
npm install @solana-mobile/seeker-connect-wallet-standard @wallet-standard/app @wallet-standard/features
```
{% endtab %}

{% tab title="pnpm" %}
```bash
pnpm add @solana-mobile/seeker-connect-wallet-standard @wallet-standard/app @wallet-standard/features
```
{% endtab %}

{% tab title="bun" %}
```bash
bun add @solana-mobile/seeker-connect-wallet-standard @wallet-standard/app @wallet-standard/features
```
{% endtab %}
{% endtabs %}

The Wallet Standard package pulls in the rest of the SDK transitively. `@wallet-standard/app` and `@wallet-standard/features` are the registry helpers most Solana apps already have.

## Relay URL

Seeker Connect utilizes Mobile Wallet Adapter’s extended remote communication protocol over a Nostr relay. Any Nostr relay that supports public access and ephemeral events can be used. Solana Mobile provides a Nostr relay that satisfies these requirements and is free to use. Use of the Solana Mobile Nostr relay requires agreement to our terms.

## Quick start

{% stepper %}
{% step %}
## Register Seeker Connect

Call `registerSeekerConnect` once, early in your app’s lifecycle. It adds the wallet to the page’s Wallet Standard registry.

```javascript
import { registerSeekerConnect } from "@solana-mobile/seeker-connect-wallet-standard";

registerSeekerConnect({
  identity: { name: "My App", uri: window.location.origin, icon: "/icon.png" },
  relayDomain: "<relay-domain>",
});
```
{% endstep %}

{% step %}
## Discover the wallet

Find Seeker Connect like any other Wallet Standard wallet.

```javascript
import { getWallets } from "@wallet-standard/app";
import { SeekerConnectWalletName } from "@solana-mobile/seeker-connect-wallet-standard";

const wallet = getWallets()
  .get()
  .find((w) => w.name === SeekerConnectWalletName);
```
{% endstep %}

{% step %}
## Connect

`connect()` launches the wallet for user consent on the first connection, then returns the authorized accounts.

```javascript
import { StandardConnect } from "@wallet-standard/features";

const { accounts } = await wallet.features[StandardConnect].connect();
console.log("connected as", accounts[0]?.address);
```

“Connected” means your app holds a wallet-issued authorization token — there is no long-lived transport. Each interaction runs in its own short-lived session and silently reauthorizes with the cached token, so the user is not re-prompted for consent.
{% endstep %}
{% endstepper %}

## Dropped sessions

If a session ends before the wallet answers, the call rejects with a `SeekerConnectError` whose `code` is `session-closed`. After a sign-and-send request, that does not mean the transaction failed: the wallet may already have submitted it, and the error carries no signature to look it up by. Don’t retry automatically. Check for the transaction’s effect on chain until its blockhash expires (for a durable-nonce transaction, until the nonce advances), so a transaction that already went through is not sent again.
