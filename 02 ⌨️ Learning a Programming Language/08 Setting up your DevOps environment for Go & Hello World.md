## Get things down
### ⬇️ get Go installed
go to [go.dev/dl](https://go.dev/dl/) 

### check Go installed
```zsh
❯ brew install go
❯ go version
go version go1.19 darwin/arm64
```

### check environment for Go 
> make sure your working directories are configured correctly

```zsh
❯ go env
GO111MODULE="on"
GOARCH="arm64"
GOBIN=""
GOCACHE="/Users/wuzhenquan/Library/Caches/go-build"
GOENV="/Users/wuzhenquan/Library/Application Support/go/env"
GOEXE=""
GOEXPERIMENT=""
GOFLAGS=""
GOHOSTARCH="arm64"
GOHOSTOS="darwin"
GOINSECURE=""
GOMODCACHE="/Users/wuzhenquan/go/pkg/mod"
GONOPROXY=""
GONOSUMDB=""
GOOS="darwin"
GOPATH="/Users/wuzhenquan/go" #⬅️检查下这个 folder 存在吗？如果不存在，自己手动创建。
GOPRIVATE=""
GOPROXY="https://goproxy.cn,direct"
GOROOT="/opt/homebrew/Cellar/go/1.19/libexec"
GOSUMDB="sum.golang.org"
GOTMPDIR=""
GOTOOLDIR="/opt/homebrew/Cellar/go/1.19/libexec/pkg/tool/darwin_arm64"
GOVCS=""
GOVERSION="go1.19"
GCCGO="gccgo"
AR="ar"
CC="clang"
CXX="clang++"
CGO_ENABLED="1"
GOMOD="/dev/null"
GOWORK=""
CGO_CFLAGS="-g -O2"
CGO_CPPFLAGS=""
CGO_CXXFLAGS="-g -O2"
CGO_FFLAGS="-g -O2"
CGO_LDFLAGS="-g -O2"
PKG_CONFIG="pkg-config"
GOGCCFLAGS="-fPIC -arch arm64 -pthread -fno-caret-diagnostics -Qunused-arguments -fmessage-length=0 -fdebug-prefix-map=/var/folders/dh/dny24lk10hd5pbt7ctlt2rfh0000gn/T/go-build1803418744=/tmp/go-build -gno-record-gcc-switches -fno-common"
```


## Create our first program
### 1️⃣ 创建目录和文件
```zsh
❯ mkdir bin
❯ mkdir src
❯ cd src/
❯ mkdir Hello
❯ cd Hello/
❯ touch main.go
```

用 vscode 打开 main.go 的时候 vscode 就会提示你装 [Go 的插件](https://marketplace.visualstudio.com/items?itemName=golang.Go) 了, 并且 pkg 目录里会自动装上新的 packages。
### 2️⃣ Get code into your `main.go`
```go
package main
import "fmt"
func main() {
	fmt.Println("Hello #90DaysOfDevOps")
}
```

### 3️⃣ Let's run 
```zsh
❯ go run main.go
```

### 4️⃣ Building our binary using the following command
```zsh
❯ go build main.go
```
![[Pasted image 20220821210451.png]]
















