# Math.abs 出现负数的问题

## 问题
```java
Math.abs(-2147483648) -> -2147483648
```

## 原因

如果参数是整数最小负数，则Math.abs（int a）方法会返回最小负数本身，那么该方法为啥这样做那。其实是因为最大正数为2147483647，而最小负数为-2147483648，对最小负数加绝对值后，已经超过了最大正正数所表达的范围。

```java
System.out.println("Integer is " + Math.abs(Integer.MIN_VALUE));
System.out.println("Long is " + Math.abs(Long.MIN_VALUE));
System.out.println("Byte is " + Math.abs(Byte.MIN_VALUE));

Integer is -2147483648
Long is -9223372036854775808
Byte is 128
```

## 解决
1. 我们可以使用 **Math.abs(long a)** 函数，也就是把 hash 值从整形转换为long型
2. 我们可以对hash值做映射，如果 hash 值为正数最小负数则把其映射为一个固定的正数值即可。