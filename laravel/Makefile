.DEFAULT_GOAL := help

build:
	cp .env.example .env
	docker-compose run --rm php composer install
	docker-compose run --rm php php artisan migrate

serve: up attach

up:
	docker-compose up -d php

attach:
	docker attach `docker ps -f name=laravel_php -f status=running --format "{{.ID}}"`

stop:
	docker-compose stop

tinker:
	docker-compose run --rm php php artisan tinker

migrate:
	docker-compose run --rm php php artisan migrate

refresh:
	docker-compose run --rm php php artisan migrate:refresh --seed

.PHONY: help
help:
	@grep -E '^[a-zA-Z_-]+:.*?## .*$$' $(MAKEFILE_LIST) | sort | awk 'BEGIN {FS = ":.*?## "}; {printf "\033[36m%-30s\033[0m %s\n", $$1, $$2}'
