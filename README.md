# simplesocket

一个简单的客户端 WebSocket 库。

## 快速开始

### 使用之前

simplesocket 约定与服务端使用 JSON 通信，JSON 格式如下

```json
{
    "type":"",
    "data":{}
}
```

### 使用方法

引入 simplesocket

```javascript
import SocketManager from 'simplesocket';
```

传入配置对象，获得 SocketManager 对象

```javascript
const sm = new SocketManager(option);
```

以下是默认配置对象
```javascript
{
    //连接协议，'ws' 或 'wss'
    protocol: 'ws',
    //连接的域名
    host: '',
    //连接的路径
    path: '',
    //连接时携带的 query 参数对象
    query: {},
    //完整的 url，有这个参数时会忽略以上配置项
    url: '',
    //最大尝试连接次数
    maxConnectCount: 5,
};
```

在需要的时候连接
```JavaScript
const socket = sm.connect();
```

在需要的时候关闭连接

```JavaScript
socket.close();
```

监听约定事件

```javascript
//eventName 为约定的事件名，fn 为处理函数
socket.on(eventName,fn);
```

移除监听

```javascript
//eventName 为约定的事件名，fn 为监听时的函数
socket.off(eventName,fn);
```

向服务器端发送消息

```JavaScript
//eventName 为约定的事件名，data 为向服务器提交的数据
socket.emit(eventName,data);
```

## simplesocket 的优势

- 小。体积非常小
- 原生。基于原生的 WebSocket 连接，可以和原生 WebSocket 并存
- 简单。代码非常简单，任何开发者都能轻松阅读和定制
- 无侵入。服务端无需增加任何库和插件
