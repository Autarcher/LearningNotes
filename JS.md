## 1.JS组成部分

![image-20240716142744891](C:\Users\廖一奥\AppData\Roaming\Typora\typora-user-images\image-20240716142744891.png)

#### 1. BOM

**BOM**（Browser Object Model，浏览器对象模型）是指浏览器提供的一组对象，用于与浏览器窗口进行交互。BOM没有标准，但通常包括以下几个主要对象：

- **window**：表示浏览器窗口，顶级对象。
- **navigator**：提供浏览器信息，例如用户代理、平台等。
- **screen**：提供屏幕分辨率和颜色深度等信息。
- **location**：表示当前URL的信息，可以用于重定向。
- **history**：表示浏览器的历史记录，可以用于在历史记录中前进或后退。

#### 2. ECMA核心（ **European Computer Manufacturers Association**）

**ECMA核心**指的是ECMAScript的核心部分。ECMAScript是由ECMA国际（欧洲计算机制造商协会）标准化的脚本语言规范，常见的实现包括JavaScript和JScript。ECMAScript核心规范定义了以下内容：

- **语法**：语言的语法规则。
- **类型**：数据类型及其行为。
- **对象**：内置对象及其属性和方法。
- **操作符**：操作符及其操作数。
- **语句**：控制流语句、声明语句等。
- **函数**：函数定义、调用及其行为。

#### 3. DOM

**DOM**（Document Object Model，文档对象模型）是HTML和XML文档的编程接口。它提供了一种表示文档的结构化方式，并定义了如何访问和操作文档的内容和结构。DOM使得程序和脚本能够动态地访问和更新文档的内容、结构和样式。

### 小结

- **BOM**：浏览器对象模型，包含一组与浏览器窗口交互的对象。
- **ECMA核心**：ECMAScript标准的核心部分，定义了脚本语言的语法、类型、对象、操作符、语句和函数。
- **DOM全称**：Document Object Model（文档对象模型），用于表示和操作HTML和XML文档的编程接口。

## 2.JS变量声明

JS中变量是弱变量更具赋值确定变量类型

通常有`var`和`let`两种声明方式

`var` 声明的变量是函数作用域（function-scoped）的，意思是在函数内部声明的变量在函数内的任何地方都能访问到，即使在声明之前也是如此

`let` 声明的变量是块作用域（block-scoped）的，意思是在花括号 `{}` 内声明的变量只能在这个块内访问。

eg:

``````javascript
function testVar() {
    if (true) {
        var x = 1;
    }
    console.log(x); // 1
}

function testLet() {
    if (true) {
        let y = 1;
    }
    console.log(y); // ReferenceError: y is not defined
}
testVar();
testLet();

``````

## 3.JavaScript和JAVA的区别

### 1. 数组

JS中数组定义为[]

eg

``````javascript
var arr = ["lisi", 11,false];
``````



JAVA中为

```java
List arr =  Arrays.asList("lisi","ll");
//List 是一个不可变长的数组
String[] arrs = {"lya","ll"};
```

### 2. 函数的重载

JS中函数没有重载只运行最后一个

eg

```javascript
<script>
       function ttest(){
        console.log("ttest");
       }
       function ttest(elem){
        console.log("ttest+elem");
       }
       function ttest(elem1,elem2){
        console.log("ttest+elem1+elem2");
       }
       ttest();
       ttest(1);
       ttest(1,2);
        //这三个个ttest都只会运行
        /*
               function ttest(elem1,elem2){
        console.log("ttest+elem1+elem2");
       }
       这个函数
        */
</script>
```

JAVA中有函数的重载

```JAVA
public class OverloadExample {

    // 无参数的方法
    public void display() {
        System.out.println("显示无参数的方法");
    }

    // 一个参数的方法
    public void display(int a) {
        System.out.println("显示一个参数的方法，参数值为: " + a);
    }

    // 两个参数的方法
    public void display(int a, int b) {
        System.out.println("显示两个参数的方法，参数值为: " + a + " 和 " + b);
    }

    // 参数类型不同的方法
    public void display(String message) {
        System.out.println("显示一个字符串参数的方法，参数值为: " + message);
    }

    public static void main(String[] args) {
        OverloadExample obj = new OverloadExample();

        // 调用无参数的方法
        obj.display();

        // 调用一个参数的方法
        obj.display(10);

        // 调用两个参数的方法
        obj.display(10, 20);

        // 调用参数类型不同的方法
        obj.display("Hello, Java Overloading!");
    }
}

```

## 4.HTML中元素id重复会发生什么？

在HTML中，如果元素的`id`属性重复，会出现以下几个问题：

1. **唯一性要求：** `id`属性应该是唯一的，用于标识HTML文档中的单个元素。如果多个元素具有相同的`id`，就违反了HTML规范。

2. **JavaScript访问：** 使用JavaScript通过`getElementById`方法访问元素时，只会返回文档中具有该`id`的第一个元素。这意味着其他具有相同`id`的元素将无法通过这种方式被访问。

    ```javascript
    var element = document.getElementById("duplicateId");
    ```

    在上述代码中，如果有多个元素具有`id="duplicateId"`，`element`变量只会引用第一个这样的元素。

3. **样式应用：** CSS中，使用`#id`选择器应用样式时，也只会应用于第一个具有该`id`的元素。其他具有相同`id`的元素不会受到影响。

    ```css
    #duplicateId {
        color: red;
    }
    ```

4. **可访问性和SEO：** 重复的`id`可能会影响网页的可访问性和搜索引擎优化（SEO），因为某些辅助技术和搜索引擎依赖于唯一的`id`来正确解析和理解网页内容。

因此，应该避免在HTML文档中使用重复的`id`属性。如果需要在多个元素上应用相同的样式或行为，可以使用`class`属性。
