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

### Create a new app named 'my-app', using the buildpacks 'my_first_buildpack', 'my_second_buildpack', 'my_final_buildpack' (applied in this order) with the default settings. Deploy the app using the 'cf push' command.

<details><summary>show</summary>
<p>

```bash
cf push my-app -b my_first_buildpack -b my_second_buildpack -b my_final_buildpack
```

</p>
</details>

### Create a new app called 'java-app' by using the 'cf push' command with the default settings. The 'java-app.jar' file is located in the '~/java-app/build/libs' folder. Use the buildpack located in the Git repository 'https://github.com/cloudfoundry/java-buildpack.git'.

<details><summary>show</summary>
<p>

```bash
cf push java-app -p '~/java-app/build/libs' -b https://github.com/cloudfoundry/java-buildpack.git
```

</p>
</details>

### You received a report that a buildpack called 'my_buildpack' is causing issues because it contacts the internet during staging and your CF environment must use proxy servers to do so. The address of your proxy server for HTTP requests is 'http://myproxysvr:8080' and for HTTPS requests 'https://myproxysvr:8080'. Create a 'manifest.yml' file for a new app named 'my-app' with the default settings. Deploy the app by using the CF CLI.

<details><summary>show</summary>
<p>

<b>manifest.yml</b>
```yaml
applications:
- name: my-app
  env:
    http_proxy: http://myproxysvr:8080
    https_proxy: https://myproxysvr:8080
  buildpacks:
  - my_buildpack
```

```bash
cf push
```

</p>
</details>

### You have received a report that a legacy buildpack named 'my_buildpack' has no stack record. Associate the stack 'cflinuxfs3' by using the CF CLI.

<details><summary>show</summary>
<p>

```bash
cf update-buildpack my_buildpack --assign-stack cflinuxfs3
```

</p>
</details>

### Delete the buildpacks named 'my_buildpack' by using the CF CLI.

<details><summary>show</summary>
<p>

```bash
cf delete-buildpack my_buildpack
```

</p>
</details>

### You have two buildpacks named 'my_buildpack', one associated with 'stack_a' and the other associated with no (nil) stack association. Delete the buildpack that uses 'stack_a' by using the CF CLI.

<details><summary>show</summary>
<p>

```bash
cf delete-buildpack my_buildpack -s stack_a
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
