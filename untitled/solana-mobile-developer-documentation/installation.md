# Installation

Install Wallet UI to integrate Mobile Wallet Adapter into your app.

## Prerequisites

* A React Native (Expo) project set up for Android development. See the [Environment Setup](get-started/development-setup.md) guide.
* An MWA-compatible wallet installed on your device or emulator. See [Install a development wallet](get-started/development-setup.md#install-a-development-wallet-app).

## Choose a Solana library

Wallet UI ships one package per Solana client library. Pick one and stay on the matching tab through the rest of this guide.

* [**`@wallet-ui/react-native-kit`**](https://github.com/wallet-ui/wallet-ui) — use this for new apps. Built on [`@solana/kit`](https://github.com/anza-xyz/kit).
* [**`@wallet-ui/react-native-web3js`**](https://github.com/wallet-ui/wallet-ui) — use this when your app already depends on `@solana/web3.js` v1.

Both packages expose the same `MobileWalletProvider` and `useMobileWallet` API. Only the Solana primitives they hand you differ.

## Install dependencies

{% tabs %}
{% tab title="@solana/kit" %}
{% tabs %}
{% tab title="npm" %}
```bash
npm install \
  @wallet-ui/react-native-kit \
  @solana/kit \
  @solana-program/memo \
  react-native-quick-crypto \
  react-native-nitro-modules \
  expo-dev-client
```
{% endtab %}

{% tab title="yarn" %}
```bash
yarn add \
  @wallet-ui/react-native-kit \
  @solana/kit \
  @solana-program/memo \
  react-native-quick-crypto \
  react-native-nitro-modules \
  expo-dev-client
```
{% endtab %}

{% tab title="pnpm" %}
```bash
pnpm add \
  @wallet-ui/react-native-kit \
  @solana/kit \
  @solana-program/memo \
  react-native-quick-crypto \
  react-native-nitro-modules \
  expo-dev-client
```
{% endtab %}
{% endtabs %}

`@solana-program/memo` is only needed for the transaction example in the [Quickstart](quickstart.md). Swap it for whichever `@solana-program/*` client your app actually builds instructions with.
{% endtab %}

{% tab title="@solana/web3.js" %}
{% tabs %}
{% tab title="npm" %}
```bash
npm install \
  @wallet-ui/react-native-web3js \
  @solana/web3.js \
  @solana/spl-memo \
  react-native-quick-crypto \
  react-native-nitro-modules \
  expo-dev-client
```
{% endtab %}

{% tab title="yarn" %}
```bash
yarn add \
  @wallet-ui/react-native-web3js \
  @solana/web3.js \
  @solana/spl-memo \
  react-native-quick-crypto \
  react-native-nitro-modules \
  expo-dev-client
```
{% endtab %}

{% tab title="pnpm" %}
```bash
pnpm add \
  @wallet-ui/react-native-web3js \
  @solana/web3.js \
  @solana/spl-memo \
  react-native-quick-crypto \
  react-native-nitro-modules \
  expo-dev-client
```
{% endtab %}
{% endtabs %}

`@solana/spl-memo` is only needed for the transaction example in the [Quickstart](quickstart.md). Swap it for whichever instruction builders your app actually uses.
{% endtab %}
{% endtabs %}

## Configure polyfills

Solana client libraries expect Node and browser APIs that React Native does not ship. The `react-native-quick-crypto` library provides the `crypto` polyfill they need, and it is the same for both libraries.

{% stepper %}
{% step %}
### Create a `polyfill.js` file in your project root

```javascript
import { install } from "react-native-quick-crypto";
install();
```
{% endstep %}

{% step %}
### Create an `index.js` entry point that imports the polyfill first

```javascript
import "./polyfill";
import "expo-router/entry"; // If using Expo Router
```
{% endstep %}

{% step %}
### Update `package.json` to use the new entry point

```json
{
  "main": "./index.js"
}
```
{% endstep %}
{% endstepper %}

{% hint style="warning" %}
The polyfill must be imported **before** any other code that uses a Solana client library.
{% endhint %}

## Custom Development Build

MWA uses Kotlin native modules, so you must use a [custom Expo development build](https://docs.expo.dev/develop/development-builds/create-a-build/) instead of Expo Go. Update your `package.json` build scripts:

```json
{
  "scripts": {
    "android": "expo run:android"
  }
}
```

## Next steps

## Setup

Wrap your app with MobileWalletProvider and set up the useMobileWallet hook.
