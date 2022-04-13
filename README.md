# Nextcloud Plus

## What is this

This repository showcases an advanced Nextcloud installation. The following features are included:
- postgres as database
- caddy as reverse proxy (supports automatic TLS)
- no nginx or apache
- full text search using elasticsearch
- OCR using tesseract

## Setup

### Prerequisites

- Docker and docker-compose
- A domain and an A record pointing to the server (this is a requirement for caddy's automatic TLS feature; see https://caddyserver.com/docs/automatic-https)

### Starting the server

```shell
docker network create caddy
docker-compose up -d
```

### Full text search

Install the following Nextcloud apps:
- Full text search
- Full text search - Elasticsearch Platform
- Full text search - Files

Go to `/settings/admin/fulltextsearch` and configure elasticsearch:
- Server address: `http://elastic:mysecretpassword@elasticsearch:9200`
- Index: nextcloud_index (or whatever)
- Analyzer tokenizer: standard
- Local files: yes
- External files: Index path and content
- Index PDF: yes
- Index Office-files: yes

In a terminal run:
```shell
docker-compose exec -u www-data nextcloud /var/www/html/occ fulltextsearch:index
```

Future index updates will be handled by the nextcloud cronjob.

### Nextcloud configuration

### SMTP
Go to `/settings/admin`. Enter SMTP data.

### Default Phone Region
Edit the file `nextcloud/config/custom.config.php`.

## TODO
- [ ] Document `env` files
- [ ] OCR using tesseract (Installed but not verified)