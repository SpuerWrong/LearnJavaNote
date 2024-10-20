# Java_三大结构_练习
## 题目：计算0-100之间的奇数和偶数的和
### 以下是我给出的解答1： {id="1_1"}
```java
public static void main(String[] args) {
int sumO= 0;
for(int i = 0; i%2==0 && i<=100;i++){
System.out.println(i);
sumO+=i;
}
System.out.println("偶数和为："+sumJ);
}
```
>运行结果：0
错误，错误原因：i % 2 == 0 这个条件是在每次循环时判断i是否为偶数。如果i不是偶数，循环条件会直接结束。<br>

#### 以下是CHatGPT给出的解释：
你在代码中遇到的问题是因为循环的条件和加法逻辑不太正确，导致没有真正对奇数进行求和。下面我来详细解释一下：

 代码分析:
你写的`for`循环是这样的：
```java
for(int i = 0; i <= 100 && i % 2 == 0; i++){
```
这部分有一个问题：`i % 2 == 0` 这个条件是在每次循环时判断`i`是否为偶数。如果`i`不是偶数，循环条件会直接结束，所以实际上这个循环只会执行一次（因为初始的`i=0`是偶数），后面循环就中断了。这样的话，程序只加了一个0，导致最后的结果是0。

解决方法:
要想正确计算**奇数**的和，你应该遍历0到100之间的所有数，然后只在`i`为奇数时执行加法。修改后的代码如下：

```java
public class ScannerFor01 {
    public static void main(String[] args) {
        int sumJ = 0;
        for(int i = 0; i <= 100; i++){
            if(i % 2 != 0){  // 这里判断是否为奇数
                System.out.println(i);
                sumJ += i;
            }
        }
        System.out.println("奇数和为：" + sumJ);
    }
}
```

关键点：
1. **`i % 2 != 0`**：用来判断`i`是否为奇数。如果为真，则进入循环体内进行求和。
2. **遍历 0 到 100**：循环遍历从0到100之间的所有数，但只在遇到奇数时做累加操作。

这样修改之后，程序会正确输出0到100之间的奇数和。

### 以下是我给出的正确解答2：
```java
package ScannerIO;

/**
 * @author 王丽杰
 * @date 2024/10/20
 * @className ScannerFor01
 * @package ScannerIO
 * @description 计算0-100之间的奇数和偶数的和
 */
public class ScannerFor01 {
    public static void main(String[] args) {
        int sumO = 0;
        int sumJ = 0;
        for(int i = 0; i<=100 ;i++){
            if(i%2==0) {
                System.out.println(i);
                sumO += i;
            }

        }
        System.out.println("偶数和为："+sumO);
        for(int i = 0; i<=100;i++){
            if(i%2!=0){
                System.out.println(i);
                sumJ +=i;
            }

        }
        System.out.println("奇数和为："+sumJ);
    }
}

```

### 方法 1：for循环（优化版，只遍历奇数）
```java
public class OddSum {
public static void main(String[] args) {
int sumJ = 0;
for (int i = 1; i <= 100; i += 2) { // 每次递增2，直接跳到下一个奇数
sumJ += i;
}
System.out.println("奇数和为：" + sumJ);
}
}
```
解释：我们直接从1开始，每次递增2，这样就只遍历奇数，效率更高。

### 方法 2：while循环
```Java
public class OddSum {
public static void main(String[] args) {
int sumJ = 0;
int i = 1;
while (i <= 100) {
sumJ += i;
i += 2;  // 每次递增2，直接跳到下一个奇数
}
System.out.println("奇数和为：" + sumJ);
}
}
```
解释：while循环通过手动控制变量i的递增，每次加2，遍历奇数并计算和。

### 方法 3：do-while循环
```java
public class OddSum {
public static void main(String[] args) {
int sumJ = 0;
int i = 1;
do {
sumJ += i;
i += 2;
} while (i <= 100);
System.out.println("奇数和为：" + sumJ);
}
}
```
解释：do-while循环与while类似，只不过它会先执行一次循环体内的语句，再进行条件判断。适合当你希望至少执行一次循环时使用。

### 方法 4：Stream API (Java 8 及以上)
```java
import java.util.stream.IntStream;

public class OddSum {
public static void main(String[] args) {
int sumJ = IntStream.rangeClosed(0, 100)
.filter(i -> i % 2 != 0)  // 过滤奇数
.sum();
System.out.println("奇数和为：" + sumJ);
}
}
```
解释：使用 Java 8 引入的Stream API，通过rangeClosed生成一个从0到100的数列，使用filter过滤出奇数，然后调用sum()进行求和。这种方式非常简洁。

### 方法 5：递归
```java
public class OddSum {
public static void main(String[] args) {
int sumJ = sumOdd(1, 100);
System.out.println("奇数和为：" + sumJ);
}

    public static int sumOdd(int start, int end) {
        if (start > end) {
            return 0;
        }
        return start + sumOdd(start + 2, end);  // 每次递增2，递归处理奇数
    }
}
```
解释：使用递归的方式，从1开始，每次递增2直到到达100。递归方法优雅但可能效率不如循环，特别是在大规模数据时。

