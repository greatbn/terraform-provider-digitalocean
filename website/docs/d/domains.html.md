---
layout: "digitalocean"
page_title: "DigitalOcean: digitalocean_domains"
sidebar_current: "docs-do-datasource-domains"
description: |-
  Retrieve information on Domains.
---

# digitalocean_droplets

Get information on domains for use in other resources, with the ability to filter and sort the results.
If no filters are specified, all domains will be returned.

This data source is useful if the domains in question are not managed by Terraform or you need to
utilize any of the domains' data.

Note: You can use the [`digitalocean_domain`](domain) data source to obtain metadata
about a single domain if you already know the `name`.

## Example Usage

Use the `filter` block with a `key` string and `values` list to filter domains.

```hcl
data "digitalocean_domains" "ttl300" {
  filter {
    key = "ttl"
    values = ["300"]
  }
}
```

## Argument Reference

* `filter` - (Optional) Filter the results.
  The `filter` block is documented below.

* `sort` - (Optional) Sort the results.
  The `sort` block is documented below.

`filter` supports the following arguments:

* `key` - (Required) Filter the domains by this key. This may be one of `name`, `urn`, and `ttl`.

* `values` - (Required) A list of values to match against the `key` field. Only retrieves domains
  where the `key` field takes on one or more of the values provided here.

`sort` supports the following arguments:

* `key` - (Required) Sort the domains by this key. This may be one of `name`, `urn`, and `ttl`.

* `direction` - (Required) The sort direction. This may be either `asc` or `desc`.

## Attributes Reference

* `domains` - A list of domains satisfying any `filter` and `sort` criteria. Each domain has the following attributes:  

  - `name` - (Required) The name of the domain.
  - `ttl`-  The TTL of the domain.
  - `urn` - The uniform resource name of the domain
