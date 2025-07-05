# Custom Container image for NSO JS9 instance

This code extends the base JS9 image with additional analysis plugins and supporting binaries.

It also replaces the index page and adds documentation.

## Requirements

- Docker
- Docker Compose
- A reverse proxy. [Caddy-Docker-Proxy](https://github.com/lucaslorentz/caddy-docker-proxy) is recommended. If using another reverse proxy, the included `docker compose` file will need to be modified. For local development, [caddystack](https://github.com/freethoughtdesign/caddystack) can be used as it includes a DNS server that resolves `.test` domains.

## Quick start

Copy `.env.example` to `.env` and populate the environment variables as needed. They are used in the `compose.yml` file.

- `HOST` - The hostname of the site. Defaults to `nso.js9.org`.
- `NETWORK` - The docker network used to communicate with the Caddy-Docker-Proxy reverse proxy. Defaults to `caddy`.
- `TLS` - The Caddy server directive to configure `https`. Defaults to `email`. Use `internal` for local development.

Then run the following:

```
docker compose up --build
```

The first time the above `docker compose` command is run, it can take quite a while to build the heasoft binaries. Subsequent runs will generally used cached layers and the process will be much faster.

Once the container has been built and started, visit the site using the `HOST` URL set in `.env` in a web browser.

## Modifying the index page

The following files in this repository will be copied into the container during a build:

- `index.html`
- All files in `images/`
- All files in `css/`

As you make modifications or additions, you can stop the running container (CTRL-c) and re-start and re-build it with `docker compose up --build`. Then reload the web page at http://localhost:9999 to test the changes.
