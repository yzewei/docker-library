# This file is generated by the template.

REGISTRY	?=lcr.loongnix.cn
ORGANIZATION	?=openanolis
REPOSITORY	?=anolisos
TAG		?=23.3
LATEST		?=true

IMAGE=$(REGISTRY)/$(ORGANIZATION)/$(REPOSITORY):$(TAG)
LATEST_IMAGE=$(REGISTRY)/$(ORGANIZATION)/$(REPOSITORY):latest

default: image

rootfs:
	docker run --rm --security-opt seccomp=unconfined \
		-v `pwd`:/wk lcr.loongnix.cn/openanolis/anolisos:23.2\
		/bin/bash -c -- 'yum install -y tar; /wk/mkimage-rootfs.sh;cp /*tar.gz* /wk'

image: rootfs
	docker build \
		--build-arg http_proxy=$(http_proxy) \
		--build-arg https_proxy=$(https_proxy) \
		-t $(IMAGE) \
		.

push:
	docker push $(IMAGE)
	#latest image
	@if [ $(LATEST) = "true" ]; \
		then \
		docker tag $(IMAGE) $(LATEST_IMAGE); \
		docker push $(LATEST_IMAGE); \
	fi
