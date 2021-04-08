![](https://ga4gh.azurewebsites.net/api?repo=CFCD-exercises/application_management&empty)
# Application Management

## Topics

- CF push
- CF start/stop/restart/restage
- CF delete
- CF app
- Scaling (horizontal/vertical)
- Application manifests

## Questions

### Create a new app named 'my-app' located in the current directory with a memory limit of 1 GB and a disk limit of 1 GB, and let Cloud Foundry detect the required buildpack

<details><summary>show</summary>
<p>

```bash
cf push my-app
```
<blockquote>
The arguments for a memory limit and a disk limit can be avoided, because 1 GB is the default value
</blockquote>

</p>
</details>

### Create a new app named 'my-app', located in the current directory, with the following settings (Memory Limit 128 MB, Disk Limit 64 MB, Create Random Route, Detect Buildpack)

<details><summary>show</summary>
<p>

```bash
cf push my-app -m 128M -k 64M --random-route
```

</p>
</details>

### Stop an app called 'my-app' already running in Cloud Foundry

<details><summary>show</summary>
<p>

```bash
cf stop my-app
```

Alternatively, you can use the alias

```bash
cf sp my-app
```

</p>
</details>

### Start an existing app called 'my-app'

<details><summary>show</summary>
<p>

```bash
cf start my-app
```

Alternatively, you can use the alias

```bash
cf st my-app
```

</p>
</details>

### Restart an app called 'my-app' already running in Cloud Foundry

<details><summary>show</summary>
<p>

```bash
cf restart my-app
```

Alternatively, you can use the alias

```bash
cf rs my-app
```

</p>
</details>

### Recreate the executable artifact of an app called 'my-app' using the latest pushed app files and the latest environment (variables, service bindings, buildpack, stack, etc.).

<details><summary>show</summary>
<p>

```bash
cf restage my-app
```

Alternatively, you can use the alias

```bash
cf rg my-app
```

</p>
</details>

### List all apps currently running in Cloud Foundry

<details><summary>show</summary>
<p>

```bash
cf apps
```

Alternatively, you can use the alias 'a'

```bash
cf a
```

</p>
</details>

### Show the details of an app called 'my-app' already running in Cloud Foundry

<details><summary>show</summary>
<p>

```bash
cf app my-app
```

</p>
</details>

### Show the Globally Unique Identifier (GUID) of an app called 'my-app' already running in Cloud Foundry

<details><summary>show</summary>
<p>

```bash
cf app my-app --guid
```

</p>
</details>

### Delete an existing app called 'my-app'. Let the CF CLI prompted for confirmation.

<details><summary>show</summary>
<p>

```bash
cf delete my-app
```

</p>
</details>

### Delete an existing app called 'my-app'. Avoid being prompted for confirmation.

<details><summary>show</summary>
<p>

```bash
cf delete my-app -f
```

</p>
</details>

### Scale an existing app called 'my-app' to 3 instances

<details><summary>show</summary>
<p>

```bash
cf scale my-app -i 3
```

</p>
</details>

### Increase the memory limit of an existing app called 'my-app' to 512 MB

<details><summary>show</summary>
<p>

```bash
cf scale my-app -m 512M
```

### Increase the disk limit of an existing app called 'my-app' to 1 GB

<details><summary>show</summary>
<p>

```bash
cf scale my-app -k 1G
```

</p>
</details>
