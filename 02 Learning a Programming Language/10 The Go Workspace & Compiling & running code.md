 # workspace, 3 directories
 - src: handles namespacing package managementa
 - pkg: packages
 - bin: all your compiled binaries

# 复杂项目的代码结构
来源 - [GoChronicles](https://gochronicles.com/project-structure/) 也解释了 why & how & deeper other 
[![](https://github.com/MichaelCade/90DaysOfDevOps/raw/main/Days/Images/Day10_Go5.png)](https://github.com/MichaelCade/90DaysOfDevOps/blob/main/Days/Images/Day10_Go5.png)
# a litter deeper compiling
Go tools let us build and process go files.
one of the Go tool is `Go`.
you can intall additional tools.

⬇️ type `go` in termainl 
```bash
❯ go
Go is a tool for managing Go source code.
Usage:
	go <command> [arguments]
The commands are:
	# 目前为止已经使用过的 two of these tools
	env         print Go environment information
	version     print Go version
```

接下来学习 `go run`,  `go build` , `go install`, 
`go run`:  compile and runs the main package comprised
`go build`: compile packages and dependencies
`go install`: The same as `go build` but will place the executable in the `bin` folder
⬇️ `go install`  执行后就会在 bin 目录生成 main.ext
![](https://github.com/MichaelCade/90DaysOfDevOps/raw/main/Days/Images/Day10_Go9.png)  
