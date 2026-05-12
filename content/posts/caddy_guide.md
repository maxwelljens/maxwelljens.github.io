---
title: "Extremely Easy Hosting with Caddy"
description: "How to stop fighting with web server configuration and just get your site online, with automatic HTTPS."
tags: ["guide", "software", "internet"]
cover:
  image: /caddy_guide/card.jpg
date: 2026-05-11
---

If you have ever set up a web server from scratch, you know the ritual. You
install nginx or Apache, you write a configuration file that looks like a legal
contract written by someone who hates you, you generate a TLS certificate using
Certbot, you set up a cron job to renew it, you hope the renewal works, and
then you discover that your configuration has a subtle syntax error that
requires you to understand five layers of mechanics in order to fix. This is no
exaggeration.

[Caddy](https://caddyserver.com/) is the antidote to this nonsense. It is a web
server written in Go that, by default, does the things other web servers treat
as optional extras. Automatic HTTPS, for example, is not an add-on or a plugin;
it is the default behaviour. You point Caddy at a domain, and it provisions a
TLS certificate from Let's Encrypt or ZeroSSL, serves it, and renews it
automatically. You do not think about certificates ever again. This is a
genuinely novel concept in the web server world, and it is embarrassing that we
accepted the alternative for so long.

## What makes Caddy different

Most web servers seem to treat TLS as an afterthought. You configure the
server, then you configure the certificates, then you configure the renewal
mechanism, then you test to make sure it works, then you forget to check the
cron job, and then your site goes down because the certificate expired. This
process is so universally painful that [hundreds of web pages cover just this
topic](https://www.google.com/search?q=nginx+automatic+tls).

Caddy does not participate in this. When you tell Caddy to serve a domain, it
automatically provisions a certificate, serves it, and renews it. There is no
Certbot, no cron job, no manual intervention. The only requirement is that the
domain's DNS points to your server. Everything else is handled by the daemon.

The other major difference is the configuration format. Caddy uses the
`Caddyfile`, which is a human-readable configuration language that bears no
resemblance to the XML-adjacent nightmare of nginx or Apache. A static file
server for a domain, for example, is three lines:

```caddy
example.com {
    root /var/www/example
    file_server
}
```

That is the entire configuration. It serves `example.com` over HTTPS with an
automatically provisioned certificate. Compare this to the twenty-odd lines
required to achieve the same thing in nginx, and the difference becomes
palpable.

## Installation

Caddy can be installed in several ways, depending on your operating system and
preference. The official [installation
documentation](https://caddyserver.com/docs/install) covers all of them, but
here are the sensible options.

{{< tabs >}}
{{< tab name="Fedora (DNF)" >}}
```bash
sudo dnf copr enable @caddy/caddy
sudo dnf install caddy
```
{{< /tab >}}
{{< tab name="Debian/Ubuntu (APT)" >}}
```bash
sudo apt install -y debian-keyring debian-archive-keyring apt-transport-https curl
curl -1sLf 'https://dl.cloudsmith.io/public/caddy/stable/gpg.key' | sudo gpg --dearmor -o /usr/share/keyrings/caddy-stable-archive-keyring.gpg
curl -1sLf 'https://dl.cloudsmith.io/public/caddy/stable/debian.deb.txt' | sudo tee /etc/apt/sources.list.d/caddy-stable.list
sudo apt update
sudo apt install caddy
```
This also installs systemd service files, which is the ideal setup.
{{< /tab >}}
{{< tab name="Arch Linux" >}}
```bash
sudo pacman -Syu caddy
```
{{< /tab >}}
{{< tab name="macOS (Homebrew)" >}}
```bash
brew install caddy
```
{{< /tab >}}
{{< /tabs >}}

Once installed, verify it with:

```bash
caddy version
```

{{< callout type="info" emoji="ℹ️" >}}
If you installed from a package manager, Caddy might already be running as a
system service. Check with `systemctl status caddy` and stop it if you want to
follow along with the manual examples.
{{< /callout >}}

## Your first Caddyfile

The Caddyfile is the primary way to configure Caddy. By default, Caddy looks
for a file named `Caddyfile` in the current directory. Let's start with the
simplest possible configuration:

```caddy
localhost:8080

respond "Hello, world!"
```

Save this to a file named `Caddyfile` and run:

```bash
caddy run
```

Visit `http://localhost:8080` in your browser, and you should see "Hello,
world!". Congratulations, you have a working web server.

{{< callout type="info" >}}
When you have only one site block, the curly braces are optional. The above is
shorthand for:
```caddy
localhost:8080 {
    respond "Hello, world!"
}
```
{{< /callout >}}

The `caddy run` command starts the server in the foreground. Press `Ctrl + C`
to stop it. If you want to run it in the background, use `caddy start` and
`caddy stop` to manage it.

## Serving static files

Serving static files is where Caddy trivialises what used to be a
configuration ordeal. This is all you need to serve a directory over HTTPS:

```caddy
example.com {
    root /var/www/example
    file_server
}
```

If you want to enable directory listings for directories that lack an index
file:

```caddy
example.com {
    root /var/www/example
    file_server browse
}
```

The `file_server` directive also supports precompressed files. If you have
`.br`, `.zst`, or `.gz` sidecar files next to your static assets, Caddy will
serve them automatically with the appropriate `Content-Encoding` header:

```caddy
example.com {
    root /var/www/example
    file_server {
        precompressed br zstd gzip
    }
}
```

SEO check telling you that headers are not gzip-compressed? No problem. Just
add an [`encode`](https://caddyserver.com/docs/caddyfile/directives/encode)
directive before `file_server`:

```caddy
example.com {
    root /var/www/example
    encode
    file_server
}
```

More details on the `file_server` directive can be found in [the official
documentation](https://caddyserver.com/docs/caddyfile/directives/file_server).

## Reverse proxy

The reverse proxy is where Caddy really demonstrates its utility. You have a
backend service running on port 9000, and you want it accessible via your
domain with automatic HTTPS. This is the configuration:

```caddy
app.example.com {
    reverse_proxy localhost:9000
}
```

That is it. Caddy reverse-proxies all requests to `localhost:9000`, provisions
a certificate for `app.example.com`, and handles HTTPS transparently.

If you need to load-balance across multiple backends:

```caddy
app.example.com {
    reverse_proxy node1:8080 node2:8080 node3:8080
}
```

Caddy supports several load-balancing policies, including `random`,
`round_robin`, `least_conn`, `first`, `ip_hash`, `uri_hash`, `header`, and
`cookie`. The full list is documented in [the reverse_proxy
documentation](https://caddyserver.com/docs/caddyfile/directives/reverse_proxy).

For example, to use sticky sessions with a cookie:

```caddy
app.example.com {
    reverse_proxy /api/* node1:8080 node2:8080 {
        lb_policy cookie api_sticky
    }
}
```

### PHP (FastCGI)

If you are running PHP applications, Caddy supports FastCGI proxying:

```caddy
example.com {
    root * /var/www/example
    php_fastcgi unix//var/run/php-fpm.sock
    file_server
}
```

The `php_fastcgi` directive is actually a shortcut that expands to a
`reverse_proxy` with the FastCGI transport, plus some sensible defaults for
PHP.

## Automatic HTTPS

This is the feature that makes Caddy worth using even if you ignore everything
else. By default, any domain you configure in a Caddyfile will automatically
receive a TLS certificate from Let's Encrypt or ZeroSSL. Caddy handles the
entire ACME process: it creates the certificate, serves it, and renews it
before it expires. You do not configure a certificate. You do not run Certbot.
You do not set up cron jobs.

```caddy
mysite.com {
    root /var/www/mysite
    file_server
}
```

The first time a request hits `mysite.com`, Caddy provisions a certificate.
From that point on, every request is served over HTTPS. The certificate is
renewed automatically, and Caddy will even attempt to replace a failing
certificate before it expires.

To configure the email address used for ACME registration, set it in the
global options block:

```caddy
{
    email admin@example.com
}

mysite.com {
    root /var/www/mysite
    file_server
}
```

## Running as a service

For production use, you typically want Caddy running as a system service. On
systemd-based systems installed via a package manager, this should be handled
automatically. You can control it with:

```bash
sudo systemctl enable caddy
sudo systemctl start caddy
sudo systemctl status caddy
```

On other systems, or if you installed the static binary, you can use Caddy's
built-in service management:

```bash
sudo caddy run
```

This runs in the foreground, which is fine for testing. For production, use the
service files provided in the [running
documentation](https://caddyserver.com/docs/running).

When you need to reload a configuration change without downtime:

```bash
caddy reload
```

This performs a graceful, zero-downtime reload. The new configuration is loaded
alongside the old one, and only when the new one is confirmed healthy does the
old one get shut down. If the new configuration has errors, Caddy rolls back
and continues serving the old one. This is the correct way to update a running
server.

{{< callout type="warning" emoji="⚠️" >}}
Do not stop and restart Caddy to apply configuration changes. Stopping the
server causes downtime. Use `caddy reload` instead, which uses the API under
the hood to perform a graceful, zero-downtime update.
{{< /callout >}}

## Caddyfile concepts worth knowing

### Multiple sites

```caddy
mysite.com {
    root /var/www/mysite
    file_server
}

api.mysite.com {
    reverse_proxy localhost:9000
}
```

Each site block is isolated. Requests do not cascade between blocks.

### Snippets (reusable blocks)

Define reusable configuration blocks outside of site blocks:

```caddy
(logging) {
    log {
        output file /var/log/caddy/access.log
        format json
    }
}

mysite.com {
    import logging
    root /var/www/mysite
    file_server
}

othersite.com {
    import logging
    reverse_proxy localhost:9000
}
```

Snippets keep your Caddyfile [DRY](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself)
without resorting to template engines or copy-paste.

### Environment variables

Refer to environment variables in your Caddyfile:

```caddy
{$DOMAIN:localhost} {
    root /var/www/{$SITE_ROOT:www}
    file_server
}
```

The syntax `{$VAR:default}` provides a default value if the environment
variable is not set. Variables are substituted before parsing, so they can
expand to partial or multiple tokens.

### Matchers

Directives apply to all requests by default. To constrain them, use matchers:

```caddy
example.com {
    @post {
        method POST
    }

    # Only reverse-proxy POST requests
    reverse_proxy @post localhost:9000

    # Serve everything else as static files
    file_server
}
```

Caddy supports path matchers (`/api/*`), header matchers, query matchers,
protocol matchers, remote IP matchers, and more. These are detailed in [the
matchers documentation](https://caddyserver.com/docs/caddyfile/matchers).

## Caddy vs. the alternatives

The technical merits of Caddy compared to other web servers are straightforward
enough.

| Feature | Caddy | nginx | Apache |
|---------|-------|-------|--------|
| Automatic HTTPS | Built-in, default | Requires Certbot + cron | Requires Certbot + cron |
| Config format | Caddyfile (human-friendly) | nginx.conf (error-prone) | .htaccess + httpd.conf |
| TLS renewal | Automatic, daemon-managed | Manual cron job | Manual cron job |
| Default HTTPS | Yes | No | No |
| OCSP stapling | Built-in | Manual config | Manual config |
| Layer 4 (TCP/stream) proxy | Not supported | Built-in | Built-in |
| HTTP/2, HTTP/3 | Built-in | Requires config | Requires config |
| Config reload | Graceful, zero-downtime | Graceful | Requires restart |

The table makes the choice look obvious, and in most cases it is. If you are
setting up a new server today, I cannot think of a compelling reason to use
anything other than Caddy for general-purpose web serving, unless you have a
specific requirement for an nginx module that has no Caddy equivalent, and [in
most cases there is one](https://github.com/caddyserver/xcaddy), since Caddy's
module ecosystem is growing.

The most noteworthy gap is layer 4 (TCP stream) proxying. Caddy operates
entirely at the application layer; it cannot handle raw TCP streams the way
nginx's `stream` module or Apache's `mod_proxy` can. This matters if you need
to terminate TLS for protocols like SMTP, IMAP, or custom TCP-based services,
or if you want to load-balance database connections directly. In those
scenarios, nginx or HAProxy alongside Caddy is still the practical choice.

The only real argument against Caddy is that it is slightly newer, which means
there is less community knowledge and fewer tutorials for obscure edge cases.
But Caddy's configuration is so much simpler that the need for obscure edge
case tutorials is dramatically reduced. For this reason, [Caddy is used
extensively in enterprise technology
stacks](https://theirstack.com/en/technology/caddy). You do not need a blog
post explaining how to set up HTTPS. You just write a domain name and it works.

## Final thoughts

I have been running web servers since I was a teenager, and I have accumulated
a healthy collection of war stories about misconfiguration and virtual hosts,
and the peculiar brand of despair that comes from debugging an Apache rewrite
rule. Caddy eliminated most of those failure modes in a way that is truly
mystical, but I am not complaining.

If you are hosting a personal blog, a small business site, or an API, Caddy is
the correct choice. The configuration is simpler, which means the security is
better, and the maintenance burden is lower. You will spend less time thinking
about your web server and more time thinking about what you are actually
serving, and that is the entire point of a tool.
