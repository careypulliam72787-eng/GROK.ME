# Solana Mobile CLI

Command-line tool for Solana Mobile development.

The `solana-mobile` CLI handles the day-to-day tasks of Solana Mobile development: scaffolding projects, checking your environment, managing emulators and devices, running a local validator your devices can reach, and testing wallet interactions.

## Usage

Run the CLI directly with your package manager’s runner — there is no global install:

{% tabs %}
{% tab title="npm" %}
```bash
npx solana-mobile@latest
```
{% endtab %}

{% tab title="pnpm" %}
```bash
pnpm dlx solana-mobile@latest
```
{% endtab %}

{% tab title="bun" %}
```bash
bunx solana-mobile@latest
```
{% endtab %}
{% endtabs %}

Always include the `@latest` tag so the runner resolves the package’s latest release instead of running an older cached version.

## Commands

| Command                                     | Description                                            |
| ------------------------------------------- | ------------------------------------------------------ |
| [`create`](cli/solana-mobile-create.md)     | Create a new Solana Mobile project                     |
| [`device`](solana-mobile-device.md)         | Work with connected devices and emulators              |
| [`doctor`](solana-mobile-doctor.md)         | Check local development dependencies                   |
| [`emulator`](solana-mobile-emulator.md)     | Manage Android emulators                               |
| [`localnet`](solana-mobile-localnet.md)     | Run a local Solana validator for emulators and devices |
| [`playground`](solana-mobile-playground.md) | Serve a wallet testing page and open it on a device    |
| [`templates`](solana-mobile-templates.md)   | Manage template repositories                           |
| [`webshell`](solana-mobile-webshell.md)     | Wrap a web app in an Android WebView shell             |

## Global options

| Option                 | Description                   |
| ---------------------- | ----------------------------- |
| `-h, --help`           | Show help for any command     |
| `--skip-version-check` | Skip checking for CLI updates |
| `-V, --version`        | Print the CLI version         |
