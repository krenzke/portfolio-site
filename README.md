# Personal Portfolio Website

This repo contains the code needed to provision a server (likely just a DigitalOcean droplet) for hosting a personal portfolio site, along with any live side projects that might need server resources as well. Keep it simple: just a single html page with some useful info, and links to any side projects that you want to highlight.

## Local Development

To get a server up and running

```sh
bin/server
```

and visit <http://localhost:4567>

The main static site is just a single page that lives in `index.html.erb`. Apply any html changes there, along with css and javascript in their respective files.

### Data Files

To add/edit/remove any experience, education, or side project details modify the corresponding yaml file in the `/data` directory.

## Deployment

To build everything

```sh
bin/build
```

TODO: rsync deploy to server

## Provisioning

TODO: uses ansible.
