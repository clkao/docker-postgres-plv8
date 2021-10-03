# postgres-plv8

Docker images for running [plv8](https://github.com/plv8/plv8) 1.4, 1.5, 2.x and 3.x on Postgres 9.4, 9.5, 9.6, 10, 11, 12 and 14(rc). Based on the [official Postgres image](http://registry.hub.docker.com/_/postgres/).

[![clkao/postgres-plv8][docker-pulls-image]][docker-hub-url] [![clkao/postgres-plv8][docker-stars-image]][docker-hub-url] [![clkao/postgres-plv8][docker-size-image]][docker-hub-url] [![clkao/postgres-plv8][docker-layers-image]][docker-hub-url]

## Tags

- `14-3`, `latest` ([12-2/Dockerfile](https://github.com/clkao/docker-postgres-plv8/blob/master/14-3/Dockerfile))
- `12-2`, `latest` ([12-2/Dockerfile](https://github.com/clkao/docker-postgres-plv8/blob/master/12-2/Dockerfile))
- `11-2` ([11-2/Dockerfile](https://github.com/clkao/docker-postgres-plv8/blob/master/11-2/Dockerfile))
- `10-2` ([10-2/Dockerfile](https://github.com/clkao/docker-postgres-plv8/blob/master/10-2/Dockerfile))
- `9.6-2`, ([9.6-2/Dockerfile](https://github.com/clkao/docker-postgres-plv8/blob/master/9.6-2/Dockerfile))
- `9.6-1.4` ([9.6-1.4/Dockerfile](https://github.com/clkao/docker-postgres-plv8/blob/master/9.6-1.4/Dockerfile))
- `9.5-2` ([9.5-1.5/Dockerfile](https://github.com/clkao/docker-postgres-plv8/blob/master/9.5-2/Dockerfile))
- `9.5-1.5` ([9.5-1.5/Dockerfile](https://github.com/clkao/docker-postgres-plv8/blob/master/9.5-1.5/Dockerfile))
- `9.5-1.4` ([9.5-1.4/Dockerfile](https://github.com/clkao/docker-postgres-plv8/blob/master/9.5-1.4/Dockerfile))
- `9.4-2` ([9.4-1.5/Dockerfile](https://github.com/clkao/docker-postgres-plv8/blob/master/9.4-2/Dockerfile))
- `9.4-1.5` ([9.4-1.5/Dockerfile](https://github.com/clkao/docker-postgres-plv8/blob/master/9.4-1.5/Dockerfile))
- `9.4-1.4` ([9.4-1.4/Dockerfile](https://github.com/clkao/docker-postgres-plv8/blob/master/9.4-1.4/Dockerfile))

## Usage

### How to use this image

This image behaves exactly like the official Postgres image with the only difference being the inclusion of the plv8 extension.

```sh
$ docker run -d --name postgres clkao/postgres-plv8
$ docker exec -it postgres bash -c "psql -U postgres -c \"CREATE EXTENSION plv8; SELECT extversion FROM pg_extension WHERE extname = 'plv8';\""
```

You should see the version of the plv8 extension installed.

You can optionally create a service using `docker-compose`:

```yml
postgres:
  image: clkao/postgres-plv8
```

## Image variants

The `clkao/postgres-plv8` image comes in multiple flavors:

### `clkao/postgres-plv8:latest`

Points to the latest release available of Postgres stable with compatible plv8 installed. Occasionally pre-release versions will be included.

### `clkao/postgres-plv8:<majorPostgresVersion>-<plv8Version>`

Points to the latest release available of Postgres `<majorPostgresVersion>` with the latest release available of plv8 `<plv8Version>` installed.

## Supported Docker versions

This image is officially supported on Docker version 19.03, with support for older versions provided on a best-effort basis.

## License

MIT

[docker-hub-url]: https://hub.docker.com/r/clkao/postgres-plv8/
[docker-pulls-image]: https://img.shields.io/docker/pulls/clkao/postgres-plv8.svg?style=flat-square
[docker-stars-image]: https://img.shields.io/docker/stars/clkao/postgres-plv8.svg?style=flat-square
[docker-layers-image]: https://img.shields.io/microbadger/layers/clkao/postgres-plv8.svg?style=flat-square
[docker-size-image]: https://img.shields.io/microbadger/image-size/clkao/postgres-plv8.svg?style=flat-square
