# Java_三大结构
## Java的基本控制结构

### 顺序结构
在Java编程中，最基本的结构就是顺序结构。**顺序结构**指的是代码按照书写顺序，从上到下依次执行，除非遇到跳转、选择或循环等结构。顺序结构是所有程序的基础，也是默认的执行方式。

例如：
```Java
System.out.println("开始程序"); // 这行代码会先执行
System.out.println("执行代码块"); // 然后执行这一行
System.out.println("程序结束"); // 最后执行这一行
```

### 选择结构
选择结构是一种根据条件判断执行不同代码块的结构。Java中常见的选择结构包括 `if` 语句和 `switch` 语句。

#### if 单选择结构 {id="if_1"}
单选择结构是最简单的条件判断结构，根据一个条件是否成立来决定是否执行代码块。

语法：
```Java
if(条件){
    // 当条件为 true 时执行这段代码
}
```

示例：
```Java
int number = 5;
if(number > 3){
    System.out.println("数字大于3");
}
```
在这个例子中，如果 `number` 大于3，程序就会打印 "数字大于3"。

#### if 双选择结构 {id="if_2"}
双选择结构不仅在条件成立时执行代码，还会在条件不成立时执行另一段代码。

语法：
```Java
if(条件){
    // 当条件为 true 时执行这段代码
} else {
    // 当条件为 false 时执行这段代码
}
```

示例：
```Java
int number = 2;
if(number > 3){
    System.out.println("数字大于3");
} else {
    System.out.println("数字小于或等于3");
}
```
在这个例子中，程序会打印 "数字小于或等于3"。

#### if 多选择结构
如果有多个条件需要判断，使用 `if-else if` 语句。程序会从上到下依次判断条件，直到某个条件为 `true` 执行对应代码块，或者执行最后的 `else` 块。

语法：
```Java
if(条件1){
    // 条件1为 true 时执行
} else if(条件2){
    // 条件2为 true 时执行
} else if(条件n){
    // 条件n为 true 时执行
} else {
    // 当所有条件都不满足时执行
}
```

示例：
```Java
int score = 85;
if(score >= 90){
    System.out.println("优秀");
} else if(score >= 80){
    System.out.println("良好");
} else if(score >= 70){
    System.out.println("合格");
} else {
    System.out.println("不合格");
}
```
程序会根据 `score` 的值打印相应的等级。

#### 嵌套if语句 {id="if_3"}
`if` 语句是可以嵌套的，即在一个 `if` 语句内部再使用 `if` 或 `if-else` 结构。当逻辑较为复杂时，可以通过嵌套 `if` 语句处理。

语法：
```Java
if(条件1){
    if(条件2){
        // 条件1和条件2都为 true 时执行
    } else {
        // 条件1为 true 且条件2为 false 时执行
    }
} else {
    // 条件1为 false 时执行
}
```

示例：
```Java
int age = 20;
int height = 180;
if(age > 18){
    if(height > 170){
        System.out.println("成年且身高大于170cm");
    } else {
        System.out.println("成年但身高小于或等于170cm");
    }
} else {
    System.out.println("未成年");
}
```
在这个例子中，程序会检查年龄是否大于18岁，然后再检查身高是否大于170cm。根据不同的条件，程序会打印不同的结果。

#### switch 多选择结构
多选择结构还有一个实现方式：`switch` `case` 语句。  
`switch` 语句用于判断一个变量的值，并根据这个值与多个 `case` 分支的匹配情况执行对应的代码。

语法格式：
```Java
char grade = 'C';
switch (grade) {
    case 'A':
        System.out.println("优秀");
        break;
    case 'B':
        System.out.println("良好");
        break;
    case 'C':
        System.out.println("及格");
        break;
    case 'D':
        System.out.println("不及格");
        break;
    default:
        System.out.println("输入错误");
}
```
- `break` 的作用：中止当前 `case` 分支的执行，防止程序执行下一个 `case` 语句，也就是防止“穿透”。如果没有 `break`，程序会继续执行下一个 `case`，即使它不满足条件。
- `default` 的作用：当所有 `case` 分支都不匹配时，执行 `default` 代码块，类似于 `else` 语句。

