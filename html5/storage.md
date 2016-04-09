# HTML5存储
> Web Storage实际上由两部分组成：sessionStorage与localStorage

### 1. localStorage
 * 没有时间限制的数据存储
 * 在所有同源窗口中都是共享的

```javascript
存储：
window.localStorage.setItem('key', 'value');
取值：
window.localStorage.getItem('key');
删除：
window.localStorage.removeItem('key');
清除：
window.localStorage.clear();
```	

### 2. sessionStorage
 * 针对一个 session 的数据存储
 * 不在不同的浏览器窗口中共享，即使是同一个页面

```javascript
存储：
window.sessionStorage.setItem('key', 'value');
取值：
window.sessionStorage.getItem('key');
删除：
window.sessionStorage.removeItem('key');
清除：
window.sessionStorage.clear();
```

>与cookie的区别

* Web Storage存储空间更大, 5M或者更大；cookie存储一般不能超过4kb。
* Web Storage不会自动把数据发给服务器，仅为本地存储；cookie在每次http请求都会传送到服务端。
* sessionStorage不在不同的浏览器窗口中共享，即使是同一个页面；localStorage在所有同源窗口中都是共享的；cookie也是在所有同源窗口中都是共享的。
* Web Storage 支持事件通知机制，可以将数据更新的通知发送给监听者。