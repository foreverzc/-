# Window对象

## 一、BOM（浏览器对象模型）

+ BOM（Browser Object Model ） 是浏览器对象模型
+ ![1678878420026](C:\Users\xiaojingang\AppData\Roaming\Typora\typora-user-images\1678878420026.png)

+ window 对象是一个全局对象，也可以是JavaScript 中的 顶级对象
+ 想document、alert（）、conlose.log（）这些都是window的属性，基本BOM的属性和方法都是window的
+ ==所有通过   var   定义在全局变量作用域中的变量==、函数都会变成window 对象的属性和方法
+ ==window对象下的属性和方法调用的时候可以省略 window==



## 二、定时器-延时函数——setTimeout

+ JavaScript 内置的一个用来让代码延迟执行的函数 ==叫 setTimeout==

+ 语法：

  ``` js
  setTimeout(回调函数，等待的毫秒数)
  ```

+ setTimeout 仅仅执行一次，所以可以理解为就是把一段代码延迟执行，平时省略window

+ 清除延时函数：

  ``` js
      <script>
          setTimeout(function () {
              console.log('nihao ');
          }, 2000)
          clearTimeout(timer)
      </script>
  ```

+ 两种定时器的对比 ：执行次数

  + 延时函数：执行一次
  + 间歇函数：每隔一段时间就执行一次，除非手动清除



## 三、JS执行机制

JavaScript 语言的一大特点就是==单线程==，也就是说，==同一个时间只能做一件事==。 

这是因为 Javascript 这门脚本语言诞生的使命所致——JavaScript 是为处理页面中用户的交互，以及操作 

DOM 而诞生的。比如我们对某个 DOM 元素进行添加和删除操作，不能同时进行。 应该先进行添加，之 

后再删除。 

单线程就意味着，所有任务需要排队，前一个任务结束，才会执行后一个任务。这样所导致的问题是： 

==如果 JS 执行的时间过长，这样就会造成页面的渲染不连贯，导致页面渲染加载阻塞的感觉==



+ 为了解决这个问题，利用多核 CPU 的计算能力，HTML5 提出 Web Worker 标准，允许 JavaScript 脚本创建多个 线程。于是，JS 中出现了同步和异步。 

+ **同步** 

  前一个任务结束后再执行后一个任务，程序的执行顺序与任务的排列顺序是一致的、同步的。比如做饭的同 

  步做法：我们要烧水煮饭，等水开了（10分钟之后），再去切菜，炒菜。 

+ **异步** 

  你在做一件事情时，因为这件事情会花费很长时间，在做这件事的同时，你还可以去处理其他事 

  情。比如做饭的异步做法，我们在烧水的同时，利用这10分钟，去切菜，炒菜。 

  **他们的本质区别： 这条流水线上各个流程的执行顺序不同。** 



### 3.1 同步任务

同步任务都在主线程上执行，形成一个执行栈。

### 3.2异步任务

js的异步是通过回调函数实现的(耗时的属于异步任务)

+ 一般而言 异步任务有以下三种类型：
  + 普通事件，如click、resize等
  + 资源加载，如load 、error 等
  + 定时器，包括setInterval、setTimeout等
  + ![1678880549900](C:\Users\xiaojingang\AppData\Roaming\Typora\typora-user-images\1678880549900.png)
+ 异步任务相关添加到 任务队列中（任务队列也称为消息队列）



###  JS执行机制

1. 先执行执行栈中的同步任务。
2. 异步任务放入任务队列中。
3. . 一旦执行栈中的所有同步任务执行完毕，==系统就会按次序读取任务队列中的异步任务==，于是被读取的异步任务结束等待 状态，进入执行栈，开始执行。
4. ![1678880890115](C:\Users\xiaojingang\AppData\Roaming\Typora\typora-user-images\1678880890115.png)

![1678881297709](C:\Users\xiaojingang\AppData\Roaming\Typora\typora-user-images\1678881297709.png)

由于主线程不断的重复获得任务、执行任务、再获取任务、再执行，所以这种==机制被称为 事件循环==





## 四、location对象

+ location的数据类型时对象，它拆分并保存了URL地址的各个组成部分

+ 属于window  可以省略window

+ 常用属性和方法：

+ ### href属性  location.href

  + ==href 属性获取完整的URL地址，对其赋值时用于地址的跳转====自动跳转==

    + ``` js
              console.log(location);
              // 1.href 经常用href 利用js的方法去跳转页面
              location.href = 'http://www.baidu.com'
      ```

+ ### search 属性   location.search

  + ==search 属性获取地址中携带的参数 符号？后面部分==

    +  ``` js
      http://127.0.0.1:5500/BOM/BOM%E7%AC%AC%E4%B8%80%E5%A4%A9/04-location%E5%AF%B9%E8%B1%A1.html?username=123&pwd=123
      ```

    + ``` js
       console.log(location.search);
      ```

    + ==?username=123&pwd=123  只拿 ？ 后面的 部分==

  

+ ### hash 属性   location.hash

  + hash 属性获取地址中的哈希值，符号#后面部分

    + ``` js
              <a href="#/my">我的</a>
              <a href="#/friend">关注</a>
              <a href="#/download">下载</a>
      http://127.0.0.1:5500/BOM/BOM%E7%AC%AC%E4%B8%80%E5%A4%A9/04-location%E5%AF%B9%E8%B1%A1.html#/download
      ```

    + ``` js
              console.log(location.hash);
      ```

    + ==#/download  只拿#后面的==



+ ### reload 方法  loaction.reload()

  + reload  方法来刷新当前页面，传入参数true 时表示强制刷新

    ``` js
  //刷新页面  相当于f5
    loaction.reload()
    //强制刷新
    loaction.reload(true)
    ```

## 五、navigator对象

+ ==navigator的数据类型时对象，该对象下记录了 浏览器自身的相关信息==

+ 常用属性和方法

  + 通过userAgent检测浏览器的版本呢及平台

  + ``` js
    console.log(navigator)
    ```

    用的时候复制下面的一大段代码

  + ``` js
    // 检测 userAgent（浏览器信息）
    !(function () {
    const userAgent = navigator.userAgent
    // 验证是否为Android或iPhone
    const android = userAgent.match(/(Android);?[\s\/]+([\d.]+)?/)
    const iphone = userAgent.match(/(iPhone\sOS)\s([\d_]+)/)
    // 如果是Android或iPhone，则跳转至移动站点
    if (android || iphone) {
    location.href = 'http://m.itcast.cn' }
    })()
    

    ```
    
  + ==!function(){}()  也是立即执行函数==



### 六 histroy对象

+ histroy 的数据类型是对象，主要 管理历史记录，该对象与浏览器地址栏的操作相对应，如前进、后退、历史记录等

+ 常用的属性和方法

  | histroy 对象方法 | 作用                                                         |
  | ---------------- | ------------------------------------------------------------ |
  | back（）         | 可以后退功能                                                 |
  | forward（）      | 前进功能                                                     |
  | go（参数）       | 前进后退功能 参数如果是1  前进一个页面 如果是-1 后退一个页面 |

  ``` js
      <button>houtui</button>
      <button>qianjin</button>
      <script>
          const back = document.querySelector('button:first-child')
          const forward = back.nextElementSibling
          back.addEventListener('click', function () {
              // history.back()
              history.go(-1)
          })
          forward.addEventListener('click', function () {
              // history.forward()
              history.go(1)
          })
      </script>                                                                                                                                                                                  
  ```

  





















































