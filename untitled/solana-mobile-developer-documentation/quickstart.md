# Quickstart

Usage examples for connecting to wallets, signing messages, and sending transactions with useMobileWallet.

This page demonstrates how to use each method from the `useMobileWallet` hook. Make sure you have completed the [Installation](installation.md) and [Setup](setup.md) steps first. Stay on the tab for the Solana library you installed.

## Connect / Disconnect

Use `connect` to initiate a wallet connection and `disconnect` to end it. The `account` field holds the selected wallet account.

{% tabs %}
{% tab title="@solana/kit" %}
```tsx
import { useMobileWallet } from "@wallet-ui/react-native-kit";

function ConnectButton() {
  const { account, connect, disconnect } = useMobileWallet();

  if (account) {
    return <Button title="Disconnect" onPress={disconnect} />;
  }

  return <Button title="Connect Wallet" onPress={connect} />;
}
```
{% endtab %}

{% tab title="@solana/web3.js" %}
```tsx
import { useMobileWallet } from "@wallet-ui/react-native-web3js";

function ConnectButton() {
  const { account, connect, disconnect } = useMobileWallet();

  if (account) {
    return <Button title="Disconnect" onPress={disconnect} />;
  }

  return <Button title="Connect Wallet" onPress={connect} />;
}
```
{% endtab %}
{% endtabs %}

## Sign Message

Use `signMessages` to request the wallet to sign an arbitrary byte payload. This is useful for off-chain signature verification.

{% tabs %}
{% tab title="@solana/kit" %}
```tsx
import { useMobileWallet } from "@wallet-ui/react-native-kit";

function SignMessageButton() {
  const { signMessages } = useMobileWallet();

  const handleSignMessage = async () => {
    const messageBytes = new TextEncoder().encode("Verify this message");
    const signature = await signMessages(messageBytes);
    console.log("Signature:", signature);
  };

  return <Button title="Sign Message" onPress={handleSignMessage} />;
}
```
{% endtab %}

{% tab title="@solana/web3.js" %}
```tsx
import { useMobileWallet } from "@wallet-ui/react-native-web3js";

function SignMessageButton() {
  const { signMessages } = useMobileWallet();

  const handleSignMessage = async () => {
    const messageBytes = new TextEncoder().encode("Verify this message");
    const signature = await signMessages(messageBytes);
    console.log("Signature:", signature);
  };

  return <Button title="Sign Message" onPress={handleSignMessage} />;
}
```
{% endtab %}
{% endtabs %}

{% hint style="warning" %}
`signMessages` takes bytes, not a string. Use `TextEncoder` to encode text — a base64 helper such as `toUint8Array` will decode your text as base64 and sign the wrong payload.
{% endhint %}

## Sign In with Solana (SIWS)

Use `signIn` to connect to a wallet and verify ownership in a single step. This combines authorization and message signing into one user interaction. Read the account from the returned result — the hook’s `account` is not updated until the next render.

{% tabs %}
{% tab title="@solana/kit" %}
```tsx
import { useMobileWallet } from "@wallet-ui/react-native-kit";

function SignInButton() {
  const { account, chain, identity, signIn } = useMobileWallet();

  const handleSignIn = async () => {
    const result = await signIn({
      address: account?.address,
      chainId: chain,
      domain: "your-app-domain.com",
      statement: "Sign in to Your App",
      uri: identity.uri,
    });
    console.log("Signed in:", result.account.address);
  };

  return <Button title="Sign In" onPress={handleSignIn} />;
}
```
{% endtab %}

{% tab title="@solana/web3.js" %}
```tsx
import { useMobileWallet } from "@wallet-ui/react-native-web3js";

function SignInButton() {
  const { account, chain, identity, signIn } = useMobileWallet();

  const handleSignIn = async () => {
    const result = await signIn({
      address: account?.address.toString(),
      chainId: chain,
      domain: "your-app-domain.com",
      statement: "Sign in to Your App",
      uri: identity.uri,
    });
    console.log("Signed in:", result.account.address.toString());
  };

  return <Button title="Sign In" onPress={handleSignIn} />;
}
```
{% endtab %}
{% endtabs %}

`signIn` works whether or not the user is already connected. Omit `address` to let the wallet pick the account and sign in as part of the same prompt.

## Sign and Send Transaction

Request the wallet to sign a transaction and submit it to the Solana network. Both examples send a memo instruction — swap it for whichever instructions your app builds.

{% tabs %}
{% tab title="@solana/kit" %}
`sendTransactions` takes instructions and handles fetching the blockhash, compiling the transaction, signing, and sending.

```tsx
import { getAddMemoInstruction } from "@solana-program/memo";
import { Instruction } from "@solana/kit";
import { useMobileWallet } from "@wallet-ui/react-native-kit";

function SendTransactionButton() {
  const { sendTransactions } = useMobileWallet();

  const handleSendTransaction = async () => {
    const instructions: Instruction[] = [
      getAddMemoInstruction({ memo: "gm from Mobile Wallet Adapter" }),
    ];

    const signature = await sendTransactions(instructions);
    console.log("Transaction signature:", signature);
  };

  return <Button title="Send Transaction" onPress={handleSendTransaction} />;
}
```
{% endtab %}

{% tab title="@solana/web3.js" %}
`signAndSendTransactions` takes a built transaction plus the `minContextSlot` the blockhash was fetched at, so compile the transaction yourself.

```tsx
import { createMemoInstruction } from "@solana/spl-memo";
import { TransactionMessage, VersionedTransaction } from "@solana/web3.js";
import { useMobileWallet } from "@wallet-ui/react-native-web3js";

function SendTransactionButton() {
  const { account, connection, signAndSendTransactions } = useMobileWallet();

  const handleSendTransaction = async () => {
    if (!account) return;

    const {
      context: { slot: minContextSlot },
      value: latestBlockhash,
    } = await connection.getLatestBlockhashAndContext();

    const message = new TransactionMessage({
      payerKey: account.address,
      recentBlockhash: latestBlockhash.blockhash,
      instructions: [createMemoInstruction("gm from Mobile Wallet Adapter")],
    }).compileToLegacyMessage();

    const transaction = new VersionedTransaction(message);

    const signature = await signAndSendTransactions(
      transaction,
      minContextSlot,
    );

    await connection.confirmTransaction(
      { signature, ...latestBlockhash },
      "confirmed",
    );

    console.log("Transaction signature:", signature);
  };

  return <Button title="Send Transaction" onPress={handleSendTransaction} />;
}
```

{% hint style="warning" %}
`signAndSendTransactions` requires `minContextSlot`. Fetch the blockhash with `getLatestBlockhashAndContext()` so you have the slot to pass along, rather than `getLatestBlockhash()`.
{% endhint %}
{% endtab %}
{% endtabs %}

## Next steps

{% content-ref url="invoke-mwa-sessions-directly.md" %}
[invoke-mwa-sessions-directly.md](invoke-mwa-sessions-directly.md)
{% endcontent-ref %}

{% content-ref url="sample-apps/sample-app-collection.md" %}
[sample-app-collection.md](sample-apps/sample-app-collection.md)
{% endcontent-ref %}

Code samples on this page are subject to the [Apache 2.0 license](https://www.apache.org/licenses/LICENSE-2.0).
