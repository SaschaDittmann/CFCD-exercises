![](https://ga4gh.azurewebsites.net/api?repo=CFCD-exercises/application_management&empty)
# Application Management

## Topics

- CF push
- CF start/stop/restart/restage
- CF delete
- CF app
- Scaling (horizontal/vertical)
- Application manifests

## Exercises

### Create a new app named 'my-app', located in the current directory, with a Memory Limit of 1 GB and a Disk Limit of 1 GB, and let Cloud Foundry detect the required buildpack

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

### Create a 'manifest.yml' file for a new app named 'my-app' with the following settings (Memory Limit 128 MB, Disk Limit 64 MB, Create Random Route, Detect Buildpack). Deploy the app using the CF CLI.

<details><summary>show</summary>
<p>

<b>manifest.yml</b>
```yaml
applications:
- name: my-app
  memory: 128M
  disk_quota: 64M
  random-route: true
```

```bash
cf push
```

</p>
</details>

### Create a 'manifest.yml' file for a new app named 'my-app' with the following settings (Memory Limit 512 MB, Disk Limit 512 MB, 2 Instances, Create Random Route, Start the application with 'node myapp.js', Detect Buildpack). Deploy the app using the CF CLI.

<details><summary>show</summary>
<p>

<b>manifest.yml</b>
```yaml
applications:
- name: my-app
  memory: 512M
  disk_quota: 512M
  instances: 2
  random-route: true
  command: node myapp.js
```

```bash
cf push
```

</p>
</details>

### Create a 'manifests-multiple-apps.yml' file to deploy two apps. Both apps should have a Memory Limit of 512 MB and a Disk Limit 512 MB. The first app is called 'node-app', is located in the '~/node-app' folder, and needs two environment variables ('FIRST_NAME' with the value 'Han' and 'LAST_NAME' with the value 'Solo'). The second app is called 'java-app', and the 'java-app.jar' file is located in the '~/java-app/build/libs' folder. Deploy these appa using the CF CLI.

<details><summary>show</summary>
<p>

<b>manifests-multiple-apps.yml</b>
```yaml
memory: 512M
disk_quota: 512M

applications:
- name: node-app
  path: ~/node-app/
  env:
    FIRST_NAME: Han
    LAST_NAME: Solo
- name: java-app
  path: ~/java-app/build/libs/java-app.jar
```

```bash
cf push -f manifests-multiple-apps.yml
```

</p>
</details>

### Create a new app named 'my-app', using the docker image 'ghost', with the following settings (Memory Limit 512 MB, Disk Limit 512 MB, Instances 2)

<details><summary>show</summary>
<p>

```bash
cf push my-app -k 512M -m 512M -i 2 -o ghost
```

</p>
</details>

### Create a 'manifest.yml' file for a new app named 'my-app' with the following settings (Memory Limit 512 MB, Disk Limit 512 MB, 2 Instances, Docker Image 'ghost'). Deploy the app using the CF CLI.

<details><summary>show</summary>
<p>

<b>manifest.yml</b>
```yaml
applications:
- name: my-app
  memory: 512M
  disk_quota: 512M
  instances: 2
  docker:
    image: ghost
```

```bash
cf push
```

</p>
</details>

### Create two manifest files. The first file is called 'base-manifest.yml' with the following settings (Memory Limit 512 MB, Disk Limit 512 MB, 2 Instances). The second file is called 'manifest-inherit.yml', inherit the settings of the first file, as well as defines an app called 'my-app' with the following settings (Memory Limit 512 MB, Disk Limit 512 MB, 3 Instances, environment variables 'FIRST_NAME' with the value 'Han' and 'LAST_NAME' with the value 'Solo', Detect Buildpack). Deploy the app using the CF CLI.

<details><summary>show</summary>
<p>

<b>base-manifest.yml</b>
```yaml
disk_quota: 512M
memory: 512M
instances: 2
```

<b>manifest-inherit.yml</b>
```yaml
inherit: base-manifest.yml
applications:
- name: my-app
  instances: 3
  env:
    FIRST_NAME: Han
    LAST_NAME: Solo
```

```bash
cf push -f manifest-inherit.yml
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
