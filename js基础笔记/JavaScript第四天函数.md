

## JavaScript第四天

### 1.函数

+ 函数：

  function，是被设计为==执行特定任务==的==代码块==

+ 说明

  函数可以吧具有相同 或相似逻辑的代码 “包裹”起来，通过函数用执行这些被“包裹”的代码逻辑，这么做的优势是 ==精简代码方便复用==

==比如alert()  prompt()   console.log() 都是一些js函数 只不过已经封装好了 我们直接使用==



### 2.函数使用

#### 2.1 函数的规范

+ 函数的声明语法

``` js
function 函数名(){
		函数体
}
```

+ 函数的命名规范
  + 和变量基本一致
  + 尽量小驼峰命名法
  + 前缀应该为动词
  + 明明建议：常用动词约定

| 动词 | 含义                   |
| ---- | ---------------------- |
| can  | 判断是否可执行某个动作 |
| has  | 判断是否含义某个值     |
| is   | 判断是否为某个值       |
| get  | 获取某个值             |
| set  | 设置某个值             |
| load | 加载某些数据           |

#### 2.2 函数的使用

+ 函数的调用方法

  ``` js
  //函数调用，这些函数体内的代码逻辑会被执行
  函数名()
  ```



#### 2.3 函数传参

+ 声明语法

  ``` js
  function 函数名（参数列表）{
  		函数体
  }
  ```

  ``` js
  function getSquare(num1){
      document.write(num1*num2)
  }
  ```

  ```js
  function getSum(num1,num2){
  document.write(num1+num2)
  }
  ```

+ 参数列表

  + 传入数据列表
  + 声明这个函数需要传入几个数据
  + 多个数据同逗号隔开

+ 调用语法

  ```js
  函数名(传递的参数列表)
  ```

  例如

  ``` js
  getSquare(8)
  ```

  ``` js
  getSum(10,20)
  ```

+ 调用函数，需==要传入几个数据就写几个，用逗号隔开==

##### 2.3.1形参和实参的参数传递

+ ==形参：可以看做一个变量 如果变量不给值 默认是undefined==
+ ==用户不输入实参 如果出现underfind+underfind  结果就是 NaN==
+ 我们可以改进，用户不输入实参 可以给形参默认值，可以默认为0，这样更严谨
+ ==如果有参数 num1 = 0 不执行== 只会在缺少实参传递时才会被执行

```js
function getSum(num1 = 0, num2 = 0) {
  let sum = num1
  document.write(`两个数的和是:${sum}`)
}
getSum(0, 0)
getSum(10, 20)
```

+  实参可以是变量

``` js
// 求n-m的累加和
function getSum(n = 0, m = 0) {
  let sum = 0
  for (let i = n; i <= m; i++) {
    sum += i
  }
  alert(`累加和为：${sum}`)
}
let num1 = +prompt('请输入第一个数：')
let num2 = +prompt('情输入第二个数：')
getSum(num1, num2)
```





### 3.函数返回值

+ 当调用一个函数，这个函数就会返回一个结果出来
+ ==函数内部是不需要输出结果的，而是返回结果== 
+ 返回值对执行的扩展性更高，可以让其他程序使用这个结果
+ 这就是有返回值的函数
+ 相当于 ==调用函数 需要点餐  函数内部是厨子  厨子做完需要将返回值返回给点餐的人==
+ 有些函数没有返回值 例如 alert()

#### 3.1 return的使用方法

+ 当函数需要返回数据出去时，需要用到return 关键字

+ 当执行函数return时  就不再执行下面的函数 所以 一般 return在最下面

+ ==return后面不接数据或者函数内 不写return 默认返回 underfind==

+ 语法

  ``` js
  return 数据
  return 20
  ```

+ 使用

  ``` js
  function getSum(x,y){
  		return x + y
  }
  let num = getSum(10,30)
  document.write(num)
  ```

  ``` js
  function getSum(x, y) {
    // 函数的返回值
    return x + y   //相当于执行了 getSum(20,30)=x+y
  }
  let re = getSum(20, 30)//这种看着更方便
  document.write(re)
  
  
  document.write(getSum(20, 30))
  ```

