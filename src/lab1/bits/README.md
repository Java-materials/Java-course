[Назад к описанию темы](https://github.com/Vladislav-Lyuminarskiy/Java-course/blob/master/lab1/bits.md)

# Битовые операции

Рассмотрим пример решения следующей задачи:

> Поменять местами байты в числе.

Для начала нужно задать число, которым мы будем оперировать. Запрограммируем выбор числа случайным способом, чтобы каждый запуск программы выдавал нам уникальный результат:

```java
int input = (int)(Math.random() * Integer.MAX_VALUE);
```

Выведем полученное число на экран:

```java
System.out.format("In [0]: 0x%08X\n", input);
```

Вывод программы:

```
In [0]: 0x6E721EA8
```

Поменять байты в числе можно с помощью операции сдвига. Для получения младшего байта нового числа используем операцию сдвига вправо на половину размера числа в байтах:

```java
int lsb = input >> (Integer.SIZE / 2);
```

Для получения старшего байта нового числа используем операцию сдвига влево на половину размера числа в байтах:

```java
int msb = input << (Integer.SIZE / 2);
```

Посмотрим промежуточный результат:

```java
System.out.format("Out[0]: 0x%08X\n", lsb);
System.out.format("Out[1]: 0x%08X\n", msb);
```

Вывод программы:

```
Out[0]: 0x00006E72
Out[1]: 0x1EA80000
```

Теперь нам осталось только объединить результаты операций сдвига с помощью операции ИЛИ:

```java
int output = lsb | msb;
```

Посмотрим результат:

```java
System.out.format("Out[2]: 0x%08X", output);
```

Вывод программы:

```
Out[2]: 0x1EA86E72
```

Как видим, в результате получилось успешно поменять байты местами.

[Посмотреть полный код примера](https://github.com/Vladislav-Lyuminarskiy/Java-course/blob/master/lab1/examples/bits/Main.java)