![](https://ga4gh.datainsights.cloud/api?repo=CFCD-exercises/routing&empty)
# Routing

## Topics

- Route management
- Inter-application communication

## Exercises

### List all domains in the current organization

<details><summary>show</summary>
<p>

```bash
cf domains
```

</p>
</details>

### List all routes in the current space

<details><summary>show</summary>
<p>

```bash
cf routes
```

</p>
</details>

### Create a 'manifest.yml' file for a new app named 'my-app' with the following settings (Memory Limit 512 MB, Disk Limit 2 GB, Detect Buildpack) and map the follwing two routes 'app.cf-app.io' and 'app2.cf-app.io'. Deploy the app using the CF CLI.

<details><summary>show</summary>
<p>

<b>manifest.yml</b>
```yaml
applications:
- name: my-app
  memory: 512M
  disk_quota: 2G
  routes:
  - route: app.cf-app.io
  - route: app2.cf-app.io
```

```bash
cf push
```

</p>
</details>
