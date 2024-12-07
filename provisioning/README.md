# Portfolio Site Provisioning

Several side projects are mentioned in the portfolio, and it'd be nice to have live demos of those available for visitors to play with. To keep things simple, the plan is to put all code/assets/etc on a single server running nginx, and just use nginx to serve or proxy_pass as needed. As new side projects are created, include any deployment instructions or scripts here.

## Provisioning

To build this project:

```sh
bin/build
```

To get the server in a state where it can handle the apps we want to host.

TODO: ansible stuff

Getting files to the server (aka deploying the site)

```sh
rsync ./build TODO 
```

## Side Projects

### Gastro

Needs a running instance of the app, with Puma listening on a unix socket. The socket specified in the example nginx config file is `/tmp/gastro.sock`, but that can be anything as long as the two sides agree.

Make sure that the rails environment is such that

```ruby
  config.relative_url_root = '/gastro'
  config.hosts << 'tomkrenzke.com'
  config.hosts << 'gastro'
```

or similar is in the corresponding environment config file. And that `API_PREFIX` is set to `/gastro` in the `app/javascript/api/index.ts` file.

### Spyrograph

This is just some static assets, so a simple rsync or similar into the right directory should do the trick.

### Weather App

For the front-end (in `weather-vue` repo), just build the assets and rsync to the server. For the back-end (in `weather-api` repo), do a `go build *.go` and copy the resulting executable, along with the `.env` file to the server. Make sure the `UNIX_SOCKET` specified in the `.env` is the same as what's in the nginx config.
