# go环境配置
1. 下载SDK
    下载地址：`https://golang.org/dl/`
    运行命令`go version`，如果显示`go version go1.8.1 darwin/amd64`,表示安装成功。
2. 配置环境变量
    1.在根目录运行命令`open .bash_profile`打开`.bash_profile`文件，
    2.如果不存在,则执行`touch .bash_profile`新建,
    3.如果存在，在文件中添加如下参数：
    ```
    #配置文件夹目录
    export GOROOT=/usr/local/go
    export PATH=$PATH:$GOROOT/bin
    export GOPATH=/Users/Yang/go
    ```
    4.保存编辑，然后在执行`source ~/.bash_profile`，完成环境变量的配置
    5.执行`go env`命令，查看配置后的路径
    
    **说明：**
        `GOROOT`：go SDK的安装目录
        `PATH`：环境变量，需要`go-bin`目录加入到`path`路径下，生成可执行文件就可以直接运行了。
        `GOPATH`为开发常用的目录，建议不要和Go的安装目录一致，在该文件夹下又有三个文件夹：`src`、`pkg`、`bin` ，`src`是自己新建的，`pkg`、`bin`是自动生成的，生成方式继续往后看。
        
        1. `src`：存放开发中的源代码
        2. `bin`：存放编译后生成的可执行文件，可以自己执行 
        3. `pgk`：编译后生成的文件(.a文件)（非main函数的文件在go install后生成）

3. 实例
    1. `cd`到`xxx/go/src`文件夹下,新建一个文件夹`hellogo（mkdir hellogo）`，在`hellogo`文件夹内新建一个`hello.go(vi hello.go)`文件，输入如下代码：

        ```
        package hellogo
        func HelloGo(s string) string {
            return string(s)
        }
        ```

    2. 保存退出后，在当前目录执行 `go install`，如果没有`pkg`文件夹，执行成功后会在`xxx/go`目录下自动生成`pkg`文件夹，并且生成一个`hellogo.a`文件

    3. 继续在src下新建一个`main`文件夹，并新建一个`main.go`文件，输入如下代码：
        
        ```
        package main
        import "fmt"
        import "hellogo"
        func main(){
         fmt.Printf(hellogo.HelloGo("hello go !!! "))
        }
        ```
        1. 在当前目录执行 `go build`，这样就成功的调用了之前生成的库文件，并且会在当前文件夹中多了一个可执行文件`main`，
        2. 然后执行`./main`命令就会输出”hello go !!!“。
        3. 继续执行`go install`命令，执行成功后会在`xxx/go`目录下自动生成`bin`文件夹，执行文件就不再存在该文件中，而是转移到了`bin`文件夹中。
           也可以直接使用`go run main.go`命令运行`main.go`文件.
4. 开发工具下载
    下载地址：`http://www.jetbrains.com/go/download/`
        
        
        
    