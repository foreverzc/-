## 对象

### 一. 什么是对象

+ 对象（object）：JavaScript里的一种数据类型

+ 可以理解为一种无序的数据集合，注意数组是有序的数据集合

+ 用来描述一个人 一个事物

+ null 叫空对象

  + 人有姓名、年龄、性别等信息、还有吃饭睡觉打代码等功能
  + 如果用过多个变量保存比较散 用对象比较统一

  ``` js
  let obj={
   uname:'pink老师',
   age:18,
   gender:'女'
  }
  ```

  

### 二、对象使用

+ 1. 对象声明语法

  ``` js
  let 对象名 = {}
  let 对象名 = new Object() 
  ```

+ 2. 对象有属性和方法组成

  + 属性：信息叫特征（名词）。比如手机尺寸、颜色、重量等...

  + 方法：功能或行为（动词）。比如手机打电话，发短信、玩游戏...

  + ``` js
    let 对象名 = {
    		属性名：属性值，
    		方法名：函数
    }
    ```

+ 3. 属性

  + 数据描述性的信息称为属性，如人的姓名、身高、年龄、性别等，一般是名词性的

  + ``` js
    let obj={
     uname:'pink老师',
     age:18,
     gender:'女'
    }
    ```

    + 属性都是成对出现的，包括属性姓名和值，它们之间使用英文：分割
    + 多个属性之间使用英文 ， 分割
    + 属性就是依附在对象上的变量（外面是变量，对象内是属性）
    + 属性名可以使用 “ ” 或 ‘ ’， 一般情况下 省略不写，除非遇到 特殊符号  如空格、中横线等

### 三、对象的增删改查

+ 对象本质是无序的数据集合，操作数据无非就是增 删 改 查

+ 查： 查询对象

  + 声明对象，并添加了若干属性之后，可以使用，获得对象中属性对应的值，我称之为属性访问

  + ==语法：对象名.属性 （对象的属性）==   ==对象名['对象属性']==

  + 简单理解就是获得对象里面的属性值。

  + ``` js
    let obj={
     uname:'pink老师',
     age:18,
     gender:'女'
      'uname-xiaomi':'xiaomi'
    }
    console.log(obj.age)
    
    console.log(obj['uname-xiaomi'])//一般都用这种
    ```

+ 改：改变属性

  + ==语法：对象名.属性 = 新值==

  + ``` js
            let obj = {
                uname: 'pink老师',
                age: 18,
                gender: '女'
            }
            console.log(obj.age);//18
            obj.age = 19
            console.log(obj.age);//19
    ```

+ 增：增加属性和属性值

  + ==语法：对象名.新属性 = 新值==

  + ``` js
            let obj = {
              uname: 'pink老师',
              age: 18,
              gender: '女'
            }
            obj.hoobby = '跳'
            console.log(obj.hoobby);
    ```

+ 删：删除属性

  + ==语法：delete 对象名.属性==

  + ``` js
    
            let obj = {
            uname: 'pink老师',
            age: 18,
            gender: '女'
            }
            obj.hoobby = '跳'
            console.log(obj.hoobby);
          				delete obj.hoobby
    ```

    



### 四、对象中的方法

+ 数据行为性的信息称为方法，如跑步、唱歌等，一般是动词型的==本质是函数==

  ``` js
  let person = {
  	name:'andy',
  	sayHi:function(){
  			document.write('hi~')
  	}
  }
  ```

+ 1. 方法是由方法名和函数两部分构成，他们之间使用：分隔

+ 2. ==多个属性之间 用， 分隔==

+ 3. 方法是依附在对象中的函数

+ 4. 方法名可以使用 “ ” 或‘’，一般情况下省略，除非名称遇到特殊符号如空格、中横线等

+ 5. ==在对象外面的是函数 在对象里面的是方法==





### 五、遍历对象

+ 对象里面是无序的键值对  不能用索引号 来遍历了

+ 遍历对象基本语法

+ 当遍历属性时  console.log(k);  打印出来的是 ==字符串==所以 只能用  ==console.log(obj[k]); 第二种方式 来打印==

  ``` js
          let obj = {
              uname: 'andy',
              age: 18,
              sex: '男'
          }
          for (let k in obj) {
              console.log(k);
              console.log(obj[k]);
          }
  ```

+ 可以 一步一步来验证

  + ==当k遍历时  遍历的是 字符串类型的 属性名  'uname'==
  + ==所以 k = 'uname'==
  + ==所以只能使用 obj[k]  来 输出属性值==

  ``` js
          let obj = {
              uname: 'andy',
              age: 18,
              sex: '男'
          }
          for (let k in obj) {
              console.log(k);
              console.log(obj.k);
              // 相当于
              // console.log(obj.'uname');  //错误的
              // 相当于 k='uname'
              // 所以只能用 console.log(obj[k]);
              console.log(obj[k]);
          }
  ```

  

### 六、内置对象

+ 内置对象是什么
+ JavaScript内部提供的对象，包含各种属性和方法给开发者调用
+ 思考：我们之前用过内置对象吗？
  + null 空对象
  + document.write()
  + console.log()

#### 6.1 内置对象-Math

+ 介绍：Math对象是JavaScript提供的一个“数学”对象
+ 作用：提供了一系列做数学运算的方法
+ Math对象包含的方法有：
  + random：生成0-1之间的随机数（包含0不包括1）、
  + ==cell：向上取整==
  + ==floor：向下取整==
  + max：找最大数
  + min：找最小数
  + pow：幂运算
  + abs：绝对值

#### 6.2 内置对象-生成任意范围随机数

+ Math.random()随机函数，返回一个0-1之间，并且包括0不包括1的随机小数[0,1)

+ 如何生成0-10的随机数?

  + ``` js
    console.log(Math.floor(Math.random() * 11));0-10
    console.log(Math.floor(Math.random() * 3)); 0-2
    ```

+ 如何生成5-10的随机数

  + ``` js
    console.log(Math.floor(Math.random() * (5 + 1)) + 5); [5,10]
    ```

+ 如何生成N-M之间的随机数

  + ``` js
    console.log(Math.floor(Math.random() * (M - N + 1)) + N);   
    ```








### 七、拓展

简单类型又叫基本数据类型 或者值类型 ，复杂类型又叫做引用类型。

+ 值类型：简单数据类型/基本数据类型，在存储变量中存储的是值得本身，因此叫做值类型
  + string、number、boolean、undefined、null
+ 引用类型：复杂数据类型，==在存储变量中存储的仅仅是地址（引用==），因此叫做引用数据类型
  + 通过new关键字创建的对象（系统对象、自定义对象），如 对象、数组、函数 Date等