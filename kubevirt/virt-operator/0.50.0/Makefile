# This file is generated by the template.

REGISTRY?=lcr.loongnix.cn
ORGANIZATION?=kubevirt
REPOSITORY?=virt-operator
TAG?=0.50.0

IMAGE=$(REGISTRY)/$(ORGANIZATION)/$(REPOSITORY):$(TAG)


default: image

download: 
	wget "http://cloud.loongnix.cn/releases/loongarch64/kubevirt/virt-operator/0.50.0/virt-operator"
	wget "http://cloud.loongnix.cn/releases/loongarch64/kubevirt/csv-generator/0.50.0/csv-generator"
	chmod +x virt-operator
	chmod +x csv-generator

image: download
	docker build \
		-t $(IMAGE) \
		.

push:
	docker push $(IMAGE)

clean:
	rm -f virt-operator \
		csv-generator
