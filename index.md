
### 四兄弟的背景
 
 在一个名为`编程语言`的村庄里，有不同姓氏的村民。例如`Java`、`Python`、`Golang`、`JavaScript`等姓氏，而接下来要介绍的就是`JavaScript`这个姓氏的一些故事。
   
我们先介绍这个姓氏里的四个兄弟： `var兄`、`function兄`、 `let兄`、 `const兄`。这四个兄弟能做的事情居然都有点相似，不知是否是村长的蓄意安排。不过让人欣慰的是，村长安排的时候考虑的还是很周到的，他们又有各自的特(脾)长(气)。都挺能装的！各自拥有一个带密码锁的背包，可以帮忙担点东西，总体来说都挺能干的，毕竟刚刚说了，挺能装~
   
### 四兄弟的特点

我们通过一个表格来看下他们各自的特点：
   
| 特征字符 | 英文名 | 中文名 | 特点 |
| --- | --- | --- | --- |
| `var` | `Var Javascript`| 鸡娃 | 好显摆，装东西之后，某种情况下还要把密码告诉房东： `window`，而且上锁之后可以打开更改里面的内容，也不知道这个锁到底能起到什么作用| 
| `function` | `Function Javascript` | 鸡法 | 装的东西很不一般，一对()一对{}，而且只能装这种。这东西就跟魔法一样，可以做好些事情。爆个小料：只要鸡娃在鸡法的领域内显摆，都能安排的明明白白，专治鸡娃的显摆|
| `let` | `Let Javascript` | 鸡栏 | 鸡栏比起前面两位，年龄偏小。他不喜欢显摆。而且装了东西就好像一个围栏，只在围栏内生效，好多JavaScript程序猿很喜欢他 |
| `const` | `Const Javascript` | 鸡坑 | 和鸡栏都出生于2015年，也有围栏的效果，这货装东西，就像往坑里扔石头，扔完就没法再扔其他东西了，再扔就发脾气|

 
 ### 四兄弟故事
 
 ```javascript
 
 window.writeWhen  -> undefined
 window.writeWho   -> undefined
 window.writeWhere -> undefined
 window.writeHow -> undefined
 window说 '你在我这找啥？我这没有你要的这些，滚一边去'
 var writeWhen = '2022-03-20 22:50:30';  -> '2022-03-20 22:50:30'
 //【画外音】 鸡娃装了个标识为writeWhen的内容，结果他显摆的毛病又犯了，让房东知道了
 
 function writeHow() {
   // 发挥魔法的地方
 }
 //【画外音】 鸡法的背包装了个魔法
 
 let writeWhen = '2022-03-20' -> SyntaxError: writeWhen has been declared
 鸡栏说：'what? 谁已经装过这个writeWhen了？看来我得换一个了'
 
 const writeHow = 'function' -> SyntaxError: writeHow has been declared
 鸡坑说：'哎哟！这都有人装过了？栏哥，咱们可别再装其他兄弟或者咱们已经装过的了'
 
 鸡栏说：'好嘞，鸡娃、鸡法，我和鸡坑装过的你们也不要装了'
 
 鸡娃、鸡法说： '了解，我们也不想看见SynctaxError，继续工作'
 //【画外音】他们达成了一致，只要被鸡栏和鸡坑装过的，兄弟四个都无法再次装入(declare)，且过程不可逆
 
 let writeWho = '简言之' -> '简言之'
 //【画外音】 鸡栏这个围栏已经造好了
 
 const writeWhere = 'juejin' -> 'juejin'
 //【画外音】 鸡娃装了个标识为writeWhen的内容，结果他显摆的毛病又犯了，让房东知道了
 
 window.writeWhen -> '2022-03-20 22:50:30'
 window.writeWho   -> undefined
 window.writeWhere -> undefined
 window.writeHow -> undefined
 window说 '嘿嘿，鸡娃爱显摆，他那的情况我知道，其他三兄弟的我就无能为力咯'
 
 function writeHow () {
     console.log(curTime, writeWho);
     var curTime = '2022-03-22 23:10';
     const writeWho = 'name'; 
     console.log(writeWho);
     return 'write with story';
 }
 //【画外音】 我们重新定义了writeHow，并定制了魔法
 
 writeHow(); -> log[undefined, '简言之'] log('name') 'write with story'
 //【画外音】 鸡法定义的这个writeHow施展了个魔法，就打印了2行结果并有了返回值，
 // 这就是鸡法的独特之处
 第一行： 打印curTime和writeWho，鸡娃声明的命名空间会在预检阶段有变量提升过程，
 即使此时未赋值，也可以访问到变量，并不会抛出异常。writeWho由于有作用域链的存在
 在writeHow所在的区域内找到了writeWho，返回了结果。所以打印了[undefined, '简言之']
 
 第二三行：以不同的方式定义了curTime和writeWho变量并赋值
 
 第四行：打印writeWho，第三行重新定义了writeWho，由于const有“围栏”的特点，所以此时的
 writeWho成为了writeHow的私有变量，与外界同名变量再无关联。所以打印了'name'
 
 第五行： 函数返回值为'write with story'
 
 ```
 ### 结语
 1. 都是定义变量的方式，`function`只能定义函数，而`let`、`const`和`var`可以定义函数和普通变量
 2. 被`const`定义过的变量`无法再次直接赋值`，`const`只用来定义`常量`，值不会发生变化的量
 3. `var`在全局下定义的变量会映射到`window`下
 4. `var`和`function`可以把`已经定义的同一变量反复定义赋值`，但是只要被`let`和`const`声明过，则无法`再次定义`
 
 
 
 
 
*以上内容均为非严格模式*
