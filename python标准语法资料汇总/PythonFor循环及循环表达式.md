
Python for循环可以遍历任何序列的项目，如一个列表或者一个字符串。<br>
语法：<br>
for循环的语法格式如下：<br>
for iterating_var in sequence:<br>
   statements(s)<br>

流程图<br>

![%E5%9B%BE%E7%89%87.png](attachment:%E5%9B%BE%E7%89%87.png)

例子1：传统用法


```python
for letter in 'Python':  # 第一个实例
    print('当前字母 :', letter)

fruits = ['banana', 'apple', 'mango']
for fruit in fruits:  # 第二个实例
    print('当前水果 :', fruit)
```

    当前字母 : P
    当前字母 : y
    当前字母 : t
    当前字母 : h
    当前字母 : o
    当前字母 : n
    当前水果 : banana
    当前水果 : apple
    当前水果 : mango


例子2：使用列表索引


```python
fruits = ['banana', 'apple',  'mango']
for index in range(len(fruits)):
   print('当前水果 :', fruits[index])
```

    当前水果 : banana
    当前水果 : apple
    当前水果 : mango


例子3：使用else循环<br>
在 python 中，for … else 表示这样的意思，for 中的语句和普通的没有区别，else 中的语句会在循环正常执行完（即 for 不是通过 break 跳出而中断的）的情况下执行，while … else 也是一样。


```python
for num in range(10,20):  # 迭代 10 到 20 之间的数字
   for i in range(2,num): # 根据因子迭代
      if num%i == 0:      # 确定第一个因子
         j=num/i          # 计算第二个因子
         print('%d 等于 %d * %d' % (num,i,j))
         break            # 跳出当前循环
   else:                  # 循环的 else 部分
      print(num, '是一个质数')
```

    10 等于 2 * 5
    11 是一个质数
    12 等于 2 * 6
    13 是一个质数
    14 等于 2 * 7
    15 等于 3 * 5
    16 等于 2 * 8
    17 是一个质数
    18 等于 2 * 9
    19 是一个质数


例子4：使用内置 enumerate 函数进行遍历:


```python
sequence = [12, 34, 34, 23, 45, 76, 89]
for i, j in enumerate(sequence):
    print(i,j)

```

    0 12
    1 34
    2 34
    3 23
    4 45
    5 76
    6 89


例子5：for表达式<br>
语法：<br>
[expr for iter_var in iterable] <br>
[expr for iter_var in iterable if cond_expr] <br>

第一种语法：首先迭代iterable里所有内容，每一次迭代，都把iterable里相应内容放到iter_var中，再在表达式中应用该iter_var的内容，最后用表达式的计算值生成一个列表。<br>
第二种语法：加入了判断语句，只有满足条件的内容才把iterable里相应内容放到iter_var中，再在表达式中应用该iter_var的内容，最后用表达式的计算值生成一个列表。


```python
L= [(x+1,y+1) for x in range(2) for y in range(3)]
print(L)
```

    [(1, 1), (1, 2), (1, 3), (2, 1), (2, 2), (2, 3)]



```python
N=[x+10 for x in range(10) if x>5]
print(N)

```

    [16, 17, 18, 19]



```python
num = [j for i in range(2, 8) for j in range(i*2, 50, i)]
print(num)
```

    [4, 6, 8, 10, 12, 14, 16, 18, 20, 22, 24, 26, 28, 30, 32, 34, 36, 38, 40, 42, 44, 46, 48, 6, 9, 12, 15, 18, 21, 24, 27, 30, 33, 36, 39, 42, 45, 48, 8, 12, 16, 20, 24, 28, 32, 36, 40, 44, 48, 10, 15, 20, 25, 30, 35, 40, 45, 12, 18, 24, 30, 36, 42, 48, 14, 21, 28, 35, 42, 49]


for前也可以使用方法


```python
words ='The quick brown fox jumps over the lazy dog'.split()
stuff = [[w.upper(), w.lower(), len(w)] for w in words]
print(stuff)

```

    [['THE', 'the', 3], ['QUICK', 'quick', 5], ['BROWN', 'brown', 5], ['FOX', 'fox', 3], ['JUMPS', 'jumps', 5], ['OVER', 'over', 4], ['THE', 'the', 3], ['LAZY', 'lazy', 4], ['DOG', 'dog', 3]]


上述代码的map（）实现：


```python
stuff = map(lambda w: [w.upper(), w.lower(), len(w)], words)
for i in stuff:
    print(i)
```

    ['THE', 'the', 3]
    ['QUICK', 'quick', 5]
    ['BROWN', 'brown', 5]
    ['FOX', 'fox', 3]
    ['JUMPS', 'jumps', 5]
    ['OVER', 'over', 4]
    ['THE', 'the', 3]
    ['LAZY', 'lazy', 4]
    ['DOG', 'dog', 3]


生成器表达式<br>
生成器表达式是在python2.4中引入的，当序列过长， 而每次只需要获取一个元素时，应当考虑使用生成器表达式而不是列表解析。生成器表达式的语法和列表解析一样，只不过生成器表达式是被（）括起来的，而不是[]，如下：<br>
(expr for iter_var in iterable) <br>
(expr for iter_var in iterable if cond_expr)<br>
例： <br>


```python
L= (i +1for i in range(10) if i %2)

L1=[]
for i in L:
    L1.append(i)
```


```python
print(L)
```

    <generator object <genexpr> at 0x11066e728>



```python
print(L1)
```

    [2, 4, 6, 8, 10]


生成器表达式并不真正创建数字列表， 而是返回一个生成器，这个生成器在每次计算出一个条目后，把这个条目“产生”(yield)出来。 生成器表达式使用了“惰性计算”(lazy evaluation，也有翻译为“延迟求值”，我以为这种按需调用call by need的方式翻译为惰性更好一些)，只有在检索时才被赋值（ evaluated），所以在列表比较长的情况下使用内存上更有效。A generator object in python is something like a lazy list. The elements are only evaluated as soon as you iterate over them. <br>
一些说明：<br>
1. 当需要只是执行一个循环的时候尽量使用循环而不是列表解析，这样更符合python提倡的直观性。<br>
for item in sequence:<br>
process(item)<br>
2. 当有内建的操作或者类型能够以更直接的方式实现的，不要使用列表解析。<br>
例如复制一个列表时，使用：L1=list（L）即可，不必使用：<br>
L1=[x for x in L]<br>
3. 当序列过长， 而每次只需要获取一个元素时，使用生成器表达式。<br>
4. 列表解析的性能相比要比map要好，实现相同功能的for循环效率最差（和列表解析相比差两倍）。<br>
5. 列表解析可以转换为 for循环或者使用map（其中可能会用到filter、lambda函数）表达式，但是列表解析更为简单明了，后者会带来更复杂和深层的嵌套。<br>
