<br>

<div align="center">
<img width="456" src="https://raw.githubusercontent.com/wayofdev/docker-php-base/master/assets/logo.gh-light-mode-only.png#gh-light-mode-only">
<img width="456" src="https://raw.githubusercontent.com/wayofdev/docker-php-base/master/assets/logo.gh-dark-mode-only.png#gh-dark-mode-only">
</div>

<br>

<br>

<div align="center">
<a href="https://actions-badge.atrox.dev/wayofdev/docker-php-base/goto"><img alt="Build Status" src="https://img.shields.io/endpoint.svg?url=https%3A%2F%2Factions-badge.atrox.dev%2Fwayofdev%2Fdocker-php-base%2Fbadge&style=flat-square"/></a>
<a href="https://github.com/wayofdev/docker-php-base/tags"><img src="https://img.shields.io/github/v/tag/wayofdev/docker-php-base?sort=semver&style=flat-square" alt="Latest Version"></a>
<a href="https://hub.docker.com/repository/docker/wayofdev/postgres"><img alt="Docker Pulls" src="https://img.shields.io/docker/pulls/wayofdev/postgres?style=flat-square"></a>
<a href="LICENSE"><img src="https://img.shields.io/github/license/wayofdev/docker-php-base.svg?style=flat-square&color=blue" alt="Software License"/></a>
<a href="#"><img alt="Commits since latest release" src="https://img.shields.io/github/commits-since/wayofdev/docker-php-base/latest?style=flat-square"></a>
</div>
<br>

# Docker Image: PHP Base

Repository contains dist folder with generated basic PHP images and source code, written on Ansible, to generate them. Is used together with other WOD images, to create local development environment for our projects.

Enabled extensions by default:

| Extension                                                    | Description                                                  | Type   |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------ |
| [intl](https://www.php.net/manual/en/book.intl.php)          | Internationalization functions                               | native |
| [pcntl](https://www.php.net/manual/en/book.pcntl.php)        | Process control                                              | native |
| [sockets](https://www.php.net/manual/en/book.sockets.php)    | Socket communication functions                               | native |
| [pdo_pgsql](https://www.php.net/manual/en/ref.pdo-pgsql.php) | PostgreSQL functions                                         | native |
| [opcache](https://www.php.net/manual/en/book.opcache.php)    | Improves PHP performance by storing precompiled script bytecode in shared memory | native |
| [zip](https://www.php.net/manual/en/book.zip.php)            | Read/write functions for ZIP archives                        | native |
| [bcmath](https://www.php.net/manual/en/book.bc.php)          | For arbitrary precision mathematics                          | native |
| [redis](https://pecl.php.net/package/redis)                  | Functions for interfacing with Redis                         | pecl   |
| [decimal](https://pecl.php.net/package/decimal)              | Arbitrary precision floating-point decimal                   | pecl   |

<br>

If you **like/use** this repository, please consider **starring** it. Thanks!

<br>

## 🔧 Configuration

Ansible is used to generate distribution files, to add or remove PHP extensions, or configure project, see [group_vars/base.yml](https://github.com/wayofdev/docker-php-base/blob/master/src/group_vars/base.yml)

**Default .ini settings for PHP:**

```yaml
settings_opcache_ini:
  php_opcache_enable: 1
  php_opcache_enable_cli: 1

settings_php_ini:
  php_timezone: "UTC"
  php_post_max_size: "16M"
  php_memory_limit: "256M"
```

**Default extension configuration:**

```yaml
ext_native_enabled:
  - intl
  - pcntl
  - sockets
  - pdo_pgsql
  - OPcache
  - zip
  - bcmath

ext_pecl_enabled:
  - redis
  - decimal

ext_pecl_versions:
  redis: "5.3.7"
  decimal: "1.4.0"
```

<br>

To generate dist files use ansible command:

```bash
$ make generate
```

<br>

## ⚙️ Development

To install dependencies and start development you can check contents of our `Makefile`

### →  Requirments

For testing purposes we use **goss** and **dgoss**, follow installation instructions on  [their official README](https://github.com/aelsabbahy/goss/blob/master/extras/dgoss/README.md)

<br>

### → Building locally

Generating distributable Dockerfiles from yaml source code:

```bash
$ make generate
```

<br>

Building default image:

```bash
$ git clone git@github.com:wayofdev/docker-php-base.git
$ make build
```

To **build** image, **test** it and then **clean** temporary files run:

```bash
$ make
```

Building all images:

```bash
$ make build TEMPLATE="7.4-cli-alpine"
$ make build TEMPLATE="7.4-fpm-alpine"
$ make build TEMPLATE="8.0-cli-alpine"
$ make build TEMPLATE="8.0-fpm-alpine"
$ make build TEMPLATE="8.1-cli-alpine"
$ make build TEMPLATE="8.1-fpm-alpine"
```

<br>

## 🧪 Testing

You can check `Makefile` to get full list of commands for local testing. For testing you can use these comands to test whole role or separate tasks:

Testing default image:

```bash
$ make test
```

To test all images:

```bash
$ make test TEMPLATE="7.4-cli-alpine"
$ make test TEMPLATE="7.4-fpm-alpine"
$ make test TEMPLATE="8.0-cli-alpine"
$ make test TEMPLATE="8.0-fpm-alpine"
$ make test TEMPLATE="8.1-cli-alpine"
$ make test TEMPLATE="8.1-fpm-alpine"
```

<br>

### → Code quality tools

Run **yamllint** to validate all yaml files in project:

```bash
$ make lint
```

Run hadolint to validate created Dockerfiles:

```bash
$ make hadolint
```

<br>

## 🤝 License

[![Licence](https://img.shields.io/github/license/wayofdev/docker-php-base?style=for-the-badge&color=blue)](./LICENSE)

<br>

## 🙆🏼‍♂️ Author Information

This repository was created in **2022** by [lotyp / wayofdev](https://github.com/wayofdev).

<br>

## 🫡 Contributors

<img align="left" src="https://img.shields.io/github/contributors-anon/wayofdev/docker-php-base?style=for-the-badge"/>

<a href="https://github.com/wayofdev/docker-nginx/graphs/contributors">
  <img src="https://opencollective.com/wod/contributors.svg?width=890&button=false">
</a>

<br>