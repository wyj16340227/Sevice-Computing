# <center>*_Go开发环境安装_*<center>

---------------------

## 1.安装golang
### 1.1安装
> 使用`Windows`系统`ssh`登陆

```
ssh wyj970720@192.168.100.2
```

![](http://imglf3.nosdn0.126.net/img/S3F1ejdrdGNrNFdLaHdQVEVRTS93NC8zcTRZM1d4R2VVdVRIQitQd0UwQkRPUFJXRjYrTVZnPT0.png?imageView&thumbnail=500x0&quality=96&stripmeta=0)

> 安装使用`yum`口令，需要注意的是，需要使用超级用户口令。

```
sudo yum install golang
```
> 安装完成之后检查版本

```
go version
```

![](http://imglf5.nosdn0.126.net/img/S3F1ejdrdGNrNFdLaHdQVEVRTS93emE5SlhPMk1aQ1dURlRxRWNrdUVZVTRIYncvWGVoMU1BPT0.png?imageView&thumbnail=500x0&quality=96&stripmeta=0)

-------------

## 1.2配置路径
> 创建工作空间

```
mkdir $HOME/gowork
```

> 创建配置文件，并编写

```
vi $HOME/gowork/profile
```

> 编写如下

```
export GOPATH=$HOME/gowork
export PATH=$PATH:$GOPATH/bin
```

> 之后source使路径生效

```
source ~/.profile
```

> 此时，再看我们的配置信息，就可以看到路径已经生效了

```
go env
```

![](http://imglf5.nosdn0.126.net/img/S3F1ejdrdGNrNFdLaHdQVEVRTS93NUpUNlNKS1JrRjlsM0RMUFlQWVArLzM1WU5SSWdTY2lRPT0.png?imageView&thumbnail=500x0&quality=96&stripmeta=0)

------------------
## 1.3Hello World小程序
> 在工作空间创建一个工作目录

```
mkdir $GOPATH/src/github.com/github-user/hello -p
```

> 使用`vi`创建并编辑一个`hello.go`文件

```
vi $GOPATH/src/github.com/github-user/hello/hello.go
```

> 编写如下：

![](http://imglf4.nosdn0.126.net/img/S3F1ejdrdGNrNFdLaHdQVEVRTS93N2dveldlWU15STU4QUYvbktUVCtZaVc3Mm1xdDV1WkZBPT0.png?imageView&thumbnail=500x0&quality=96&stripmeta=0)

> 运行，有如下显示：

```
go run hello.go
```

![](http://imglf4.nosdn0.126.net/img/S3F1ejdrdGNrNFVsOW5QK1BFL2VaQnhvKzBYRTZ1UnA4TmtpcFI5OThlaXp4dVo3TmZCQmVRPT0.png?imageView&thumbnail=500x0&quality=96&stripmeta=0)

> 到此为止，`golang`环境已经配置完毕！

-----------------------

# 2.安装 Git
> 直接使用口令即可安装

```
sudo yum install git
```

-----------------

# 3.了解Golang
## 3.1构建并安装程序
> 使用我们之前所创建的`hello`文件来构建，由于路径已经被我们添加了，因此我们可以直接使用指令来运行

```
go install github.com/github-user/hello
hello
```

![](http://imglf4.nosdn0.126.net/img/S3F1ejdrdGNrNFdLaHdQVEVRTS93KzVrTE01d0JDQkViY0NaSmNRL0tQQ0lGK1JLN3hWMVlnPT0.png?imageView&thumbnail=500x0&quality=96&stripmeta=0)

## 3.2建立一个字符反转库，为hello提供保障
> 首先，为我们的库创建一个包路径

```
mkdir $GOPATH/src/github.com/github-user/stringutil
```

> 接着，使用`vim`创建文件，并开始编写~

```
vi $GOPATH/src/github.com/github-user/stringutil/stringutil.go
```

![](http://imglf4.nosdn0.126.net/img/S3F1ejdrdGNrNFdLaHdQVEVRTS93NXl4Z01Ud2JGa0p5WmhHc3dzaGRxS2pvRDg0MlNaUnRnPT0.png?imageView&thumbnail=500x0&quality=96&stripmeta=0)

> 测试一下包的编译

```
go build $GOPATH/src/github.com/github-user/stringutil
```

 - 注意，使用`build`指令并不会生成文件，只有使用`install`才会将他装进包中。

> 修改一下我们原来的hello文件，在其中调用stringutil函数

```
vi $GOPATH/src/github.com/github-user/hello/hello.go
```

![](http://imglf5.nosdn0.126.net/img/S3F1ejdrdGNrNFVsOW5QK1BFL2VaQ1prZ2Q5TjhkVmw0Y0YzZ0Nia1FOS3Z3MWZ4c0VVcmVnPT0.png?imageView&thumbnail=500x0&quality=96&stripmeta=0)

> 重新构建并运行

```
go install $GOPATH/src/github.com/github-user/hello
hello
```

![](http://imglf4.nosdn0.126.net/img/S3F1ejdrdGNrNFVsOW5QK1BFL2VaQTUvbVhCQjZ4R1VaUGp5eU9nN1RuY2kreFIva1YwODR3PT0.png?imageView&thumbnail=500x0&quality=96&stripmeta=0)

------------------------

## 3.3尝试使用测试文件
> golang自带了简单的测试系统，即`go test   testing`。下面我们用一个例子来简单的接触一下。
> 比如我们要测试刚才的文件stringutil，那么我们需要在同目录下创建一个名字带有`_test.go`后缀的文件。
> 编写函数如下：

```
vi $GOPATH/src/github.com/github-user/stringutil/reverse_test.go
```

![](http://imglf3.nosdn0.126.net/img/S3F1ejdrdGNrNFVsOW5QK1BFL2VaSisyREU4dkVUUUZXaWFCanNXMDY5WWVWUFhNUzJyQ09RPT0.png?imageView&thumbnail=500x0&quality=96&stripmeta=0)

> 运行测试文件

```
go test github.com/github-user/stringutil
```

![](http://imglf5.nosdn0.126.net/img/S3F1ejdrdGNrNFVsOW5QK1BFL2VaRkNHcElmTFNxYTNVTUNJNVJLSXZPdDZmM3EvNTZFWUZnPT0.png?imageView&thumbnail=500x0&quality=96&stripmeta=0)

-----------

## 3.4调用远程包
> 如果我们有合法的`URL`地址，那么我们就可以远程调用了。

```
go get github.com/golang/example/hello
$GOPATH/bin/hello
```

![](http://imglf5.nosdn0.126.net/img/S3F1ejdrdGNrNFVsOW5QK1BFL2VaRmZuazRlNEUwSjdGZlZSYjlxUjA4QkdGVzVpdTVKTjVBPT0.png?imageView&thumbnail=500x0&quality=96&stripmeta=0)
