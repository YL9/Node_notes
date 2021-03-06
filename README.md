# Node_notes

Node_notes

-----------------------------

>- 阻塞代码 -> 在文件读取完毕之后才执行完代码

>- 非阻塞代码 -> 不需要等待文件读取完毕，在读取文件的同时执行其余代码 -> 提供程序性能

### 阻塞是按顺序执行的，而非阻塞是不需要按顺序的

> Node.js 使用事件驱动模型，当web server接收到请求，就把它关闭然后进行处理，然后去服务下一个web请求。
当这个请求完成，它被放回处理队列，当到达队列开头，这个结果被返回给用户。
这个模型非常高效可扩展性非常强，因为webserver一直接受请求而不等待任何读写操作。（这也被称之为非阻塞式IO或者事件驱动IO）
在事件驱动模型中，会生成一个主循环来监听事件，当检测到事件时触发回调函数。

>- EventEmitter -> 事件触发与事件监听器功能的封装

------------------2018.05.07 YoliLin

-----------------------------

>- 在 Node.JS 中，存在三种 Stream 分别为: 写入流、管道流、链式流

>- 管道流: 管道流提供了一个输出流到输入流的机制 通常用于从一个流中获取数据并将数据传递到另外一个流中

>- 链式流: 链式流是通过连接输出流到另外一个流并创建多个流操作链的机制 链式流一般用于管道操作

## Node.Js 加载模块的方式

### 从文件模块缓存中加载

>- 尽管原生模块与文件模块的优先级不同，但是都会优先从文件模块的缓存中加载已经存在的模块

### 从原生模块加载

> 原生模块的优先级仅次于文件模块缓存的优先级 require 方法在解析文件名之后，优先检查模块是否在原生模块列表中 以http模块为例，尽管在目录下存在一个 http/http.js/http.node/http.json 文件，require("http") 都不会从这些文件中加载，而是从原生模块中加载
原生模块也有一个缓存区，同样也是优先从缓存区加载 如果缓存区没有被加载过，则调用原生模块的加载方式进行加载和执行

### 从文件加载

>- 当文件模块缓存中不存在，而且不是原生模块的时候，Node.js 会解析 require 方法传入的参数，并从文件系统中加载实际的文件

------------------2018.05.08 YoliLin

### __filename

>- __filename 表示当前正在执行的脚本的文件名。它将输出文件所在位置的绝对路径，且和命令行参数所指定的文件名不一定相同。 如果在模块中，返回的值是模块文件的路径

### __dirname

>- __dirname 表示当前执行脚本所在的目录

### setTimeout(cb, ms)

>- setTimeout(cb, ms) 全局函数在指定的毫秒(ms)数后执行指定函数(cb)。：setTimeout() 只执行一次指定函数 返回一个代表定时器的句柄值

### clearTimeout(t)

>- clearTimeout( t ) 全局函数用于停止一个之前通过 setTimeout() 创建的定时器。 参数 t 是通过 setTimeout() 函数创建的定时器

### setInterval(cb, ms)

>- setInterval(cb, ms) 全局函数在指定的毫秒(ms)数后执行指定函数(cb) 返回一个代表定时器的句柄值。可以使用 clearInterval(t) 函数来清除定时器 setInterval() 方法会不停地调用函数，直到 clearInterval() 被调用或窗口被关闭

------------------2018.05.09 YoliLin
