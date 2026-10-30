# Seeker Connect

Seeker Connect is a dapp SDK for connecting directly to a certified device’s own wallet, built on Mobile Wallet Adapter.

Seeker Connect is a dapp-only SDK that connects your app directly to a Solana Mobile certified device’s own wallet — Seeker is the first such device. Instead of the generic “pick a wallet” chooser, it provides a branded, direct connect experience using the Endpoint-specific URI (Android App Link) mechanism from the MWA spec.

## Relationship to Mobile Wallet Adapter

Seeker Connect is built on top of the official [Mobile Wallet Adapter](mobile-wallet-adapter.md) libraries. It is a UX/DX layer, not a protocol reimplementation.

## Targets

| Target           | Status                                                                 |
| ---------------- | ---------------------------------------------------------------------- |
| Web              | Available — Wallet Standard implementation, plus an imperative web SDK |
| React Native     | Planned                                                                |
| Android (Kotlin) | Planned                                                                |

A Wallet Standard-compatible package is always provided.

## Get started

The easiest way to get started is with [`solana-mobile create`](../cli/solana-mobile-create.md), using a template that ships Seeker Connect:

{% tabs %}
{% tab title="npm" %}
```bash
npx solana-mobile@latest create my-app --template react-kit-shadcn
```
{% endtab %}

{% tab title="pnpm" %}
```bash
pnpm dlx solana-mobile@latest create my-app --template react-kit-shadcn
```
{% endtab %}

{% tab title="bun" %}
```bash
bunx solana-mobile@latest create my-app --template react-kit-shadcn
```
{% endtab %}
{% endtabs %}

To add Seeker Connect to an existing app, follow the [Quickstart](quickstart.md).
