#  Go依赖管理的基础知识
- 三种（按年代排）：GOPATH，vendor，module
- 现在默认且推荐使用module
- 在特定环境下可以启用vendor

## module使用总结
### 1. 创建module(对应一个仓库)
```sh
$ mkdir exampleproj // 先创建dir
$ cd exampleproj 
$ go mod init examplemodule // 初始化
```
默认会生成`go.mod`, 这个文件唯一确定一个module

### 2. 规整整个module的依赖
```sh
$ go mod tidy
```
- 如果源码没有对应依赖，`go.mod`中的依赖会被自动去除
- 如果源码中依赖还没有进`go.mod`，执行此命令后会自动添加进require区
  - **最小版本依赖**：go mod tidy 自动引入满足当前源码的最小版本
