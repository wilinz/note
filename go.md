go build 和 go build main 区别



`go build` 和 `go build main` 是 Go 语言中用于编译 Go 程序的两个命令。

`go build` 用于编译当前目录下所有可执行文件。它会编译所有以 main 函数为入口点的 Go 文件。如果当前目录下有多个 main 函数，它会编译所有这些文件。

`go build main` 用于编译当前目录下名为 main 的可执行文件。它只会编译那些名为 main.go 的文件。如果当前目录下不存在这样的文件，它会报错。

所以，如果你想编译当前目录下所有的可执行文件，可以使用 `go build` ，如果你只想编译名为 main.go 的文件，可以使用 `go build main`。



可以使用 `-o` 参数来指定 go build main 的输出文件名称。

格式:

```
Copy code
go build -o [输出文件名称] main.go 
```