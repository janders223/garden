---
date: 2021-08-02T10:02
---

Listing all images in a shared image gallery

```shell
az sig image-definition list  --resource-group <group> --gallery-name <name> | jq '.[].name'
```

Listing all versions of a specific image definition

```shell
az sig image-version list --gallery-image-definition <definition>  --resource-group <group> --gallery-name <gallery> | jq '.[].name'
```
