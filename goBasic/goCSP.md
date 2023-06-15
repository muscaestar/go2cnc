# go的并发机制
- 基于并发模型CSP(Communicating Sequential Process)
- 三个基本关键字：`go` for goroutine,`chan` for channel, `<-` for read/write channel

## Goroutine
- 基于协程，是线程的轻量级实现
- 占存小，一个线程占存4MB，一个协程占存2KB

## Channel
- 三种形态
  - `chan`: 普通通道，创建方式`make(chan, 1)`, 第二参数为buffer长度
  - `chan<-`: 只写通道
  - `<-chan`: 只读通道
