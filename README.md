# golang
Golang With Private Optimization


交叉编译：
- 准备环境：

vim ~/.bash_profile 
```shell
export GOPATH=/data/www/golang/gopath
export GOROOT=/data/www/golang/go
export GOARCH=amd64
export GOOS=darwin
export CGO_ENABLED=1
export PATH=$GOROOT/bin:$PATH
```

```
source ~/.bash_profile 

cd $GOROOT/src
./all.bash
```

```
cd path/to/go/src

CGO_ENABLED=0 GOOS=linux GOARCH=amd64 ./make.bash
CGO_ENABLED=0 GOOS=linux GOARCH=386 ./make.bash
CGO_ENABLED=0 GOOS=windows GOARCH=amd64 ./make.bash
CGO_ENABLED=0 GOOS=windows GOARCH=386 ./make.bash
CGO_ENABLED=0 GOOS=freebsd GOARCH=amd64 ./make.bash
CGO_ENABLED=0 GOOS=freebsd GOARCH=386 ./make.bash
```

CGO_ENABLED=0 GOOS={system} GOARCH={amd64 or 386 or arm} ./make.bash

{system}:  linux darwin windows freebsd


-	开始编译:

```shell
CGO_ENABLED=0 GOOS={system} GOARCH={amd64 or 386} go build
```

-	编译祛除符号表与调试信息(gdb)
```shell
go build -ldflags "-s -w" main.go
```

-	编译时解决windows Dos窗口
```shell
go build -ldflags "-H windowsgui" main.go
```
