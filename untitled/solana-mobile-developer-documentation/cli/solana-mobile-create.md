# solana-mobile create

Create a new Solana Mobile project from a template.

Scaffold a new Solana Mobile project. Run it without arguments for interactive prompts, or pass a project name and template to skip them:

{% tabs %}
{% tab title="npm" %}
```bash
npx solana-mobile@latest create my-app
```
{% endtab %}

{% tab title="pnpm" %}
```bash
pnpm dlx solana-mobile@latest create my-app
```
{% endtab %}

{% tab title="bun" %}
```bash
bunx solana-mobile@latest create my-app
```
{% endtab %}
{% endtabs %}

After scaffolding, the CLI initializes git, installs dependencies, and runs the template’s init script. Skip any of these with the `--skip-*` flags below.

## Templates

List the available templates and their descriptions:

{% tabs %}
{% tab title="npm" %}
```bash
npx solana-mobile@latest create --list-templates
```
{% endtab %}

{% tab title="pnpm" %}
```bash
pnpm dlx solana-mobile@latest create --list-templates
```
{% endtab %}

{% tab title="bun" %}
```bash
bunx solana-mobile@latest create --list-templates
```
{% endtab %}
{% endtabs %}

Pick one with `--template`:

{% tabs %}
{% tab title="npm" %}
```bash
npx solana-mobile@latest create my-app --template expo-kit-minimal
```
{% endtab %}

{% tab title="pnpm" %}
```bash
pnpm dlx solana-mobile@latest create my-app --template expo-kit-minimal
```
{% endtab %}

{% tab title="bun" %}
```bash
bunx solana-mobile@latest create my-app --template expo-kit-minimal
```
{% endtab %}
{% endtabs %}

Options declared by the selected template are passed through as boolean long flags, e.g. `create my-app --minimal --reset-project`.

## Options

| Option                                     | Description                                           |
| ------------------------------------------ | ----------------------------------------------------- |
| `-d, --dry-run`                            | Show what would happen without writing files          |
| `--list-template-ids`                      | List available template ids as a JSON array           |
| `--list-templates`                         | List available templates                              |
| `--list-versions`                          | Verify your versions of Anchor, AVM, Rust, and Solana |
| `--minimal`                                | Use the minimal template                              |
| `--pm, --package-manager <packageManager>` | Package manager to use                                |
| `--skip-git`                               | Skip git initialization                               |
| `--skip-init`                              | Skip running the init script                          |
| `--skip-install`                           | Skip installing dependencies                          |
| `-t, --template <templateName>`            | Use a template                                        |
| `-v, --verbose`                            | Verbose output                                        |
