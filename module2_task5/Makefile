# Define variables
API_BINARY = awesome-api
HUGO_BINARY = hugo

.PHONY: build
build: go-build hugo-build

.PHONY: go-build
go-build:
	go build -o $(API_BINARY) ./awesome-api

.PHONY: hugo-build
hugo-build:
	$(HUGO_BINARY)

.PHONY: run
run: build
	./$(API_BINARY) &

.PHONY: stop
stop:
	killall $(API_BINARY)

.PHONY: help
help:
	@echo "Available targets:"
	@echo "  build     : Build both the static website and the API application"
	@echo "  run       : Start the service in the background"
	@echo "  stop      : Stop the service started by 'make run'"
	@echo "  help      : List all targets with their help message"
	@echo "  lint      : Execute all lint steps"
	@echo "  post      : Add a new post"
	@echo "  test      : Execute all testing targets (unit-tests, integration-tests, and validate)"
	@echo "  clean     : Delete all generated files (logs, test reports, distribution directory, etc.) and call 'make stop' target as preliminary"
