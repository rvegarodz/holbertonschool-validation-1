# Makefile for generating a website from markdown and configuration files

# Default target: generate the website
build:
	hugo

clean:
	rm -rf dist/

post:
	hugo new posts/${POST_NAME}.md
	echo "---\ntitle: ${POST_TITLE}\ndate: `date Iseconds`\ndraft: true\n---" 

# Phony targets
.PHONY: build clean