### 方法 6：数学公式法
```Java
public class OddSum {
public static void main(String[] args) {
int n = (100 - 1) / 2 + 1;  // 奇数的个数
int sumJ = n * n;  // 奇数和公式：n^2
System.out.println("奇数和为：" + sumJ);
}
}
```
解释：0到100之间的奇数为1, 3, 5, ..., 99，这是一个等差数列，首项为1，公差为2，项数为50。根据等差数列的求和公式，奇数和为前50项平方，即n^2。

## 题目2：用while或for循环输出1-1000之间能被5整除的数，并以每行输出3个的形式输出
### 我的错误解法1：
```java
package ScannerIO;

/**
 * @author 王丽杰
 * @date 2024/10/20
 * @className ScannerFor02
 * @package ScannerIO
 * @description 用while或for循环输出1-1000之间能被5整除的数，并以每行输出3个的形式输出
 */
public class ScannerFor02 {
    public static void main(String[] args) {
        for(int i = 1 ; i<=1000 ; i++){
            if(i%5==0){
                for(int j =1; j<=3; j++){
                    System.out.print(i+"  ");
                    
                }
                System.out.println();

            }
        }
    }
}

```
#### ChatGPT讲解： {id="chatgpt_1"}
### 题目分析

题目的要求是：输出1到1000之间能被5整除的数，并且每行输出3个。

你使用了 `for` 循环和 `if` 语句来筛选1到1000之间能被5整除的数，并且尝试用嵌套的循环输出每行3个数。这个思路是正确的，但你在实现细节上出现了一些问题，导致程序的输出不符合题目的要求。

### 代码分析及错误解释

```java
public class ScannerFor02 {
    public static void main(String[] args) {
        for(int i = 1 ; i <= 1000 ; i++){ // 遍历1到1000的每一个数
            if(i % 5 == 0){ // 检查这个数是否能被5整除
                for(int j = 1; j <= 3; j++){ // 这里的问题出在嵌套的循环
                    System.out.print(i + "  "); // 打印3次相同的数
                }
                System.out.println(); // 换行
            }
        }
    }
}
```

#### 错误解释
1. **重复打印相同的数字**：
    - 你嵌套了一个 `for` 循环，在筛选出能被5整除的数后，使用 `j` 进行第二次循环。这个内部循环每次都会打印 `i` 这个数，而不是你想要的不同的三个数。因此，你的代码每次打印3个相同的数字，而不是3个不同的数字。

   举个例子：假设 `i=5` 时，满足 `i % 5 == 0`，内层的 `for` 循环会运行3次，所以输出会是：
   ```
   5  5  5  
   ```
   但你真正想要的效果是：
   ```
   5  10  15  
   ```

2. **每行输出3个的逻辑错误**：
    - 题目的要求是每行输出3个数，而你是每找到一个能被5整除的数，直接重复打印3次。因此，需要修改程序的逻辑，不是每个数都打印3次，而是把符合条件的数按顺序排列，每3个数为一行。

### 正确的实现思路
要解决这个问题，你需要：
1. **遍历1到1000之间的数字**，筛选出能被5整除的数字。
2. **计数**每行已经打印了多少个数，当计数达到3时就换行。

### 正确代码

```java
public class ScannerFor02 {
    public static void main(String[] args) {
        int count = 0; // 用于计数每行已经输出的数字个数
        for(int i = 1 ; i <= 1000 ; i++){ // 遍历1到1000的每个数
            if(i % 5 == 0){ // 判断数是否能被5整除
                System.out.print(i + "  "); // 输出这个数
                count++; // 每输出一个数，计数器加1

                if(count % 3 == 0){ // 如果已经输出了3个数，就换行
                    System.out.println();
                }
            }
        }
    }
}
```

### 解释
1. **计数变量`count`**：这个变量用于跟踪每行已经输出的数字个数。
    - 每找到一个能被5整除的数并输出后，`count` 加1。
    - 当 `count` 的值能被3整除时，说明已经输出了3个数字，所以调用 `System.out.println()` 换行。

2. **逻辑变化**：内层循环被去除，只需要一个 `if` 语句控制是否换行，不再重复输出相同的数字。

### 输出效果
最终的输出效果是每行输出3个能被5整除的数字，类似：
```
5  10  15  
20  25  30  
35  40  45  
...
```

这个代码更符合题目的要求，并且实现了正确的每行输出3个数的功能。

### 最后我写的正确代码：
```Java
package ScannerIO;

/**
 * @author 王丽杰
 * @date 2024/10/20
 * @className ScannerFor02
 * @package ScannerIO
 * @description 用while或for循环输出1-1000之间能被5整除的数，并以每行输出3个的形式输出
 */
public class ScannerFor02 {
    public static void main(String[] args) {
        int con=0;
        for(int i = 1 ; i<=1000 ; i++){
            if(i%5==0){
                    System.out.print(i+"  ");
                    con++;
                }
            if(con==3){
                System.out.println();
                con = 0;
            }


        }
    }
}

```

## 题目3：打印九九乘法表
### 我一次写的正确代码：
```java
package ScannerIO;

/**
 * @author 王丽杰
 * @date 2024/10/20
 * @className ScannerFor03
 * @package ScannerIO
 * @description 打印九九乘法表
 */
public class ScannerFor03 {
    public static void main(String[] args) {
        for(int i = 1 ; i < 10;i++){
            for(int j = 1;j<=i; j++){
                System.out.print(j+"*"+i+"="+i*j+"  ");
            }
            System.out.println();
        }
    }
}

```