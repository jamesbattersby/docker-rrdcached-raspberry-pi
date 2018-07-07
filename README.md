<p align="center"><a href="https://github.com/crazy-max/docker-rrdcached" target="_blank"><img height="128"src="https://raw.githubusercontent.com/crazy-max/docker-rrdcached/master/.res/docker-rrdcached.jpg"></a></p>

<p align="center">
  <a href="https://microbadger.com/images/crazymax/rrdcached"><img src="https://images.microbadger.com/badges/version/crazymax/rrdcached.svg?style=flat-square" alt="Version"></a>
  <a href="https://travis-ci.org/crazy-max/docker-rrdcached"><img src="https://img.shields.io/travis/crazy-max/docker-rrdcached/master.svg?style=flat-square" alt="Build Status"></a>
  <a href="https://hub.docker.com/r/crazymax/rrdcached/"><img src="https://img.shields.io/docker/stars/crazymax/rrdcached.svg?style=flat-square" alt="Docker Stars"></a>
  <a href="https://hub.docker.com/r/crazymax/rrdcached/"><img src="https://img.shields.io/docker/pulls/crazymax/rrdcached.svg?style=flat-square" alt="Docker Pulls"></a>
  <a href="https://quay.io/repository/crazymax/rrdcached"><img src="https://quay.io/repository/crazymax/rrdcached/status?style=flat-square" alt="Docker Repository on Quay"></a>
  <a href="https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=YY7W3WDEPHCPQ"><img src="https://img.shields.io/badge/donate-paypal-7057ff.svg?style=flat-square" alt="Donate Paypal"></a>
</p>

## About

🐳 [RRDcached](https://oss.oetiker.ch/rrdtool/doc/rrdcached.en.html) image based on Alpine Linux.<br />
If you are interested, [check out](https://hub.docker.com/r/crazymax/) my other 🐳 Docker images!

## Docker

### Environment variables

| Key                              | Default           | Description                               
|----------------------------------|-------------------|-------------------------------------------
| `TZ`                             | `UTC`             | Timezone assigned to the container (e.g. `Europe/Paris`)
| `PUID`                           | `1000`            | Daemon user id
| `PGID`                           | `1000`            | Daemon group id
| `LOG_LEVEL`                      | `LOG_INFO`        | Log level (`-V`)
| `WRITE_TIMEOUT`                  | `300`             | Data is written to disk every *X* seconds (`-w`)
| `WRITE_JITTER`                   |                   | Delay writing of each RRD for a random number of seconds in the range (`-z`)
| `WRITE_THREADS`                  | `4`               | Number of threads used for writing RRD files (`-t`)
| `FLUSH_DEAD_DATA_INTERVAL`       | `3600`            | Every *X* seconds the entire cache is searched for old values which are written to disk (`-f`)

> More info : https://github.com/oetiker/rrdtool-1.x/blob/master/doc/rrdcached.pod

### Volumes

* `/data` : Contains rrd database

### Ports

* `42217` : RRDcached port

## Use this image

### Docker Compose

Docker compose is the recommended way to run this image. You can use the following [docker compose template](examples/compose/docker-compose.yml), then run the container :

```bash
docker-compose up -d
docker-compose logs -f
```

### Command line

You can also use the following minimal command :

```bash
$ docker run -d -p 42217:42217 --name rrdcached \
  -e TZ="Europe/Paris" \
  -v $(pwd)/data:/data \
  crazymax/rrdcached
```

## Update

Recreate the container whenever i push an update :

```bash
docker-compose pull
docker-compose up -d
```

## How can i help ?

All kinds of contributions are welcomed :raised_hands:!<br />
The most basic way to show your support is to star :star2: the project, or to raise issues :speech_balloon:<br />
But we're not gonna lie to each other, I'd rather you buy me a beer or two :beers:!

[![Paypal](.res/paypal.png)](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=YY7W3WDEPHCPQ)

## License

MIT. See `LICENSE` for more details.
