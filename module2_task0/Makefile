# Commands
.PHONY: build run stop clean test help

# Variables
BINARY_NAME := awesome-api
LOG_FILE := $(BINARY_NAME).log
PID_FILE := $(BINARY_NAME).pid


help: ## Prints out the list of targets and their usage
	@awk 'BEGIN {FS = ":.*?# "} /^[a-zA-Z_-]+:.*?# / {printf "\033[36m%-10s\033[0m %s\n", $$1, $$2}' $(MAKEFILE_LIST)

build: ## Compile the source code of the application
	go get github.com/gorilla/mux
	go build -o $(BINARY_NAME)

run: ## Run the application in background
	./$(BINARY_NAME) > $(LOG_FILE) 2>&1 & echo $$! > $(PID_FILE)

stop: ## Stop the application with the command 
	-kill `cat $(PID_FILE)` || true
	-rm $(PID_FILE) || true

clean: ## Stop the application
	make stop
	-rm $(BINARY_NAME) || true
	-rm $(LOG_FILE) || true

test: ## You want to test it to ensure that it behaves as expected
	@echo "Testing HTTP endpoint /..."
	@curl -sSf http://localhost:9999 || echo "TESTFAILED"
	@echo "Testing HTTP endpoint /health..."
	@curl -sSf http://localhost:9999/health || echo "TESTFAILED"

