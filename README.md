# kong-plugin-route-by-cookie
Kong plugin for dynamically change upstream url based on cookies.

## Overview

This Kong plugin allows you to route client request based on user cookies. It is inspired by [Route By Header](https://docs.konghq.com/hub/kong-inc/route-by-header/).

## Usage

### Enabling the plugin on a Service

```
curl -X POST http://kong:8001/services/{service}/plugins \
    --data "name=route-by-cookie"  \
    --data "config.target_upstream=new-upstream" \
    --data "config.cookie_name=COOKIE_NAME" \
    --data "config.cookie_val=value"
```

### Enabling the plugin on a Route

```
curl -X POST http://kong:8001/routes/{route_id}/plugins \
    --data "name=route-by-cookie"  \
    --data "config.target_upstream=new-upstream" \
    --data "config.cookie_name=COOKIE_NAME" \
    --data "config.cookie_val=value"
```

### Config

- `target_upstream`: Kong Upstream which we want to route the request to
- `config.cookie_name`: Cookie name which we will check at
- `config.cookie_val`: If user's cookie value equals this, Kong will route the user to `target_upstream`

## Supported Kong Releases

Kong >= 2.0

Should work with 1.X but not tested

## Installation

```
luarocks install kong-plugin-route-by-cookie
```

## Tests

You need [Pongo](https://github.com/Kong/kong-pongo) to run the tests.

```
pongo run
```
Expected output:
```
Kong version: 2.2.0
●●●●●●●●●●●●●●●●●●●●●●●●●●●●●●●●●●●●●●●●●●●●●●●●●
49 successes / 0 failures / 0 errors / 0 pending : 5.379104 seconds
```

## Maintainers

[redhoyasa](https://github.com/redhoyasa)
[utix](https://github.com/utix)
