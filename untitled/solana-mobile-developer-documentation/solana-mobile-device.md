# solana-mobile device

Work with connected devices and emulators.

Work with Android devices and emulators connected over adb.

## device install

Install APKs from local files, directories, or the built-in APK catalog. Run it without arguments to pick from the catalog, which includes tools like the Mobile Wallet Adapter test wallet (`fakewallet`):

{% tabs %}
{% tab title="npm" %}
```bash
npx solana-mobile@latest device install
```
{% endtab %}

{% tab title="pnpm" %}
```bash
pnpm dlx solana-mobile@latest device install
```
{% endtab %}

{% tab title="bun" %}
```bash
bunx solana-mobile@latest device install
```
{% endtab %}
{% endtabs %}

Or pass one or more APK files or directories:

{% tabs %}
{% tab title="npm" %}
```bash
npx solana-mobile@latest device install ./app-release.apk --all
```
{% endtab %}

{% tab title="pnpm" %}
```bash
pnpm dlx solana-mobile@latest device install ./app-release.apk --all
```
{% endtab %}

{% tab title="bun" %}
```bash
bunx solana-mobile@latest device install ./app-release.apk --all
```
{% endtab %}
{% endtabs %}

| Option              | Description                                      |
| ------------------- | ------------------------------------------------ |
| `--all`             | Install on every connected device                |
| `--device <serial>` | Target a device serial                           |
| `--downgrade`       | Allow version downgrades (`adb install -d`)      |
| `--force`           | Re-download catalog APKs even when cached        |
| `--grant`           | Grant all runtime permissions (`adb install -g`) |
| `--list`            | List the APKs available in the catalog           |
| `-v, --verbose`     | Verbose output                                   |

## device list

List connected devices and emulators:

{% tabs %}
{% tab title="npm" %}
```bash
npx solana-mobile@latest device list
```
{% endtab %}

{% tab title="pnpm" %}
```bash
pnpm dlx solana-mobile@latest device list
```
{% endtab %}

{% tab title="bun" %}
```bash
bunx solana-mobile@latest device list
```
{% endtab %}
{% endtabs %}

| Option   | Description                |
| -------- | -------------------------- |
| `--json` | Print a stable JSON report |

## device open

Open a URL, port, or deep link on a connected device. For localhost URLs with an explicit port, the CLI creates an `adb reverse` (unless `--no-forward` is set) so the device can reach servers running on your machine:

{% tabs %}
{% tab title="npm" %}
```bash
npx solana-mobile@latest device open http://localhost:3000
```
{% endtab %}

{% tab title="pnpm" %}
```bash
pnpm dlx solana-mobile@latest device open http://localhost:3000
```
{% endtab %}

{% tab title="bun" %}
```bash
bunx solana-mobile@latest device open http://localhost:3000
```
{% endtab %}
{% endtabs %}

| Option              | Description                                     |
| ------------------- | ----------------------------------------------- |
| `--device <serial>` | Target a device serial                          |
| `--no-forward`      | Do not create an adb reverse for localhost URLs |
| `-v, --verbose`     | Explain URL and port forwarding decisions       |

## device tune

Apply agent-friendly tweaks to a connected device or emulator — the animations, first-run dialogs, lock screen, and notifications that get in the way of automation. With no target it picks the only connected device, or prompts when several are connected:

{% tabs %}
{% tab title="npm" %}
```bash
npx solana-mobile@latest device tune
```
{% endtab %}

{% tab title="pnpm" %}
```bash
pnpm dlx solana-mobile@latest device tune
```
{% endtab %}

{% tab title="bun" %}
```bash
bunx solana-mobile@latest device tune
```
{% endtab %}
{% endtabs %}

Every tweak starts selected in the picker, so `Enter` applies the lot. Pass `-y` to skip the picker for unattended runs, and `--all` to tune every connected device:

{% tabs %}
{% tab title="npm" %}
```bash
npx solana-mobile@latest device tune --all --yes
```
{% endtab %}

{% tab title="pnpm" %}
```bash
pnpm dlx solana-mobile@latest device tune --all --yes
```
{% endtab %}

{% tab title="bun" %}
```bash
bunx solana-mobile@latest device tune --all --yes
```
{% endtab %}
{% endtabs %}

Physical devices are accepted as well as emulators. A device or Android version that rejects a tweak — a phone with a screen lock keeps its lock screen, for instance — is reported as skipped instead of failing the run.

### Tweaks

| Tweak                      | Description                                                              |
| -------------------------- | ------------------------------------------------------------------------ |
| `animations-off`           | Disable window, transition, and animator animations                      |
| `autofill-off`             | Disable the autofill service and its prompts                             |
| `chrome-notifications-off` | Silence Chrome notifications and its permission prompt                   |
| `chrome-quiet`             | Skip Chrome first-run sign-in and disable the new-tab feed and shortcuts |
| `keyboard-feedback-off`    | Disable touch sounds and haptic feedback                                 |
| `lockscreen-off`           | Disable the lock screen                                                  |
| `provisioning-complete`    | Mark device setup and provisioning as complete                           |
| `screen-awake`             | Keep the screen on while charging and extend the screen timeout          |
| `stylus-handwriting`       | Disable stylus handwriting and its onboarding popup                      |
| `system-notifications-off` | Silence system, Play Store, and Play services notifications              |

### Options

| Option              | Description                         |
| ------------------- | ----------------------------------- |
| `--all`             | Tune every connected device         |
| `--device <serial>` | Target a device serial              |
| `-y, --yes`         | Apply every tweak without prompting |
