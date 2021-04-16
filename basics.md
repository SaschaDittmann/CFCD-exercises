![](https://ga4gh.datainsights.cloud/api?repo=CFCD-exercises/basics&empty)
# Basics

## Topics

- CLI
- CLI plugins
- Logging
- Targeting
- CF help
- Orgs & spaces
- CF curl

## Exercises

### List all commands of installed CLI plugins

<details><summary>show</summary>
<p>

```bash
cf plugins
```

</p>
</details>

### Search the plugin repositories for new versions of installed CLI plugins

<details><summary>show</summary>
<p>

```bash
cf plugins --outdated
```

</p>
</details>

### Install a plugin named 'myplugin' from the registered repositories called 'CF-Community'

<details><summary>show</summary>
<p>

```bash
cf install-plugin -r CF-Community "myplugin"
```

</p>
</details>

### Install a CLI plugin, which is located locally '~/Downloads/cf-plugin'

<details><summary>show</summary>
<p>

```bash
cf install-plugin ~/Downloads/cf-plugin
```

</p>
</details>

### Connecte to the log stream of an app called 'my-app' and show the tailing log entries

<details><summary>show</summary>
<p>

```bash
cf logs my-app
```

</p>
</details>

### Show the recent logs of an app called 'my-app'

<details><summary>show</summary>
<p>

```bash
cf logs my-app --recent
```

</p>
</details>

### View the current targeted organization and space

<details><summary>show</summary>
<p>

```bash
cf target
```

</p>
</details>

### List all organizations

<details><summary>show</summary>
<p>

```bash
cf orgs
```

Alternatively, you can use the alias 'o'

```bash
cf o
```

</p>
</details>

### Set the targeted organization to 'my-org'

<details><summary>show</summary>
<p>

```bash
cf target -o my-org
```

</p>
</details>

### List all spaces in the current organization

<details><summary>show</summary>
<p>

```bash
cf spaces
```

</p>
</details>

### Set the targeted space to 'dev' in the current organization

<details><summary>show</summary>
<p>

```bash
cf target -s dev
```

</p>
</details>

### Create a new organization called 'myorg'

<details><summary>show</summary>
<p>

```bash
cf create-org myorg
```

</p>
</details>

### Create a new organization called 'myorg'. Let the CF CLI prompted for confirmation.

<details><summary>show</summary>
<p>

```bash
cf delete-org myorg
```

</p>
</details>

### Create a new space called 'myspace' in the current organization

<details><summary>show</summary>
<p>

```bash
cf create-space myspace
```

</p>
</details>

### Create a new space called 'myspace' in the organization called 'myorg'

<details><summary>show</summary>
<p>

```bash
cf create-space myspace -o myorg
```

</p>
</details>

### Delete a space called 'myspace' in the current organization. Let the CF CLI prompted for confirmation.

<details><summary>show</summary>
<p>

```bash
cf delete-space myspace
```

</p>
</details>

### Delete a space called 'myspace' in the current organization. Avoid being prompted for confirmation.

<details><summary>show</summary>
<p>

```bash
cf delete-space myspace -f
```

</p>
</details>

### Rename a space called 'myspace' in the current organization to 'mynewspace'

<details><summary>show</summary>
<p>

```bash
cf rename-space myspace mynewspace
```

</p>
</details>

### Prevent connecting with SSH to all apps in the space called 'myspace'

<details><summary>show</summary>
<p>

```bash
cf disallow-space-ssh myspace
```

</p>
</details>

### Check if connecting with SSH to all apps in the space called 'myspace' is allowed.

<details><summary>show</summary>
<p>

```bash
cf space-ssh-allowed myspace
```

</p>
</details>

### Allow SSH access to all apps in the space called 'myspace'

<details><summary>show</summary>
<p>

```bash
cf allow-space-ssh myspace
```

</p>
</details>
