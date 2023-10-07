[Mail-In-A-Box](https://mailinabox.email/) custom DNS API module for Caddy
===========================

This package contains a DNS provider module for [Caddy](https://github.com/caddyserver/caddy). It can be used to manage DNS records with [Mail-In-A-Box](https://mailinabox.email/).

## Caddy Mail-In-A-Box

```
dns.providers.miab
```

## Config examples

To use this module for the ACME DNS challenge, [configure the ACME issuer in your Caddy JSON](https://caddyserver.com/docs/json/apps/tls/automation/policies/issuer/acme/) like so:

```json
{
	"module": "acme",
	"challenges": {
		"dns": {
			"provider": {
				"name": "miab",
				"api_url": "https://[your main-in-a-box domain name]/admin/dns/custom"
                "email_address": "[admin account email address]"
                "password": "[corresponding password]"
			}
		}
	}
}
```

or with the Caddyfile:

```
# globally
{
	acme_dns maib {
        api_url https://[your main-in-a-box domain name]/admin/dns/custom
        email_address [admin account email address]
        password [corresponding password]
    }
}
```

```
# one site
tls {
	dns maib {
        api_url https://[your main-in-a-box domain name]/admin/dns/custom
        email_address [admin account email address]
        password [corresponding password]
    }
}
```
