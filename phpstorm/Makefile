DOCKER=docker
JETBRAINS_VERSION=2022.3.3
CONTAINER_URL=docker.io/thunderal/jetbrains:phpstorm-$(JETBRAINS_VERSION)

all:
	$(MAKE) container-build
	$(MAKE) container-push

container-build:
	$(DOCKER) build . --build-arg "JETBRAINS_VERSION=$(JETBRAINS_VERSION)" -t "$(CONTAINER_URL)" --progress plain

container-push:
	$(DOCKER) push "$(CONTAINER_URL)"
