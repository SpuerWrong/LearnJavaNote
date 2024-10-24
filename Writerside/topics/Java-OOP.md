# Java_OOP

面向对象编程（OOP）是一种编程范式，通过将数据和操作数据的代码组织成对象，使得代码结构更加清晰、易维护。Java 是一种典型的面向对象语言。以下是 Java 面向对象编程的主要概念和特性。

## 面向过程和面向对象

### 面向过程
- **面向过程**是一种编程方式，注重按步骤执行代码来完成任务，每一步都是按顺序处理的。
- 适合一些简单、短小的程序，但当程序规模增大时，代码复用性和可维护性较差。

### 面向对象
- **面向对象**是一种将程序结构按对象（事物的抽象）来组织的编程方式，通过类与对象的方式进行程序设计。
- **面向对象的本质**：通过类的方式组织代码，使用对象来封装数据。
- **核心思想**：抽象，把现实中的事物抽象为对象和类。

#### 三大特性
1. **封装**：将对象的状态信息隐藏在内部，仅提供公共方法供外部调用。
2. **继承**：通过继承机制，子类可以继承父类的属性和方法，减少代码重复。
3. **多态**：同一方法在不同对象中可以有不同表现，增强代码的灵活性和扩展性。

## 静态类和非静态类

### 静态类
- 在 Java 中，**静态类**一般指嵌套在其他类中的 `static` 内部类。
- 静态类可以直接通过外部类调用，不需要实例化外部类。

### 非静态类
- **非静态类**必须实例化后才能使用。
- 例如：
    ```java
    Student student = new Student();  // 创建 Student 类的实例
    ```

## 形参和实参

- **形参**：方法定义时的参数，称为形式参数。
- **实参**：调用方法时实际传入的参数，称为实际参数。

## 值传递和引用传递

- **值传递**：传递基本类型的值，不影响原始数据。
- **引用传递**：传递对象引用，对象的属性值可能被改变。

## `this` 关键字

- **`this`** 代表当前对象的引用，用于区分成员变量和局部变量，也可以在构造方法中调用类的其他构造方法。

## 类和对象的关系
- **类**是一种抽象的数据类型，是对某一类事物的整体描述。
- **对象**是类的实例化，即具体的实例，代表某一类事物的具体表现。

## 构造器（构造方法）

### 构造器的作用
1. 在创建对象时初始化对象的属性。
2. 使用 `new` 关键字创建对象时必须调用构造器。

### 构造器的特点
1. 构造器的名称与类名相同。
2. 构造器没有返回值类型。
3. 如果定义了带参数的构造器，需要额外定义无参构造器以确保兼容性。

### 快捷键
- 在 IDE 中使用 `Alt+Insert` 快速生成构造器。

```java
public class Student {
    private String name;
    private int age;

    public Student(String name, int age) {  // 带参构造器
        this.name = name;
        this.age = age;
    }
}
```

## 创建对象的内存分析

Java 内存分为堆、栈、方法区等部分，不同数据存放在不同区域。创建对象时，对象存放在堆中，对象的引用存放在栈中。

## 封装

- **封装**是一种将数据隐藏在对象内部的方式，通过 `private` 关键字对属性进行封装，外部只能通过 `get` 和 `set` 方法访问。

### 封装的意义
1. 提高程序的安全性，保护数据。
2. 隐藏实现细节，减少耦合。
3. 统一接口，增加系统的可维护性。

```java
public class Student {
    private String name;  // 属性封装
    private int age;

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }
}
```

## 继承

- **继承**是一种类与类之间的关系，使得子类可以拥有父类的属性和方法。
- Java 中支持**单继承**，即每个类只能有一个直接父类。

### `extends` 关键字
- 使用 `extends` 关键字表示继承。

```java
public class Animal {
    public void eat() {
        System.out.println("Animal is eating");
    }
}

public class Dog extends Animal {
    public void bark() {
        System.out.println("Dog is barking");
    }
}
```

## 修饰符

- **`public`**：可以被所有类访问。
- **`protected`**：可以被同包和子类访问。
- **默认（default）**：仅限于同包访问。
- **`private`**：仅限于同类访问。

## `Object` 类

- **`Object`** 是所有类的父类，位于 `java.lang` 包中。
- 每个类都隐式继承 `Object` 类，提供基础方法如 `toString()` 和 `equals()`。

## `super` 关键字

- `super` 用于引用父类的属性和方法。
- 在子类构造方法中可以通过 `super()` 调用父类的构造方法，必须位于构造方法的首行。

### `super` 与 `this` 的区别
- **`this`**：代表当前对象的引用。
- **`super`**：代表父类对象的引用。
- **构造方法**：
    - `this()` 调用当前类的构造方法。
    - `super()` 调用父类的构造方法。

## 方法的重写

- **重写**是子类对父类方法进行修改，满足多态性需求。
- 使用 `@Override` 注解标注重写的方法，确保语法正确。

### 重写的规则
1. 方法名和参数列表必须相同。
2. 访问权限范围可以扩大但不能缩小。
3. 抛出异常范围可以缩小但不能扩大。

```java
public class Animal {
    public void sound() {
        System.out.println("Animal makes sound");
    }
}

public class Dog extends Animal {
    @Override
    public void sound() {
        System.out.println("Dog barks");
    }
}
```

## 多态

- **多态**是指相同的方法可以根据不同对象表现出不同的行为。
- **实现多态的条件**：
    1. 存在父子类关系。
    2. 子类重写父类方法。
    3. 使用父类引用指向子类对象。

```java
public class Animal {
    public void sound() {
        System.out.println("Animal sound");
    }
}

public class Dog extends Animal {
    @Override
    public void sound() {
        System.out.println("Dog barks");
    }
}

Animal animal = new Dog();
animal.sound();  // 输出: Dog barks
```

## `instanceof` 关键字和引用类型的转换

- **`instanceof`** 检查一个对象是否是某个类或接口的实例，用于避免类型转换异常。
- **类型转换**：
    1. 父类引用指向子类对象（向上转型），自动转换。
    2. 父类引用转回子类对象（向下转型），需要强制转换。

```java
Animal animal = new Dog();
if (animal instanceof Dog) {
    Dog dog = (Dog) animal;
    dog.bark();
}
```

## `static` 关键字

- **`static`** 表示静态成员或方法，属于类本身，不依赖于具体对象。
- **静态代码块**：只在类加载时执行一次，用于初始化类的静态资源。

```java
public class StaticExample {
    static {
        System.out.println("Static block");
    }
    
    {
        System.out.println("Instance block");
    }
    
    public StaticExample() {
        System.out.println("Constructor");
    }
    
    public static void main(String[] args) {
        new StaticExample();
        new StaticExample();
    }
}
```

### 输出结果
```
Static block
Instance block
Constructor
Instance block
Constructor
```

## `final` 关键字

- **`final`** 用于声明常量、方法不可被重写、类不可被继承等情况。

```java
public final class Constants {
    public static final int MAX_VALUE = 100;
}
```
