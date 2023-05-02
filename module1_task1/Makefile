.PHONY: build clean post

build:
	hugo

clean:
	rm -rf dist/

post:
	hugo new posts/${POST_NAME}.md
	echo "---\ntitle: ${POST_TITLE}\ndate: `date -Iseconds`\ndraft: true\n---" 
