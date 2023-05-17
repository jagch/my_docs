# golang

- [golang](#golang)
  - [installation](#installation)
  - [installation grpc in linux ubuntu with zsh](#installation-grpc-in-linux-ubuntu-with-zsh)
## installation

>linux ubuntu
1. Download the file gox.xx.x.linux-amd64.tar.gz
2. sudo tar -C /usr/local -xzf gox.xx.x.linux-amd64.tar.gz
3. ls /usr/local/go
4. vi ~/.profile - with zsh is vi ~/.zshrc
5. In the end write: export PATH=$PATH:/usr/local/go/bin
6. go version

## installation grpc in linux ubuntu with zsh

>linux ubuntu
1. Go to https://grpc.io/docs/languages/go/quickstart/ and install:
   
   ```ssh
    $ go install google.golang.org/protobuf/cmd/protoc-gen-go@v1.28
    $ go install google.golang.org/grpc/cmd/protoc-gen-go-grpc@v1.2
   ```

2. Update your PATH so that the protoc compiler can find the plugins:
   ```ssh
    $ export PATH="$PATH:$(go env GOPATH)/bin"
   ```

3. Tip: https://stackoverflow.com/questions/56287808/can-not-compile-proto-file-in-ubuntu-for-golang/56293038#56293038
   
   zsh: command not found: protoc indicates that protoc is not installed on your machine. To do so, you need to download binary from Official Releases, as you are on an ubuntu machine, I suggest you download protoc-3.7.1-linux-x86_64.zip (This is latest protoc at the time of writing this answer, you should check on the releases and download latest version)

   You can download via browser or use following command:

   ```
   wget "https://github.com/protocolbuffers/protobuf/releases/download/v3.7.1/protoc-3.7.1-linux-x86_64.zip" -O protoc-3.7.1-linux-x86_64.zip
   ```

   Now unzip, you'll get two folders, "bin" and "include".

   Copy bin/protoc to /usr/local/bin/protoc and include/google to /usr/local/include/google

   This will properly install protoc on your machine.

