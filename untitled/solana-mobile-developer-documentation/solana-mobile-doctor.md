# solana-mobile doctor

Check your local development environment.

Check that your machine is ready for Solana Mobile development:

{% tabs %}
{% tab title="npm" %}
```bash
npx solana-mobile@latest doctor
```
{% endtab %}

{% tab title="pnpm" %}
```bash
pnpm dlx solana-mobile@latest doctor
```
{% endtab %}

{% tab title="bun" %}
```bash
bunx solana-mobile@latest doctor
```
{% endtab %}
{% endtabs %}

The report covers your operating system, JavaScript runtimes and package managers, Java, the Android SDK and its tools, connected devices and emulators, and ends with a readiness summary plus recommendations for anything that needs fixing.

```
Readiness
  ✓ Project creation          ready
  ✓ Android build             ready
  ✓ Emulator workflow         ready
  • Physical device workflow  unavailable

✓ Ready for Solana Mobile development.
```

## Options

| Option      | Description                                   |
| ----------- | --------------------------------------------- |
| `--json`    | Print a stable JSON report                    |
| `--verbose` | Include resolved paths and diagnostic details |

Use `--json` to consume the report from scripts or CI.
