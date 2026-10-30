# solana-mobile webshell

Wrap a web app in an Android WebView shell.

Turn an existing web app or PWA into an installable Android app: `init` generates an Android WebView project around your URL, and `build` produces a signed release APK you can publish on the [dApp Store](submit-a-new-app.md).

The generated project is a WebView shell, not a [Trusted Web Activity (TWA)](https://developer.chrome.com/docs/android/trusted-web-activity) — it needs no Digital Asset Links setup. Links outside the configured host open in the system browser, and Solana wallet intents are handled natively by the shell.

## webshell init

Generate the Android project. Run it without arguments to be prompted for everything, or pass the values you already know:

{% tabs %}
{% tab title="npm" %}
```bash
npx solana-mobile@latest webshell init my-app --url https://example.com
```
{% endtab %}

{% tab title="pnpm" %}
```bash
pnpm dlx solana-mobile@latest webshell init my-app --url https://example.com
```
{% endtab %}

{% tab title="bun" %}
```bash
bunx solana-mobile@latest webshell init my-app --url https://example.com
```
{% endtab %}
{% endtabs %}

The directory defaults to the current one. `--force` overwrites an existing directory. If your app already has a [web manifest](https://developer.mozilla.org/en-US/docs/Web/Manifest), point `--manifest` at it — by path or URL — and the CLI seeds the app name, URL, and icons from it. A Bubblewrap `twa-manifest.json` works too, and also carries over the application id, versions, and signing key:

{% tabs %}
{% tab title="npm" %}
```bash
npx solana-mobile@latest webshell init --manifest https://example.com/manifest.json
```
{% endtab %}

{% tab title="pnpm" %}
```bash
pnpm dlx solana-mobile@latest webshell init --manifest https://example.com/manifest.json
```
{% endtab %}

{% tab title="bun" %}
```bash
bunx solana-mobile@latest webshell init --manifest https://example.com/manifest.json
```
{% endtab %}
{% endtabs %}

The generated project keeps its configuration in `twa-manifest.json`, so `init` can be re-run against it later.

### Signing

`init` needs a signing keystore, and creates one when the path you give it does not exist yet. Set `SOLANA_MOBILE_KEYSTORE_PASSWORD` (and `SOLANA_MOBILE_KEY_PASSWORD`, if the key uses a different password) to skip the password prompt; otherwise you are asked for a password and a confirmation, since a typo produces a keystore you can never sign an update with. An existing keystore is reused as-is and needs no password until you build.

{% hint style="warning" %}
Keep the keystore file and its passwords safe. Every future update of your app must be signed with the same key — losing it means you cannot update the app. See Google’s [app signing guide](https://developer.android.com/studio/publish/app-signing#secure_key).
{% endhint %}

### Options

| Option                     | Description                                           |
| -------------------------- | ----------------------------------------------------- |
| `--app-name <name>`        | Application display name                              |
| `--application-id <id>`    | Android application id (e.g. `com.example.app`)       |
| `--force`                  | Overwrite an existing directory                       |
| `--keystore-alias <alias>` | Signing keystore alias (default `android`)            |
| `--keystore-path <path>`   | Signing keystore path (created when missing)          |
| `--manifest <path-or-url>` | Web `manifest.json` or Bubblewrap `twa-manifest.json` |
| `--url <url>`              | Web app URL to wrap                                   |
| `--version-code <number>`  | Android `versionCode`                                 |
| `--version-name <name>`    | Android `versionName`                                 |

## webshell build

Build a signed release APK from a webshell project:

{% tabs %}
{% tab title="npm" %}
```bash
npx solana-mobile@latest webshell build my-app
```
{% endtab %}

{% tab title="pnpm" %}
```bash
pnpm dlx solana-mobile@latest webshell build my-app
```
{% endtab %}

{% tab title="bun" %}
```bash
bunx solana-mobile@latest webshell build my-app
```
{% endtab %}
{% endtabs %}

The directory defaults to the current one. The APK lands at `app/build/outputs/apk/release/app-release.apk`, ready to [install on a device](solana-mobile-device.md#device-install) or submit to the dApp Store. Signing passwords come from `SOLANA_MOBILE_KEYSTORE_PASSWORD` and `SOLANA_MOBILE_KEY_PASSWORD` so CI runs never prompt; when they are unset, the build asks for them.

### Options

| Option                     | Description                   |
| -------------------------- | ----------------------------- |
| `--keystore-alias <alias>` | Signing keystore alias        |
| `--keystore-path <path>`   | Signing keystore path         |
| `--stacktrace`             | Pass `--stacktrace` to Gradle |

## Environment variables

| Variable                          | Description                                           |
| --------------------------------- | ----------------------------------------------------- |
| `SOLANA_MOBILE_KEY_PASSWORD`      | Signing key password — defaults to the store password |
| `SOLANA_MOBILE_KEYSTORE_PASSWORD` | Keystore password                                     |
