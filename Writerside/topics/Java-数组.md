# Java_数组

## 数组的定义
- **数组**是相同类型数据的有序集合。
- 数组是由若干相同类型的数据组成的，这些数据按照一定的顺序排列组合。
- 数组中的每一个数据叫做**数组元素**，每个数组元素可以通过**下标**来访问。

## 数组的声明
在使用数组之前，必须先声明数组变量。  
语法格式：

```java
dataType[] arrayRefVar;  // 推荐的声明方式
int[] nums;  // 声明一个名为 nums 的 int 类型数组

dataType arrayRefVar[];  // 也可以用这种方式，但不推荐
int nums2[];  // 与上面 nums 效果相同
```

### 数组的创建
在 Java 中，使用 `new` 操作符来创建数组。

```java
dataType[] arrayRefVar = new dataType[arraySize];
int[] nums3 = new int[10];  // 创建了一个名为 nums3 的长度为10的int数组
```

- `int[] nums3 = new int[10];` 定义了一个名为 `nums3` 的 int 类型数组，并通过 `new` 操作符为数组分配内存。这个数组可以存放 10 个整数元素，数组的索引从 `0` 到 `9`。

### 访问数组元素
数组的元素是通过**索引**访问的，索引从 `0` 开始。  
获取数组长度的语法：`array.length`。

## Java内存分析 {id="java_1"}
在 Java 中，内存主要分为三个区域：堆、栈和方法区。

### 堆（Heap）
- 存放通过 `new` 操作符创建的对象和数组。
- 堆内存是所有线程共享的，不会存放局部变量。

### 栈（Stack）
- 存放基本类型变量（包含基本类型的具体数值）。
- 存放引用对象的变量（引用的对象存放在堆中）。

### 方法区（Method Area）
- 被所有线程共享，存放类的相关信息和 `static` 变量。

## Java数组的三种初始化

1. **动态初始化**：指定数组长度，由系统自动初始化。
   ```java
   int[] nums = new int[10];  // 动态初始化，长度为10，元素自动初始化为 0
   ```
2. **静态初始化**：在定义数组时直接为每个元素赋值。
   ```java
   int[] nums = {1, 2, 3, 4, 5};  // 静态初始化
   ```
3. **默认初始化**：数组创建时，元素默认被初始化（int 类型默认为 0，引用类型默认为 `null`）。

## 数组的四个基本特点
1. **长度固定**：数组一旦被创建，大小不可改变。
2. **相同类型**：数组中的元素必须是相同类型的，不允许出现混合类型。
3. **元素类型多样**：数组中的元素可以是任何类型的数据，包括基本类型和引用类型。
4. **引用类型**：数组变量是引用类型，数组可以看作对象，数组中的每个元素相当于该对象的成员变量。数组本身在堆中分配空间。

## 多维数组
**多维数组**可以看作是数组的数组，例如二维数组是一个特殊的一维数组，其每个元素又是一个一维数组。

```java
int[][] a = new int[2][5];  // 创建了一个2行5列的二维数组
```

## 冒泡排序

冒泡排序是一种简单的排序算法，基本原理是通过比较相邻的元素来把最大的元素逐步“冒泡”到数组的末尾。

### 冒泡排序步骤：
1. 比较相邻的元素，如果前面的比后面的元素大，则交换它们。
2. 重复相邻元素的比较和交换，直到数组的末尾，此时最大的元素会被排到数组的最后。
3. 再次从头开始，继续对剩下的部分进行同样的操作。
4. 这个过程会不断重复，直到整个数组有序。

### 冒泡排序的代码实现：

```java
public int[] bubbleSort(int[] array) {
    int temp;
    boolean swapped;
    for (int i = 0; i < array.length - 1; i++) {
        swapped = false;  // 每轮开始前初始化为false
        for (int j = 0; j < array.length - 1 - i; j++) {
            if (array[j] > array[j + 1]) {  // 如果前一个元素大于后一个元素
                temp = array[j];  // 交换两者
                array[j] = array[j + 1];
                array[j + 1] = temp;
                swapped = true;  // 发生交换，标记为true
            }
        }
        if (!swapped) {  // 如果在一轮中没有发生交换，说明数组已排序完成
            break;
        }
    }
    return array;
}
```

### 冒泡排序的解释：
- 外层循环：控制排序的轮数，每轮都会把当前最大值“冒泡”到数组的尾部。
- 内层循环：比较相邻的元素并进行交换。
- `swapped` 标志：用于优化，如果某一轮没有发生交换，则说明数组已经有序，可以提前终止排序。

## 稀疏数组

### 什么是稀疏数组？
稀疏数组是指其中大多数元素都是相同值（通常是 0）的数组。与普通数组不同，稀疏数组可以通过压缩存储来节省空间，只记录非默认值的元素及其位置信息。

### 稀疏数组的使用场景：
当一个数组的大多数元素为相同的值时（例如：0），使用稀疏数组能够有效地减少空间占用，提升程序性能。

### 稀疏数组的转换过程：
1. **记录原始数组的行数、列数和非零元素的个数**。
2. **记录非零元素的位置（行和列）及其值**。
3. 将这些信息存储到一个新的稀疏数组中，原数组可以通过该稀疏数组还原。

### 稀疏数组的代码实现：
```java
public class SparseArray {
    public static void main(String[] args) {
        // 原始二维数组，0 表示没有元素，1 表示有元素
        int[][] originalArray = new int[11][11];
        originalArray[1][2] = 1;
        originalArray[2][3] = 2;
        
        // 统计非零值个数
        int nonZeroCount = 0;
        for (int i = 0; i < 11; i++) {
            for (int j = 0; j < 11; j++) {
                if (originalArray[i][j] != 0) {
                    nonZeroCount++;
                }
            }
        }

        // 创建稀疏数组
        int[][] sparseArray = new int[nonZeroCount + 1][3];
        sparseArray[0][0] = 11;  // 原数组的行数
        sparseArray[0][1] = 11;  // 原数组的列数
        sparseArray[0][2] = nonZeroCount;  // 非零元素的个数

        // 将非零值存入稀疏数组
        int count = 0;
        for (int i = 0; i < 11; i++) {
            for (int j = 0; j < 11; j++) {
                if (originalArray[i][j] != 0) {
                    count++;
                    sparseArray[count][0] = i;
                    sparseArray[count][1] = j;
                    sparseArray[count][2] = originalArray[i][j];
                }
            }
        }

        // 输出稀疏数组
        System.out.println("稀疏数组：");
        for (int i = 0; i < sparseArray.length; i++) {
            System.out.printf("%d\t%d\t%d\n", sparseArray[i][0], sparseArray[i][1], sparseArray[i][2]);
        }

        // 恢复二维数组
        int[][] restoredArray = new int[sparseArray[0][0]][sparseArray[0][1]];
        for (int i = 1; i < sparseArray.length; i++) {
            restoredArray[sparseArray[i][0]][sparseArray[i][1]] = sparseArray[i][2];
        }
    }
}
```

### 稀疏数组的解释：
- **稀疏数组格式**：第一行记录原始数组的大小（行和列）以及非零元素的个数，后面的每一行记录非零元素的行、列和值。
- **优势**：通过这种方式，原本占用大量空间的数组可以转化为一个较小的稀疏数组，极大地节省空间。

## 总结
- 数组是存储相同类型元素的有序

集合，可以通过下标访问元素，长度固定。
- Java 中数组是引用类型，保存在堆内存中。
- 冒泡排序是一种通过相邻元素比较并交换来排序的简单算法。
- 稀疏数组适用于大多数元素相同（如 0）的场景，能够压缩存储，减少空间占用。