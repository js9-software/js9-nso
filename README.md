# Custom Container image for NSO JS9 instance

This code extends the base JS9 image with additional analysis plugins and supporting binaries.

It also replaces the index page and adds documentation.

## Requirements

- Docker
- Docker Compose

## Quick start

```
docker compose up --build
```

The first time the above command is run, it can take quite a while to build the heasoft binaries. Subsequent runs will generally used cached layers and the process will be much faster.

Once the container has been built and started, visit http://localhost:9999 in a web browser.

## Modifying the index page

The following files in this repository will be copied into the container during a build:

- `index.html`
- All files in `images/`
- All files in `css/`

As you make modifications or additions, you can stop the running container (CTRL-c) and re-start and re-build it with `docker compose up --build`. Then reload the web page at http://localhost:9999 to test the changes.