+ ==return 返回 多个数据 用数组==

  ``` js
  //求数组中最大最小值
  function getArrMax(arr = []) {
    let max = arr[0]
    let min = arr[0]
    for (let i = 1; i < arr.length; i++) {
      if (max < arr[i]) {
        max = arr[i]//求最大值
      }
      if (min > arr[i]) {
        min = arr[i]//求最小值
      }
    }
    return [max, min]
  }
  let newArr = getArrMax([2, 4, 56, 3, 21])
  console.log(`数组的最大值是：${newArr[0]}`)
  console.log(`数组的最小值是：${newArr[1]`)
  ```

###  4. 函数细节补充

+ ==两个相同的函数 后面的 会覆盖前面的函数==
+ 在JavaScript中 实参的个数和形参的个数可以不一致
  + 如果实参过少 会自动填上undefined  输出NaN
  + 如果实参过多 那么多余的会被忽略（函数内部有一个arguments，里面装着所有的实参)
+ 函数一旦碰到return 就不会再往下执行了 函数的结束用return





### 5.作用域

名字的 ==可用性的代码范围就是这个名字的作用域==

作用域的使用提高了程序逻辑的局部性，增强了程序的可靠性，减少了名字的冲突

+ ==全局变量==：函数外部的 let 的变量

+ ==局部变量==：函数内部let 的变量

+ ==特殊情况：如果函数内部没有 用 let 声明变量 ，直接赋值也可以 当做全局变量看 但是强烈不推荐==
+ 形参也是看做局部变量

### 变量的访问原则

+ 只要是代码就至少有一个作用域
+ 写在函数内部的局部作用域
+ 如果函数中还有函数，那么在这作用域 中就又可以诞生一个作用域
+ ==访问原则：在能够访问到的情况下， 先局部 局部没有在找全局==  就近原则



### 6.匿名函数

+ 函数可分为 
  + ==具名函数：具名函数的调用可以写到任何位置==
  + 匿名函数

+ 匿名函数

  没有名字的函数，无法直接使用

  使用方式：

  + ==函数表达式：必须先声明 表达式 后调用==

    ``` js
            let fun = function () {
                console.log('我是函数表达式');
            }
            fun()
    ```

    

  + 立即执行函数

#### 6.1 函数表达式

将函数赋值给一个变量，并且通过变量名称进行调用，我们称这个为 函数表达式

==函数表达式必须先声明 后调用==

语法：

``` js
let fun = function () {
  console.log('我是函数表达式');
}
fun()
```

#### 6.2 立即执行函数

场景介绍： 避免全局变量之间的污染

==立即执行函数必须加分号==

> 第一种写法
>
> 写法 先写 ()()   ==小括号调用相当于==  所以里面的是实参
>
> 再写 (function(){
>
> })()

``` js
(function () {
  console.log(11);
}());

(function (x, y) {
  console.log(x + y);
})(1, 2);
```



> 第二种写法
> 先写()
>
> 再写（function(){
>
> }()）

``` js
 (function (x, y) {
   console.log(x + y);
 }(1, 2));

(function () {
  console.log(11);
}());
```



语法：

``` js
//方式1
(function(){conlose.log(11)})()
//方式2
(function(){conlose.log(11)}())

//不要调用立即执行
```

### 7.逻辑中断

#### 7.1 逻辑运算符里的短路

+ 短路：只存在于&& 和 ||中，当满足一定条件会让右边代码不执行

| 符号 | 短路条件                                                    |
| ---- | ----------------------------------------------------------- |
| &&   | 左边为False就短路    一假则假  如果第一个为真则返回第二个值 |
| \|\| | 左边为true就短路    一真则真  如果为假 则输出后面的         |

+ 原因：通过左边能得到整个式子的结果，因此没必要判断右边
+ &&

``` js
let age = 18
console.log(false && age++); //age++ 不执行 一假则假  不用看后面
console.log(age);

console.log(11 && 22);//如果都是真 则返回最后一个真值
```

+ ||

``` js
let age = 18
console.log(true || age++);//一真则真不用看后面
console.log(age);

console.log(false || 11) //第一个为假 输出 第二个
```







### 转换为Boolean型                    

显示转换

1. ==boolean(内容==)

   ​	记忆： ''、0、undefined、null、false、NaN、转换为布尔值后都是false 其余则为true
   
   ``` js
   console.log(false && 20);     //false
   console.log(5 < 3 && 20);       //false
   console.log(undefined && 20);   //underfined
   console.log(null && 20);    //null
   console.log(0 && 20);       //0
   console.log(10 && 20);      //20
   ```

隐式转换：

1. 有字符串的加法" "+1  结果是 “1”
2. 减法- （像大多数数学运算符一样）只能用于数字，它会使空字符串“” 转换为0
3. null 经过数字转换之后变为0
4. undefined 经过数字转换之后变为 NaN