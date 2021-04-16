![](https://ga4gh.datainsights.cloud/api?repo=CFCD-exercises/application_lifecycle&empty)
# Application Lifecycle

- Buildpacks
- Buildpack sources (system,git)
- Stacks
- Health checks
- Buildpack release notes
- Environment Variables
- Tasks

## Exercises

### List all available buildpacks

<details><summary>show</summary>
<p>

```bash
cf buildpacks
```

</p>
</details>

### Create a new app named 'my-app', using the buildpack for static-content websites, with the following settings (Memory Limit 64 MB, Disk Limit 64 MB, Instances 2)

<details><summary>show</summary>
<p>

```bash
cf push my-app -k 64M -m 64M -i 2 -b staticfile_buildpack
```

</p>
</details>

### Create a 'manifest.yml' file for a new app named 'my-app' with the following settings (Memory Limit 64 MB, Disk Limit 64 MB, 2 Instances, Buildpack for static-content). Deploy the app using the CF CLI.

<details><summary>show</summary>
<p>

<b>manifest.yml</b>
```yaml
applications:
- name: my-app
  memory: 64M
  disk_quota: 64M
  instances: 2
  buildpacks:
  - staticfile_buildpack
  
```

```bash
cf push
```

</p>
</details>

### Create a new app named "my-app" for static content websites, without specifying a build pack, by using the CF CLI and use the following settings (Memory Limit 64 MB, Disk Limit 64 MB, Instances 2)

<details><summary>show</summary>
<p>

```bash
touch Staticfile
cf push my-app -k 64M -m 64M -i 2
```

</p>
</details>

### Create a new app named 'my-app', using the CF CLI, with the following settings (cflinuxfs3 Stack, default for everything else)

<details><summary>show</summary>
<p>

```bash
cf push my-app -s cflinuxfs3
```

</p>
</details>

### Create a 'manifest.yml' file for a new app named 'my-app' with the following settings (cflinuxfs3 Stack, default for everything else). Deploy the app using the CF CLI.

<details><summary>show</summary>
<p>

<b>manifest.yml</b>
```yaml
applications:
- name: my-app
  stack: cflinuxfs3
```

```bash
cf push
```

</p>
</details>

### Create a 'manifest.yml' file for a new app named 'my-app' with the following settings (Memory Limit 512 MB, Disk Limit 512 MB, 2 Instances). Ensure that http health checks will be run on /health. Deploy the app using the CF CLI.

<details><summary>show</summary>
<p>

<b>manifest.yml</b>
```yaml
applications:
- name: my-app
  memory: 512M
  disk_quota: 512M
  instances: 2
  health-check-type: http
  health-check-http-endpoint: /health
```

```bash
cf push
```

</p>
</details>

### Show the type of health check performed on an app called 'my-app'

<details><summary>show</summary>
<p>

```bash
cf get-health-check my-app
```

</p>
</details>

### Add a http based health check to an existing app called 'my-app' using the CLI. Ensure that http health checks will be run on /health.

<details><summary>show</summary>
<p>

```bash
cf set-health-check my-app http --endpoint /health
cf rs my-app
```

</p>
</details>

### Create a 'manifest.yml' file for a new app named 'my-app' with the following settings (Memory Limit 512 MB, Disk Limit 512 MB, 2 Instances). The app is very large and requires up to 3 minutes to start. Deploy the app using the CF CLI.

<details><summary>show</summary>
<p>

<b>manifest.yml</b>
```yaml
applications:
- name: my-app
  memory: 512M
  disk_quota: 512M
  instances: 2
  timeout: 180
```

```bash
cf push
```

</p>
</details>

### Create a 'manifest.yml' file to deploy an app called 'my-app' with a Memory Limit of 512 MB and a Disk Limit of 512 MB. The app is located in the '~/my-app' folder, and needs two environment variables ('FIRST_NAME' with the value 'Han' and 'LAST_NAME' with the value 'Solo'). Deploy these appa using the CF CLI.

<details><summary>show</summary>
<p>

<b>manifest.yml</b>
```yaml
applications:
- name: my-app
  memory: 512M
  disk_quota: 512M
  path: ~/my-app/
  env:
    FIRST_NAME: Han
    LAST_NAME: Solo
```

```bash
cf push
```

</p>
</details>

### View all environment variables of an app called 'my-app'

<details><summary>show</summary>
<p>

```bash
cf env my-app
```

</p>
</details>

### Set the environment variable called 'FIRST_NAME' to the value 'Luke', as well as an environment variable called 'LAST_NAME' to the value 'Skywalker', of an existing app called 'my-app' using CF CLI commands.

<details><summary>show</summary>
<p>

```bash
cf set-env my-app FIRST_NAME Luke
cf set-env my-app LAST_NAME Skywalker
cf restage my-app
```

</p>
</details>
