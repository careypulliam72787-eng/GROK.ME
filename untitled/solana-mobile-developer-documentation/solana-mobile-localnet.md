# solana-mobile localnet

Run a local Solana validator for emulators and devices.

Run a local Solana validator in a container and forward its ports to connected devices and emulators, so apps on the device can reach `localhost:8899` as if the validator ran on the device itself.

## Shared options

These options apply to `start`, `check`, `forward`, `status`, and `stop`:

| Option                 | Description                                      |
| ---------------------- | ------------------------------------------------ |
| `--device <serial>`    | Target a device serial (repeatable)              |
| `--engine <engine>`    | Validator engine: `surfpool` or `test-validator` |
| `--port <port>`        | Host port for the RPC endpoint                   |
| `--studio-port <port>` | Host port for the Studio UI                      |
| `--ws-port <port>`     | Host port for the WebSocket endpoint             |

## localnet start

Start the validator and forward its ports to every connected device:

{% tabs %}
{% tab title="npm" %}
```bash
npx solana-mobile@latest localnet start
```
{% endtab %}

{% tab title="pnpm" %}
```bash
pnpm dlx solana-mobile@latest localnet start
```
{% endtab %}

{% tab title="bun" %}
```bash
bunx solana-mobile@latest localnet start
```
{% endtab %}
{% endtabs %}

| Option            | Description                                       |
| ----------------- | ------------------------------------------------- |
| `--detach`        | Leave the validator running in the background     |
| `--image <image>` | Container image to run                            |
| `--no-watch`      | Do not re-apply port forwards when devices change |

## localnet check

Verify the validator is reachable from every device:

{% tabs %}
{% tab title="npm" %}
```bash
npx solana-mobile@latest localnet check
```
{% endtab %}

{% tab title="pnpm" %}
```bash
pnpm dlx solana-mobile@latest localnet check
```
{% endtab %}

{% tab title="bun" %}
```bash
bunx solana-mobile@latest localnet check
```
{% endtab %}
{% endtabs %}

| Option   | Description                                   |
| -------- | --------------------------------------------- |
| `--json` | Print a stable JSON report                    |
| `--open` | Also open the Studio UI in the device browser |

## localnet forward

Forward validator ports to connected devices — useful after plugging in a new device:

{% tabs %}
{% tab title="npm" %}
```bash
npx solana-mobile@latest localnet forward
```
{% endtab %}

{% tab title="pnpm" %}
```bash
pnpm dlx solana-mobile@latest localnet forward
```
{% endtab %}

{% tab title="bun" %}
```bash
bunx solana-mobile@latest localnet forward
```
{% endtab %}
{% endtabs %}

| Option    | Description                                        |
| --------- | -------------------------------------------------- |
| `--watch` | Keep re-applying port forwards when devices change |

## localnet logs

Print validator logs:

{% tabs %}
{% tab title="npm" %}
```bash
npx solana-mobile@latest localnet logs
```
{% endtab %}

{% tab title="pnpm" %}
```bash
pnpm dlx solana-mobile@latest localnet logs
```
{% endtab %}

{% tab title="bun" %}
```bash
bunx solana-mobile@latest localnet logs
```
{% endtab %}
{% endtabs %}

| Option            | Description              |
| ----------------- | ------------------------ |
| `--lines <count>` | Number of lines to print |

## localnet status

Show validator and port forward status:

{% tabs %}
{% tab title="npm" %}
```bash
npx solana-mobile@latest localnet status
```
{% endtab %}

{% tab title="pnpm" %}
```bash
pnpm dlx solana-mobile@latest localnet status
```
{% endtab %}

{% tab title="bun" %}
```bash
bunx solana-mobile@latest localnet status
```
{% endtab %}
{% endtabs %}

| Option   | Description                |
| -------- | -------------------------- |
| `--json` | Print a stable JSON report |

## localnet stop

Stop the validator and remove its port forwards:

{% tabs %}
{% tab title="npm" %}
```bash
npx solana-mobile@latest localnet stop
```
{% endtab %}

{% tab title="pnpm" %}
```bash
pnpm dlx solana-mobile@latest localnet stop
```
{% endtab %}

{% tab title="bun" %}
```bash
bunx solana-mobile@latest localnet stop
```
{% endtab %}
{% endtabs %}
