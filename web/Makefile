SHELL := /bin/bash

.PHONY: serve
serve: .ensure-hugo
	hugo server --templateMetrics --bind 0.0.0.0 --disableFastRender

.PHONY: static
static: .ensure-hugo
	hugo --templateMetrics --verbose --baseURL $(SITE)

.PHONY: test
test: local-link-test

.PHONY: local-link-test
local-link-test:
	../scripts/checklinks

.PHONY: .ensure-hugo
.ensure-hugo:
	command -v hugo

.PHONY: theme
theme:
	git submodule update --init --recursive

.PHONY: clean
clean:
	find content/packages/ -type f -and -not -name _index.md -and -not -name package.md -exec rm {} +
	rm -rf public/* data/*
