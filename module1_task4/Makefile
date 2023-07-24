.PHONY: ## Building clean post.

	build clean post

build: ## Building new repository called dist.
	hugo --destination ./dist

clean: ## Delete repository dist.

	rm -rf dist/

post: ## Make new post in md format.

	hugo new posts/$(POST_NAME).md
	sed -i '2s/title: .*/title: "$(POST_TITLE)"/' content/posts/$(POST_NAME).md

help: ## Prints out the list of targets and their usage
	@awk 'BEGIN {FS = ":.*?# "} /^[a-zA-Z_-]+:.*?# / {printf "\033[36m%-10s\033[0m %s\n", $$1, $$2}' $(MAKEFILE_LIST)


