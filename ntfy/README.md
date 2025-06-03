## Usage

```sh
mkdir -p /opt/ntfy/config
cd /opt/ntfy && docker-compose up -d
```

### Caddy

```caddyfile
ntfy.sh, http://nfty.sh {
    reverse_proxy 127.0.0.1:2586

    # Redirect HTTP to HTTPS, but only for GET topic addresses, since we want
    # it to work with curl without the annoying https:// prefix
    @httpget {
        protocol http
        method GET
        path_regexp ^/([-_a-z0-9]{0,64}$|docs/|static/)
    }
    redir @httpget https://{host}{uri}
}
```

## TroubleShooting

## Reference

- [NTFY Doc](https://docs.ntfy.sh/)
