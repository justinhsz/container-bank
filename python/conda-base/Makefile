IMAGE_NAME = conda-base

.PHONY: build
build:
	docker build -t $(IMAGE_NAME) .

.PHONY: test
test:
	docker build --no-cache -t $(IMAGE_NAME)-candidate .
	IMAGE_NAME=$(IMAGE_NAME)-candidate test/run

.PHONY: deploy
deploy:
	docker tag $(IMAGE_NAME) default-route-openshift-image-registry.apps-crc.testing/python-dev/$(IMAGE_NAME)
	docker push default-route-openshift-image-registry.apps-crc.testing/python-dev/$(IMAGE_NAME)