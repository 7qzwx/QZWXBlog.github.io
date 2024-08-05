# kotlin学习

## 基础篇

- 
![Clip_2024-08-04_13-59-45-1722751250661-2](https://github.com/user-attachments/assets/1632c57a-6f93-42ac-8b82-bdb9573235ca)

- 程序入口
- 注释：
  普通注释直接//即可，多行注释只需要 `/*` +`回车` 即可。



#### 1.变量与基础类型

##### 变量

可变变量：var                         不可变量：val（一但定义值后就不可修改）

```kotlin
fun main() {
   var X :int=7
    println(X)
}
```

##### 数字类型

- 整数默认使用  Int  ，非常大的整数可以用  Long；

- 小数默认使用 double ，如果用  float 需要后面加 f，如：

  ```kotlin
  val e = 2.7182818284 // Double类型的数值
  val e: Float = 2.7182818284f // 这里表示为Float会导致精度折损，得到2.7182817
  ```

- a++跟++a的联系与区别：

​		比如 a=10, 运算的结果都是11，但是区别如下：

```kotlin
fun main() {
    var a = 10
    println(a++)   //这里++在后面，打印a的值依然是10，但是结束之后a的值就变成11了
    println(++a)   //这里++在前面，打印a的值是这里先自增之后的结果，就是12了
}
```

- 布尔类型：

  布尔类型（boolean）：`true` 或者  `false`        

  如：     【打印结果为false     true   true】

  ```kotlin
  fun main() {
      val a = 10
      val b = 8
      println(a == b)  //判断a是否等于b（注意等号要写两个，因为单等号为赋值运算）
      println(a >= b)   //判断a是否大于等于b
    	val c: Boolean = a != b   //判断a是否不等于b并将结果赋值给变量c
      println（c）
  }
  ```

  我们为了快速判断某个数是否在一个区间内，可以直接使用 `a..b` 来表示一个数学上`[a, b]`这样的闭区间,如：   【打印结果为true】

  ```kotlin
  fun main() {
      var a=10
      println(a in 1..20)
  }
  ```

  拥有逻辑运算符：

  - `||`– 逻辑或运算：“或者”  如A||B表示A或者B
  - `&&`– 逻辑与运算：“并且”  如A&&B表示A并且B
  - `!`– 取反运算

  ```kotlin
  fun main() {
      val a = 10
      val b = 0
      println(100 >= a && b >= 60)  //我们可以使用与运算符连接两个判断表达式，只有两边都为true结果才是true
      println(100 >= a || b >= 60)  //我们可以使用或运算符连接两个判断表达式，只要两边任意一个为true结果就是true
  }
  ```

  取反！如下

  ```kotlin
  fun main() {
      val a = 10
      val b = 20
      val c = a > b   //这里很明显c应该为false
      println(!c)   //这里进行了取反操作并打印，那么结果就是true了
  }
  ```

##### 字符类型

- 单字符 char  ：可以打印单个字符，如 ‘Q’  ‘,’  ‘2’ 等；

  打印符号：（推荐直接写符号）
![ugem2scKxyX7wJL-1722757750442-5](https://github.com/user-attachments/assets/8a4a9a7c-327f-4245-a2e7-ed6f34204d4e)


```kotlin
fun main() {
    val d = '★'    //可以直接打符号进去！
    val c = '\u2713'   //符号✓对应的Unicode编码为10003，这里需要转换为16进制表示，结果为0x2713
    println(c)
}
```

- 字符串  string    ：可以打印一句话等

​		转义类型：

​		`\n` – 换行（LF）

​		`\t` – 选项卡

​		`\b` – 退格

​		`\r` – 回车（CR）

​		`\'` – 单引号

​		`\"` – 双引号

​		`\\` –反斜杠

​		`\$` – 美元符号

使用：

```kotlin
fun main() {
   var tex ="你好\n" +"这里开始"
   println(tex)
}
```

打印结果：
![Clip_2024-08-04_15-58-47-1722758331756-8](https://github.com/user-attachments/assets/c7c4c5e0-6651-4501-b814-d5dfaa4fa86e)

如果要打印多行文字，用“”“  文本  ”“”，但是转义符号无效（即不能用换行符号）

```kotlin
fun main() {
   var tex ="""
      你好！
      这里是七种文学！
      我在测试\n多行文字
   """
   println(tex)
}
```

打印结果：
![Clip_2024-08-04_16-02-28-1722758553432-11](https://github.com/user-attachments/assets/f06682f4-614b-4a07-85d4-9dce4c19982a)


也可以这样使用：

```kotlin
fun main() {
   val a = 10
   val text1 = "这是拼接的值$a"  //这里的$为模版表达式，可以直接将后面跟着的变量或表达式以字符串形式替换到这个位置
   val text2 = "$a 这是拼接的值" //注意这里$a之后必须空格，否则会把后面的整个字符串认为这个变量的名字
   println(text1)
   println(text2)
}
```



#### 2.逻辑语句

##### IF语句

简单嵌套：

```kotlin
fun main() {
    val score = 12
    if (score < 60) {   //先判断不及格
        if (score > 30) //在内层再嵌套一个if语句进行进一步的判断
            println("分数在30-60之间") 
        else 
            println("分数<30")
    }
}
```

如果简单语句只有一行，可以不用  { }  包裹

```kotlin
fun main() {
    val score = 2
  	//这里判断socre是否大于60，是就得到Yes，否就得到No，并且可以直接赋值给变量
    val res = if (score > 60) "Yes" else "No"
}
```

对于多行，默认最后一行为返回值

```kotlin
fun main() {
    val score = 2
    val res = if (score > 60) {
        println("不错啊期末没挂科")
        "Yes"   //代码块默认最后一行作为返回结果
    } else {		//注意这里必须要有else作为返回值
        println("不会有人Java期末还要挂科吧")
        "No"     
    }
}
```



##### When选择语句    【相当于Switch】

基本结构：（需要考虑所有情况，否则必须有else）

```kotlin
when (目标) {
    匹配值1 -> 代码...   //我们需要传入一个目标，比如变量，或是计算表达式等
    匹配值2 -> 代码...   //如果目标的值等于我们这里给定的匹配值，那么就执行case后面的代码
    else -> {
        代码...    //如果以上条件都不满足，就进入else中（可以没有），类似于之前的if-elseif-else
    }
}
```

例子：  （打印结果为：去尖子班！准备冲刺985大学！）

```kotlin
fun main() {
    val c = 'A'
    when (c) {
        'A' -> println("去尖子班！准备冲刺985大学！")
        'B' -> println("去平行班！准备冲刺一本！")
        'C' -> println("去职高深造。")
    }
}
```



##### While循环语句

​	*for语句的简单版本*

基本结构：

```kotlin
while(循环条件) 循环体;
```

例子：（运行结果为：100  50  25  12  6  3  1）

```kotlin
fun main() {
    var i = 100 //比如现在我们想看看i不断除以2得到的结果会是什么，但是循环次数我们并不明
    while (i > 0) {   //现在唯一知道的是循环条件，只要大于0那么就可以继续除
        println(i)
        i /= 2 //每次循环都除以2
    }
}
```

也支持break打断：（运行结果为：100  50  25  12）

```kotlin
fun main() {
    var i = 100
    while (i > 0) {
        if (i < 10) break
        println(i)
        i /= 2
    }
}
```

可以先执行再判断：（运行结果为0  1   3  4  5  6  7  8  9）

```kotlin
fun main() {
    var i = 0 //比如现在我们想看看i不断除以2得到的结果会是什么，但是循环次数我们并不明确
    do {  //无论满不满足循环条件，先执行循环体里面的内容
        println(" $i ")
        i++
    } while (i < 10) //再做判断，如果判断成功，开启下一轮循环，否则结束
}
```



##### For循环语句

continue：跳过       break：终止

基本机构：

```kotlin
for (遍历出来的单个目标变量 in 可遍历目标) 循环体
```

这里的可遍历目标有很多，比如：

* 数组
* 区间
* 任何实现了运算符重载函数iterator的类

例子：

```kotlin
fun main(){
   val A=1..5
   for (i in A) println("这是第 $i 次")    //这里的println可以用 { }包裹，也可以不用，因为是单行简单语句
}   //注意这里的i 是一个局部变量，只能在for语句中有用，在main中用不了
```

运行结果：

![Clip_2024-08-04_16-36-34-1722760597070-14](https://github.com/user-attachments/assets/8459fcac-cb7a-432f-981d-e0c1cdca681c)




也可以简单嵌套：

```kotlin
fun main() {
    for (i in 0..2)  //外层循环执行3次
        for (j in 0..2)  //内层循环也执行3次
            println("外层$i，内层$j")
}
```

输出结果：

![Clip_2024-08-04_16-45-59-1722761161834-17](https://github.com/user-attachments/assets/3a58a9de-e02d-4508-8cec-13a5f445e3b0)


​	跳过某轮次continue：


```kotlin
fun main(){
for (i in 0..2) {
    if (i == 1) continue  //比如我们希望当i等于1时跳过这一轮，不执行后面的打印
    println("在这么冷的天")
    println("当前i的值为：$i")
   }
}
```

打印结果：

![Clip_2024-08-04_16-48-55-1722761339420-20](https://github.com/user-attachments/assets/6d2fb08b-8e1b-4f57-8586-f9c557dd5fcc)

提前终止break：

```kotlin
fun main() {
    for (i in 0..2) {
        if (i == 1) break //我们希望当i等于1时提前结束
        println("伞兵一号卢本伟准备就绪！")
        println("当前i的值为：$i")
    }
}
```

打印结果：

![Clip_2024-08-04_16-50-20-1722761427759-23](https://github.com/user-attachments/assets/a24286f1-2a75-44bd-8466-bf3e59911149)


可以用标记来直接作用整个地方

不用标记：

![Clip_2024-08-04_17-00-35-1722762043703-29](https://github.com/user-attachments/assets/8941218d-0ced-47be-ba8c-2b15461987f2)

用标记：

![Clip_2024-08-04_17-04-49](https://github.com/user-attachments/assets/4a6858c1-920a-452e-8297-fb2128912020)


## 中级篇

### 1.函数

> 当一些代码需要重复使用时候，可以写成一个函数，在需要用的地方插入函数即可。可理解为“组件”

- 创建函数

```kotlin
fun 函数名称([函数参数...]): 返回值类型 {
    //函数体
}
```

​	如果不需要返回值，返回值类型可以不用写（默认为unit，类似Java的void，返回值为空）；

​	

例子：（由简单到复杂）
![Clip_2024-08-04_17-35-59](https://github.com/user-attachments/assets/05daea93-550e-486f-8f92-720fb29adb99)


下面一张图片中  **A(小括号内的自定义参数)**  就是**形参**， **实际调用函数时候传入的参数   “hello”    就是**实参**。

【形参就是告诉函数你创建的函数，需要传入一个什么类型的数据；

​    实参则是调用函数时候传入的数据】

*调用有形参的函数必须填写实参，否则会报错！如果设置了形参默认值可以不写实参*

![Clip_2024-08-04_17-46-15](https://github.com/user-attachments/assets/0dd56920-1321-48aa-8ec6-985cae44268e)

![Clip_2024-08-04_18-10-13](https://github.com/user-attachments/assets/e968e39f-31c5-4e3d-880a-14a4fae6225f)

![Clip_2024-08-04_18-03-04](https://github.com/user-attachments/assets/737b854a-7343-4aef-bbe7-db3be9aebe16)

![Clip_2024-08-04_18-17-32](https://github.com/user-attachments/assets/22b159b3-7e12-4b38-93ec-3d91bb844c31)


编写同名但不同参数，叫函数的重载

![Clip_2024-08-04_18-26-33](https://github.com/user-attachments/assets/cb03276b-f2e4-492d-86a4-15429ac9cfbc)


#### 2.递归函数

> 就是函数本身调用本身函数，但是需要有终止代码
>
> 合理利用递归函数，有利于处理 循环问题

例子：

```kotlin
fun main() {
    println(test(5))  //计算0-5的和
}

//这个函数实现了计算0-n的和的功能
fun test(n: Int): Int{
    if(n <= 0) return 0  //当n等于0的时候就不再向下，而是直接返回0
    return n + test(n - 1)  //n不为0就返回当前的n加上test参数n-1的和
}
```

#### 3.高阶函数

> 正是得益于函数可以作为变量的值进行存储，因此，如果一个函数接收另一个函数作为参数，或者返回值的类型就是一个函数，那么该函数称为高阶函数。

##### 【上】

要声明函数类型，需要按照以下规则：

- 所有函数类型都有一个括号，并在括号中填写参数类型列表和一个返回类型，比如：`(A, B) -> C ` 表示一个函数类型，该类型表示接受类型`A`和`B`的两个参数并返回类型`C`的值的函数。参数类型列表可为空的，比如`() -> A`，注意，即使是`Unit`返回类型也不能省略。

我们可以像下面这样编写：

```kotlin
//典型的函数类型 (参数...) -> 类型  小括号中间是一个剪头一样的符号，然后最后是返回类型
var func0: (Int) -> Unit  //这里的 (Int) -> Unit 表示这个变量存储的是一个有一个int参数并且没有返回值的函数
var func1: (Double, Double) -> String   //同理，代表两个Double参数返回String类型的函数
```

同样的，作为函数的参数也可以像这样表示：

```kotlin
fun test(other: (Int) -> String){
}
```

函数类型的变量，我们可以将其当做一个普通的函数进行调用：

```kotlin
fun test(other: (Int) -> String){
    println(other(1))  //这里提供的函数接受一个Int参数返回string，那么我们可以像普通函数一样传入参数调用它
}
```

由于函数可以接受函数作为参数，所以说你看到这样的套娃场景也不奇怪：

```kotlin
var func: (Int) -> ((String) -> Double)
```

不过这样写可能有些时候不太优雅，我们可以为类型起别名来缩短名称：

```kotlin
typealias HelloWorld = (String) -> Double
fun main() {
    var func: HelloWorld
}
```

##### 【下】

可以使用Lambda表达式来表示一个函数实例：

```kotlin
fun main() {
    var func: (String) -> Int = {  //一个Lambda表达式只需要直接在花括号中编写函数体即可
        println("这是传入的参数$it")   //默认情况下，如果函数只有一个参数，我们可以使用it代表传入的参数
        666   //跟之前的if表达式一样，默认最后一行为返回值
    }
  	func("HelloWorld!")
}
```

是不是感觉特别简便？

<img width="746" alt="fsxB2UhpXZewk4Q" src="https://github.com/user-attachments/assets/88ee2af2-425c-49f1-9b31-dfff0328b522">


对于参数有多个的情况，我们也可以这样进行编写：

```kotlin
fun main() {
    val func: (String, String) -> Unit = { a, b ->   //我们需要手动添加两个参数这里的形参名称，不然没法用他两
        println("这是传入的参数$a, 第二个参数$b")   //直接使用上面的形参即可
    }
  	val func2: (String, String) -> Unit = { _, b ->
        println("这是传入的第二个参数$b")   //假如这里不使用第一个参数，也可以使用_下划线来表示不使用
    }
    func("Hello", "World")
}
```

<img width="823" alt="R9WjhIUinaP465p" src="https://github.com/user-attachments/assets/55b2db14-d92e-46ee-b70b-47ce47c48751">


是不是感觉玩的非常高级？还有更高级的在后面呢！

我们接着来看，如果我们现在想要调用一个高阶函数，最直接的方式就是下面这样：

```kotlin
fun main() {
    val func: (Int) -> String = { "收到的参数为$it" }
    test(func)
}

fun test(func: (Int) -> String) {
    println(func(66))
}
```

当然我们也可以直接把一个Lambda作为参数传入作为实际参数使用：

```kotlin
fun main() {
    test({ "收到的参数为$it" })
}
```

不过这样还不够简洁，在Kotlin中，如果函数的最后一个形式参数是一个函数类型，可以直接写在括号后面，就像下面这样：

```kotlin
test() { "收到的参数为$it" }
```

由于小括号里面此时没有其他参数了，还能继续省，直接把小括号也给干掉：

```kotlin
test { "收到的参数为$it" }   //干脆连小括号都省了，这语法真的绝
```

当然，如果在这之前有其他的参数，只能写成这样了：

```kotlin
fun main() {
    test(1) { "收到的参数为$it" }
}

//这里两个参数，前面还有一个int类型参数，但是同样的最后一个参数是函数类型
fun test(i: Int, func: (Int) -> String) {
    println(func(66))
}
```

这种语法也被称为 尾随lambda表达式，能省的东西都省了，不过只有在最后一个参数是函数类型的情况下才可以，如果不是最后一位，就没办法做到尾随了。

最后需要特别注意的是，在Lambda中没有办法直接使用`return`语句返回结果，而是需要用到之前我们学习流程控制时用到的标签：

```kotlin
fun main() {
    val func: (Int) -> String = test@{
        //比如这里判断到it大于10就提前返回结果
        if(it > 10) return@test "我是提前返回的结果"
        println("我是正常情况")
        "收到的参数为$it"
    }
    test(func)
}

fun test(func: (Int) -> String) {
    println(func(66))
}
```

如果是函数调用的尾随lambda表达式，默认的标签名字就是函数的名字：

```kotlin
fun main() {
    testName {  //默认使用函数名称
        if(it > 10) return@testName "我是提前返回的结果"
        println("我是正常情况")
        "收到的参数为$it"
    }
}

fun testName(func: (Int) -> String) {
    println(func(66))
}
```

不过，为什么要这么麻烦呢，还要打标签才能返回，这不多此一举么？这个问题我们会在下一节内联函数中进行讲解。



#### 4.内联函数

使用高阶函数会可能会影响运行时的性能：每个函数都是一个对象，而且函数内可以访问一些局部变量，但是这可能会在内存分配（用于函数对象和类）和虚拟调用时造成额外开销。

为了优化性能，开销可以通过内联Lambda表达式来消除。使用`inline`关键字会影响函数本身和传递给它的lambdas，它能够让方法的调用在编译时，直接替换为方法的执行代码，什么意思呢？比如下面这段代码：

```kotlin
fun main() {
    test()
}

//添加inline表示内联函数
inline fun test(){
    println("这是一个内联函数")
  	println("这是一个内联函数")
  	println("这是一个内联函数")
}
```

由于test函数是内联函数，在编译之后，会原封不动地把代码搬过去：

```kotlin
fun main() {
    println("这是一个内联函数")   //这里是test函数第一行，直接搬过来
  	println("这是一个内联函数")
  	println("这是一个内联函数")
}
```

同样的，如果是一个高阶函数，效果那就更好了：

```kotlin
fun main() {
    test { println("打印：$it") }
}

//添加inline表示内联函数
inline fun test(func: (String) -> Unit){
    println("这是一个内联函数")
    func("HelloWorld")
}
```

由于test函数是内联的高阶函数，在编译之后，不仅会原封不动地把代码搬过去，还会自动将传入的函数参数贴到调用的位置：

```kotlin
fun main() {
    println("这是一个内联函数")   //这里是test函数第一行
  	val it = "HelloWorld"  //这里是函数内传入的参数
    println("打印：$it")  //第二行是调用传入的函数，自动贴过来
}
```

内联会导致编译出来的代码变多，但是同样的换来了性能上的提升，不过这种操作仅对于高阶函数有显著效果，普通函数实际上完全没有内联的必要，也提升不了多少性能。

注意，内联函数中的函数形参，无法作为值给到变量，只能调用：

<img width="911" alt="ufLoiIyGKTbYV9H" src="https://github.com/user-attachments/assets/87482ee3-8345-4d59-bcf0-81ceee338e9d">


同样的，由于内联，导致代码被直接搬运，所以Lambda中的return语句可以不带标签，这种情况会导致直接返回：

```kotlin
fun main() {
    test { return }  //内联高阶函数的Lambda参数可以直接写return不指定标签
    println("调用上面方法之后")
}

inline fun test(func: (String) -> Unit){
    func("HelloWorld")
    println("调用内联函数之后")
}
```

上述代码的运行结果就是，直接结束，两句println都不会打印，这种情况被称为**非局部返回**。

回到上一节最后我们提出的问题，实际上，在Kotlin中Lambda表达式支持一个叫做"标签返回"（labeled return）的特性，这使得你能够从一个Lambda表达式中返回一个值给外围函数，而不是简单地返回给Lambda表达式所在的最近的封闭函数，就像下面这样：

```kotlin
fun main() {
    test { return@main }  //标签可以直接指定为外层函数名称main来提前终止整个外部函数
    println("调用上面方法之后")
}

inline fun test(func: (String) -> Unit){
    func("HelloWorld")
    println("调用内联函数之后")
}
```

效果跟上面是完全一样的，为了避免这种情况，我们也可以像之前一样将标签写为@test来防止非局部返回。

```kotlin
fun main() {
    test { return@test }  //这样就只会使test返回，而不会影响到外部函数了
    println("调用上面方法之后")
}
```

有些时候，可能一个内联的高阶函数中存在好几个函数参数，但是我们希望其中的某一个函数参数不使用内联，能够跟之前一样随意当做变量使用：

```kotlin
fun main() {
    test({ println("我是一号：$it") }, { println("我是二号：$it") })
}

//在不需要内联的函数形参上添加noinline关键字，来防止此函数的调用内联
inline fun test(func: (String) -> Unit, noinline func2: (Int) -> Unit){
    println("这是一个内联函数")
    func("HelloWorld")
  	var a = func2  //这样就不会报错，但是不会内联了
    func2(666)
}
```

最后编译出来的结果，类似于：

```kotlin
fun main() {
    println("这是一个内联函数")
    val it = "HelloWorld"
    println("打印：$it")
  	//第二个参数由于不是内联，这里依然作为Lambda使用
    val func2: (Int) -> Unit = { println("我是二号：$it") }
    func2(666)
}
```

由于目前知识的学习还不太够，函数我们只能先暂时告一段落，在后续的学习中我们会继续认识更多函数的特性。

***

### 2.类与对象

> 类是一个抽象的概念，对象是一个具体的实例，如人类与人。



#### 类的创建与使用

一般类可以单独放在一个.kt文件中，便于管理。

- ```kotlin
  //如果没有任何可见性修饰符，可以省略constructor关键字，如果类中没有其他内容，可以省去花括号{}
  class Student constructor(var name:String,var age:Int){
  
  }
  ```

- ```kotlin
  //也可以这样写，但是需要赋予初始值
  class Student (){
      var name:String="" 
      var age:Int=0
  }
  ```

- 可以这样使用：

  ```kotlin
  class Student (var name:String,var age:Int)
  fun main() {
    val stu1 = Student("马可波罗",18)
      println(stu1.name)
      println(stu1.age)
  }
  ```

- 除了直接使用主构造函数创建对象外，我们也可以添加一些次要构造函数，比如我们的学生可以只需要一个名字就能完成创建，我们可以直接在类中编写一个次要构造函数：

  ```kotlin
  class Student(var name: String, val age: Int) {
    	//这里可以使用constructor关键字继续声明次要构造函数
    	//次要构造函数中的参数仅仅是表示传入的参数，不能像主构造函数那样定义属性
    	//这里的this表示是当前这个类，this()就是调用当前类的构造函数
      constructor(name: String) : this(name, 18)
      {println("哈哈我是次要构造函数，只需要一个name值就要可以啦!")}//这里其实是调用主构造函数，并且参数只有name，年龄直接给个默认值18
  }
  //使用方法：
  fun main() {
      println(Student("马可波罗"))
  }
  ```

  * **主构造函数：** 可以直接在主构造函数中定义类属性，使用更方便，但是主构造函数只能存在一个，并且无法编写函数体，只有为类属性做初始化赋值的效果。【可以没有主构造函数！】
  * **辅助（次要）构造函数：** 可以存在多个，并且可以自定义函数体，但是无法像主构造函数那样定义类属性，并且当类具有主构造函数时，所有次要构造函数必须直接或间接地调用主构造函数。

#### 对象的初始化操作

> 在创建对象时候可以执行多个初始化操作

```kotlin
class Student(var name: String) {
    init{
        println("星光荡开宇宙，本人闪亮登场！")
    }
    init {
        println("其实后面可以添加跟过init来实现初始化操作！")

    }    }
fun main() {
   val stu1=Student("东方曜")
}
```

上面打印结果为：

```kotlin
星光荡开宇宙，本人闪亮登场！
其实后面可以添加跟过init来实现初始化操作！
```

#### 类的成员函数

在类中可以定义函数，在其他地方通过 . 调用

```kotlin
class Student(var name: String,var age: Int) {
    fun hello(){
        println("大家好！我叫$name，今年已经${age}岁了!")
    }
}
fun main() {
   val stu1=Student("李信",18)
    stu1.hello()
}   //打印结果：大家好！我叫李信，今年已经18岁了！
```

#### 可见性修饰符

- public：默认修饰符，声明的内容可以在各个地方引用；
- private：只在当前文件可访问；



### 3.封装，继承和多态

封装、继承和多态是面向对象编程的三大特性。

> * 封装，把对象的属性和函数结合成一个独立的整体，隐藏实现细节，并提供对外访问的接口。
> * 继承，从已知的一个类中派生出一个新的类，叫子类。子类实现了父类所有非私有化的属性和函数，并根据实际需求扩展出新的行为。
> * 多态，多个不同的对象对同一消息作出响应，同一消息根据不同的对象而采用各种不同的函数。

正是这三大特性，能够让我们的Kotlin程序更加生动形象。

#### 类的封装

在编写类时一般将成员变量私有化，外部类需要使用Getter和Setter函数来查看和设置变量。

好处：可以直接省略类内部中如何运算，只定义两个方法，传入数据，获取结果 。

​			外面直接传入数据就可以获取结果。
![Clip_2024-08-05_16-13-50](https://github.com/user-attachments/assets/e8f23980-1037-44b2-a4ee-326897e7fe71)



#### 类的继承

在类前面加  open   关键字表示可被继承的父类，如

```

```

