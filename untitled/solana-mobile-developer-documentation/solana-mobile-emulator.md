# solana-mobile emulator

Manage Android emulators and system images.

Create, start, and manage Android emulators without opening Android Studio. `emu` works as a shorthand for `emulator`.

## emulator create

Create or update an Android emulator. Run it without arguments for interactive prompts:

{% tabs %}
{% tab title="npm" %}
```bash
npx solana-mobile@latest emulator create --start
```
{% endtab %}

{% tab title="pnpm" %}
```bash
pnpm dlx solana-mobile@latest emulator create --start
```
{% endtab %}

{% tab title="bun" %}
```bash
bunx solana-mobile@latest emulator create --start
```
{% endtab %}
{% endtabs %}

| Option                     | Description                                               |
| -------------------------- | --------------------------------------------------------- |
| `--data-size <size>`       | Data partition size                                       |
| `--device <device>`        | Android device profile id                                 |
| `--profile <profile>`      | Solana Mobile emulator profile                            |
| `--ram-mb <megabytes>`     | RAM size in MB                                            |
| `--sdcard-size <size>`     | SD card size                                              |
| `--sdk-root <path>`        | Android SDK root                                          |
| `--start`                  | Start the emulator after creating it                      |
| `--system-image <package>` | Android system image package                              |
| `--tune`                   | Apply emulator tweaks after starting (requires `--start`) |
| `-v, --verbose`            | Verbose output                                            |
| `--vm-heap-mb <megabytes>` | VM heap size in MB                                        |

## emulator delete

Delete one or more Android emulators:

{% tabs %}
{% tab title="npm" %}
```bash
npx solana-mobile@latest emulator delete my-emulator
```
{% endtab %}

{% tab title="pnpm" %}
```bash
pnpm dlx solana-mobile@latest emulator delete my-emulator
```
{% endtab %}

{% tab title="bun" %}
```bash
bunx solana-mobile@latest emulator delete my-emulator
```
{% endtab %}
{% endtabs %}

| Option              | Description      |
| ------------------- | ---------------- |
| `--sdk-root <path>` | Android SDK root |

## emulator images

Manage Android system images with the `install`, `list`, and `delete` subcommands:

{% tabs %}
{% tab title="npm" %}
```bash
npx solana-mobile@latest emulator images install
```
{% endtab %}

{% tab title="pnpm" %}
```bash
pnpm dlx solana-mobile@latest emulator images install
```
{% endtab %}

{% tab title="bun" %}
```bash
bunx solana-mobile@latest emulator images install
```
{% endtab %}
{% endtabs %}

| Option              | Description                                       |
| ------------------- | ------------------------------------------------- |
| `--all`             | Show all available system images (`install` only) |
| `--sdk-root <path>` | Android SDK root                                  |
| `-v, --verbose`     | Verbose output (`install` and `delete` only)      |

## emulator list

List installed Android emulators:

{% tabs %}
{% tab title="npm" %}
```bash
npx solana-mobile@latest emulator list
```
{% endtab %}

{% tab title="pnpm" %}
```bash
pnpm dlx solana-mobile@latest emulator list
```
{% endtab %}

{% tab title="bun" %}
```bash
bunx solana-mobile@latest emulator list
```
{% endtab %}
{% endtabs %}

## emulator start

Start an Android emulator. Run it without a name to pick one interactively:

{% tabs %}
{% tab title="npm" %}
```bash
npx solana-mobile@latest emulator start my-emulator
```
{% endtab %}

{% tab title="pnpm" %}
```bash
pnpm dlx solana-mobile@latest emulator start my-emulator
```
{% endtab %}

{% tab title="bun" %}
```bash
bunx solana-mobile@latest emulator start my-emulator
```
{% endtab %}
{% endtabs %}

| Option              | Description                          |
| ------------------- | ------------------------------------ |
| `--sdk-root <path>` | Android SDK root                     |
| `--tune`            | Apply emulator tweaks after starting |

## emulator status

Show the status of an Android emulator by name or serial:

{% tabs %}
{% tab title="npm" %}
```bash
npx solana-mobile@latest emulator status
```
{% endtab %}

{% tab title="pnpm" %}
```bash
pnpm dlx solana-mobile@latest emulator status
```
{% endtab %}

{% tab title="bun" %}
```bash
bunx solana-mobile@latest emulator status
```
{% endtab %}
{% endtabs %}

## emulator stop

Stop a running Android emulator by name or serial:

{% tabs %}
{% tab title="npm" %}
```bash
npx solana-mobile@latest emulator stop my-emulator
```
{% endtab %}

{% tab title="pnpm" %}
```bash
pnpm dlx solana-mobile@latest emulator stop my-emulator
```
{% endtab %}

{% tab title="bun" %}
```bash
bunx solana-mobile@latest emulator stop my-emulator
```
{% endtab %}
{% endtabs %}

## emulator tune

Apply the [agent-friendly tweaks](solana-mobile-device.md#device-tune) to a running Android emulator, by name or serial:

{% tabs %}
{% tab title="npm" %}
```bash
npx solana-mobile@latest emulator tune my-emulator
```
{% endtab %}

{% tab title="pnpm" %}
```bash
pnpm dlx solana-mobile@latest emulator tune my-emulator
```
{% endtab %}

{% tab title="bun" %}
```bash
bunx solana-mobile@latest emulator tune my-emulator
```
{% endtab %}
{% endtabs %}

Tuning is opt-in: `emulator start` and `emulator create --start` only apply the tweaks when you pass `--tune`, which is non-interactive and applies all of them. Running `tune` on its own asks which tweaks to apply, with every one pre-selected so `Enter` applies the lot; `-y` skips that question.

Name the emulator in a script. Unlike [`device tune`](solana-mobile-device.md#device-tune), `emulator tune` has no single-candidate shortcut: with no name or serial it opens an emulator picker whenever any emulator is running, one or many, and `-y` does not suppress it — that flag skips the tweak question only. With no emulator running it prints a hint and exits without tuning.

A name matching no running emulator is an error, and one matching more than one asks you to pass a serial instead. Physical device serials are refused here — use [`device tune`](solana-mobile-device.md#device-tune) for those, which does fall back to the only connected device and takes `--device` or `--all`.

| Option      | Description                         |
| ----------- | ----------------------------------- |
| `-y, --yes` | Apply every tweak without prompting |
