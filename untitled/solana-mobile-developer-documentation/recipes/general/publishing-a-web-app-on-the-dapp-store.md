# Publishing a Web App on the dApp Store

Learn how to publish a web app on the Solana dApp Store by wrapping it in an Android WebView shell.

Web apps can be published on the dApp Store by wrapping them in an Android WebView shell and submitting the resulting APK. The [`solana-mobile webshell`](../../solana-mobile-webshell.md) command generates that Android project and builds a signed release APK from it.

A WebView shell needs no Digital Asset Links setup, and it keeps Mobile Wallet Adapter working: browsers are rolling out [Local Network Access](https://developer.chrome.com/blog/local-network-access) restrictions that break wallet connections for web apps, including Trusted Web Activity wrappers such as Bubblewrap APKs. The shell handles wallet intents natively instead.

{% stepper %}
{% step %}
## Host your web app

Make sure your web app is reachable at a public URL. If it has a [web manifest](https://developer.mozilla.org/en-US/docs/Web/Manifest), the CLI seeds the app name, icons, and start URL from it.
{% endstep %}

{% step %}
## Update Mobile Wallet Adapter

If your app uses Mobile Wallet Adapter, update `@solana-mobile/wallet-standard-mobile` to **v0.5.1 or later** so it detects the shell and skips the browser permission flow. See [Local Network Access](../mobile-wallet-adapter/local-network-access-permission.md). Apps that do not connect to a wallet can skip this step.
{% endstep %}

{% step %}
## Wrap into an Android APK

Run [`webshell init`](../../solana-mobile-webshell.md#webshell-init) to generate the project and [`webshell build`](../../solana-mobile-webshell.md#webshell-build) to produce a signed release APK.
{% endstep %}

{% step %}
## Publish to the dApp Store

Submit your signed APK through the standard dApp Store publishing process.
{% endstep %}
{% endstepper %}

See our guide to wrapping a web app with the Solana Mobile CLI:

## Wrap a Web App as an APK

Follow the full step-by-step guide in the Web App tab of the APK building guide.