**额外提示**：
- 从JDK 7开始，`switch` 语句支持 `String` 类型的变量，这使得在处理字符串时更加方便。

---

### 循环结构

#### while 循环
`while` 循环是Java中最基本的循环结构之一，用于在布尔表达式为 `true` 的情况下反复执行代码块。

语法格式：
```java
while(布尔表达式){
    // 循环体
}
```
只要布尔表达式的结果为 `true`，循环体就会被反复执行。因此，通常需要在循环体内修改控制条件以避免无限循环。

```java
// 示例：计算1到100的和
int i = 0;
int sum = 0;
while (i <= 100) {
    sum += i;
    i++;
}
System.out.println(sum);  // 输出：5050
```

**死循环**：`while (true)` 表示一个永远不会结束的循环，通常在某些情况下会用到，例如：
```java
while (true) {
    // 这是一种死循环，通常用于：
    // 1. 等待客户端连接
    // 2. 定期检查任务
    // 但要避免在正常开发中使用这种循环，因为它会导致程序无法结束。
    break; // 可以使用 break 语句来终止死循环
}
```

---

#### do-while 循环
`do-while` 循环与 `while` 循环的区别在于，它会**先执行一次循环体**，然后再判断条件是否成立。即使条件为 `false`，循环体也会至少执行一次。

语法格式：
```java
do {
    // 循环体
} while(布尔表达式);
```

---

### For 循环
`for` 循环是Java中最常用的循环结构之一，因为它结构紧凑、可读性强，特别适合在已知循环次数的情况下使用。

语法格式：
```java
for(初始化; 布尔表达式; 迭代) {
    // 循环体
}
```

以下是 `while` 循环和 `for` 循环的等效例子：
```java
// while 循环
int a = 1;
while (a <= 100) {
    System.out.println(a);
    a += 5;  // 迭代
}
System.out.println("while 循环结束");

// for 循环
for (int i = 1; i <= 100; i += 5) {
    System.out.println(i);
}
System.out.println("for 循环结束");
```

**`for` 循环的优势**：
- 初始化部分在循环开始时只执行一次。
- 布尔表达式在每次循环前进行判断，如果为 `true`，则执行循环体；如果为 `false`，循环结束。
- 迭代部分在每次循环结束后执行，可以用来控制循环的变化。

---

### 增强for循环 {id="for_1"}
增强 `for` 循环是JDK 5引入的一种简化数组或集合遍历的方式，适用于遍历所有元素，而不需要使用索引来访问元素。

**语法格式**：
```java
for(元素类型 变量名 : 集合或数组) {
    // 循环体
}
```
在增强 `for` 循环中，**每次迭代会将数组或集合中的一个元素赋值给变量**，并执行循环体。

例如，下面的代码遍历并输出一个数组中的每个元素：
```java
public class ScannerForPRO {
    public static void main(String[] args) {
        int[] numbers = {10, 20, 30, 40, 50}; // 定义了一个数组
        for (int x : numbers) {
            System.out.println(x); // 依次输出数组中的每个元素
        }
    }
}
```

上述代码的等效传统 `for` 循环：
```java
for (int i = 0; i < numbers.length; i++) {
    System.out.println(numbers[i]);
}
```

**增强 `for` 循环的原理**：
- 它的作用类似于遍历数组中的每个元素，并将当前遍历到的元素赋值给变量 `x`。每次循环 `x` 会依次获取数组中的下一个元素。
- 增强 `for` 循环适合用于**遍历数组或集合**，而不需要关心索引或者手动控制循环。

**优点**：
- 增强 `for` 循环更加简洁易读，特别适用于只需要遍历数组或集合时。
- 省去了手动控制循环变量和索引的复杂操作。



## break 和 continue 关键词
### break
- break 在任何循环的主体部分，都可以控制循环流程。
- break 用于**强制退出循环**,不执行循环中剩余的语句
- break 也用在switch语句中

### continue
- continue 用于循环语句体中，用于**中止某次循环过程**，即跳过循环体中尚未执行的语句，接着进行下一次判断是否执行下一次循环的判定。

### goto(非java)
- goto 虽然很早就在程序设计语言中出现，尽管goto仍然是java的一个保留字，但并未在语言中得到正式使用。
- java中没有goto



