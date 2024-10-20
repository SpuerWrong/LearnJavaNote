# Java_ScannerOI
Java 流程控制
## 用户交互Scanner对象 {id="scanner_1"}

### Scanner对象
Java提供的可以获取用户输入的工具类，java.util.Scanner是java5新特征
```java
public class Demo01{
    public static void main(String[] args){
        Scanner scanner = new Scanner(System.in);
        System.out.println("使用next方式接收：");
        
        //判断用户有没有输入字符串
        if(scanner.hasNext()){
        String str = scanner.next();
        System.out.println("输出的内容："+str);
        }
        scanner.close();
        //凡是属于IO流的类如果不关闭会一直占用资源，要养成
    }
}
```
基本语法：
```java
Scanner scanner = new Scanner(System.in);
```

Scanner对象：<br>
1. next()
   功能：用于读取并返回下一个有效的输入字符或字符串，自动跳过无效字符。
   特点：
   自动跳过空白字符：next()在读取到有效字符前，会自动跳过空白字符（如空格、换行等）。
   有效字符为界：只有在读取到有效字符后，next()才会将后续的空白字符视为分隔符或结束符。
   不读取空格：next()无法获取带有空格的字符串，一旦遇到空格就会将其作为分隔符。
2. nextLine()
   功能：读取一整行输入，直到用户按下 "Enter" 键为止。
   特点：
   整行读取：nextLine()会读取包括空格在内的整行内容，并将光标移至下一行等待输入。
   以Enter结束：在遇到"Enter"之前的所有字符都被视为有效输入。
3. nextInt()
   功能：用于接收整型（int）数据的输入。
   特点：
   如果输入不为有效的整数值，程序可能会抛出异常。
4. nextDouble()
   功能：用于接收双精度浮点型（double）数据的输入。
   特点：
   输入不为有效的双精度浮点数时，同样会抛出异常。
5. nextFloat()
   功能：用于接收单精度浮点型（float）数据的输入。
   特点：
   与nextDouble()类似，专门用于处理float类型输入。
6. nextShout()
   功能：用于接收shout类型数据的输入（假设这是自定义类型）。
   特点：根据上下文可能是一个特别定义的类型，需要具体环境下的说明。
7. hasNextInt()
   功能：判断是否存在可以解析为int类型的输入。
   特点：如果输入内容能够成功转换为int类型，则返回true。
8. hasNext()
   功能：判断输入流中是否存在下一个有效的字符或字符串。
   特点：常用于输入是否结束的检测。
9. hasNextLine()
   功能：判断输入流中是否还有下一行内容可供读取。
   特点：通常用于检测输入是否已读到最后一行。
10. hasNextDouble()
    功能：判断是否存在可以解析为double类型的数据。
    特点：如果输入内容能被成功解析为double类型，则返回true。
11. hasNextFloat()
    功能：判断是否存在可以解析为float类型的数据。
    特点：与hasNextDouble()类似，用于检测float类型的数据输入。
12. hasNextShout()
    功能：判断是否存在可以解析为shout类型的数据（假设为自定义类型）。
    特点：具体行为需参考shout类型的定义。

