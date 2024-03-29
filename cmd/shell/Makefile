BINARY_NAME=shell
WINDOWS=$(BINARY_NAME)_windows.exe
LINUX=$(BINARY_NAME)_linux
DARWIN=$(BINARY_NAME)_darwin
GOCMD=go
GOBUILD=$(GOCMD) build
GOCLEAN=$(GOCMD) clean
GOGET=$(GOCMD) get -u
RELEASE_DIR=../../release

.PHONY: all clean

all: deps build

deps:
	$(GOGET) github.com/konsorten/go-windows-terminal-sequences
	$(GOGET) github.com/Cbuckles17/genericlog/pkg/genericlog

build: windows linux darwin

run-windows: windows
	./$(WINDOWS)

run-linux: linux
	./$(LINUX)

run-darwin: darwin
	./$(DARWIN)

windows: $(WINDOWS)

linux: $(LINUX)

darwin: $(DARWIN)

$(WINDOWS):
	mkdir -p $(RELEASE_DIR)
	env GOOS=windows GOARCH=amd64 $(GOBUILD) -v -o $(RELEASE_DIR)/$(WINDOWS)

$(LINUX):
	mkdir -p $(RELEASE_DIR)
	env GOOS=linux GOARCH=amd64 $(GOBUILD) -v -o $(RELEASE_DIR)/$(LINUX)

$(DARWIN):
	mkdir -p $(RELEASE_DIR)
	env GOOS=darwin GOARCH=amd64 $(GOBUILD) -v -o $(RELEASE_DIR)/$(DARWIN)

clean:
	rm -f $(RELEASE_DIR)/$(WINDOWS) $(RELEASE_DIR)/$(LINUX) $(RELEASE_DIR)/$(DARWIN)
