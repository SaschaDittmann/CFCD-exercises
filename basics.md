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

<!--What commands are not listed when using the cf -h?
What does the cf target command do?
What command would you use to list all spaces in your Cloud Foundry organization?
What command would you use to list service offerings in the marketplace?-->
