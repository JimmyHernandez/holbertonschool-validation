SHELL = /bin/bash
POST_TITLE ?= default-title
POST_NAME ?= default-name

.PHONY: build clean post help go-build hugo-build lint run stop test unit-tests integration-tests check validate

build:  go-build hugo-build ##Build your website and API

lint:   ## Catch errors without the need to compile or execute the application
	@golangci-lint run

run:    build ## Run the application in background by executing the binary
	@./awesome-api >./awesome-api.log 2>&1 &

stop:   ## Stop the application
	@pkill awesome-api || true

hugo-build: ## build website
	@hugo

go-build:   ## Compile the source code of the application to a binary
	@go build

clean:  stop ## Delete all the content inside dist directory
	@rm -rf dist awesome-api awesome-api.log coverage-units.out coverage-integrations.out

post:  ## Create a new post with global variables where file name is POST_NAME and post title is POST_TITLE
	@hugo new posts/$(POST_NAME).md
	@sed -i 's/^title: .*/title: "'"${POST_TITLE}"'"/' content/posts/"${POST_NAME}".md

check:  ## check content and links  of URLs
	@markdownlint content/posts/*.md
	@find content/**/*.md -exec markdown-link-check {} \;

validate: ## validate links in dist folder
	@python3 /opt/W3C-Validator/w3c_validator.py ./dist/index.html 2>&1 || true

help:  ## Show this help usage
	@cat Makefile | grep "^[a-z][a-z\-]*:.*##.*" | sed 's/:.*## /: /'