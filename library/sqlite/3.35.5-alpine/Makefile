# This file is generated by the template.

REGISTRY?=lcr.loongnix.cn
ORGANIZATION?=library
REPOSITORY?=sqlite
TAG?=3.35.5-alpine

IMAGE=$(REGISTRY)/$(ORGANIZATION)/$(REPOSITORY):$(TAG)

SQLITE_VERSION?=3.35.5

default: image

download:
	wget -O sqlite-version-$(SQLITE_VERSION).tar.gz "https://github.com/sqlite/sqlite/archive/refs/tags/version-$(SQLITE_VERSION).tar.gz"

image: download
	docker build \
		-t $(IMAGE) \
		.

push:
	docker push $(IMAGE)
