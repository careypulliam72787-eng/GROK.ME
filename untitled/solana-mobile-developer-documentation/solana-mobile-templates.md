# solana-mobile templates

Manage template repositories.

Maintain a template repository like [solana-mobile/templates](https://github.com/solana-mobile/templates) — the source of the templates used by [`create`](cli/solana-mobile-create.md). You only need this command if you author or maintain templates.

## templates check

Check that generated template artifacts are up to date:

{% tabs %}
{% tab title="npm" %}
```bash
npx solana-mobile@latest templates check
```
{% endtab %}

{% tab title="pnpm" %}
```bash
pnpm dlx solana-mobile@latest templates check
```
{% endtab %}

{% tab title="bun" %}
```bash
bunx solana-mobile@latest templates check
```
{% endtab %}
{% endtabs %}

## templates generate

Generate template artifacts:

{% tabs %}
{% tab title="npm" %}
```bash
npx solana-mobile@latest templates generate
```
{% endtab %}

{% tab title="pnpm" %}
```bash
pnpm dlx solana-mobile@latest templates generate
```
{% endtab %}

{% tab title="bun" %}
```bash
bunx solana-mobile@latest templates generate
```
{% endtab %}
{% endtabs %}

## templates sync

Sync git-tracked templates to another template repository:

{% tabs %}
{% tab title="npm" %}
```bash
npx solana-mobile@latest templates sync ../my-templates
```
{% endtab %}

{% tab title="pnpm" %}
```bash
pnpm dlx solana-mobile@latest templates sync ../my-templates
```
{% endtab %}

{% tab title="bun" %}
```bash
bunx solana-mobile@latest templates sync ../my-templates
```
{% endtab %}
{% endtabs %}

| Option      | Description                                                                                  |
| ----------- | -------------------------------------------------------------------------------------------- |
| `--dry-run` | Show what would change without writing                                                       |
| `--force`   | Sync even if the target has uncommitted changes — synced files may be overwritten or removed |

All subcommands accept `--root <path>` to point at a template repository other than the current directory.
