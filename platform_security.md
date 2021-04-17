![](https://ga4gh.datainsights.cloud/api?repo=CFCD-exercises/platform_security&empty)
# Platform Security

## Topics

- Roles & Permissions
- Application security groups

## Exercises

### List users in an org called 'my_org' by their assigned roles

<details><summary>show</summary>
<p>

```bash
cf org-users my_org
```

</p>
</details>

### Assign the Org Manager role to a user named 'my@user.com' to the org 'my_org'

<details><summary>show</summary>
<p>

```bash
cf set-org-role 'my@user.com' my_org OrgManager
```

</p>
</details>

### Remove a user named 'my@user.com' from the Org Manager role in the org 'my_org'

<details><summary>show</summary>
<p>

```bash
cf unset-org-role 'my@user.com' my_org OrgManager
```

</p>
</details>

### List users in the 'dev' space of an org called 'my_org' by their assigned roles

<details><summary>show</summary>
<p>

```bash
cf space-users my_org dev
```

</p>
</details>

### Assign the Space Developer role to a user named 'my@user.com' in the 'dev' space of the org 'my_org'

<details><summary>show</summary>
<p>

```bash
cf set-space-role 'my@user.com' my_org dev SpaceDeveloper
```

</p>
</details>

### Remove a user named 'my@user.com' from the Space Developer role in the 'dev' space of the org 'my_org'

<details><summary>show</summary>
<p>

```bash
cf unset-space-role 'my@user.com' my_org dev SpaceDeveloper
```

</p>
</details>
