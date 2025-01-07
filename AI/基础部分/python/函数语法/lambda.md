`lambda` 是 Python 中用来创建匿名函数的关键字。它允许你生成一个简单的函数，而不需要使用 `def` 语句来定义一个完整的函数。以下是 `lambda` 的基本语法和一些使用示例。

---
# `基本语法`
```
lambda arguments: expression
```

- **`lambda`**：关键字，用来声明一个匿名函数。
- **`arguments`**：输入参数，可以是一个或多个，以逗号分隔。
- **`expression`**：一个单一的表达式，这个表达式的结果会作为函数的返回值。


---
# 例子

## 1. **基本使用**：

本质上，`lambda` 创建一个函数，下面的例子展示了如何使用 `lambda`：
```
# 创建一个将输入值加2的匿名函数
add_two = lambda x: x + 2

print(add_two(3))  # 输出: 5


```
---

## 2.多个参数：
可以定义多个参数，如下所示：
```
# 创建一个接受两个参数并返回其和的匿名函数
add = lambda x, y: x + y

print(add(3, 4))  # 输出: 7

```
---
## 3.与高阶函数结合使用：
`lambda` 函数常常用于高阶函数，比如 `map`、`filter` 和 `sorted` 等。例如：

```
# 使用lambda与map和filter
numbers = [1, 2, 3, 4, 5]

# 使用map来平方每个数
squares = list(map(lambda x: x ** 2, numbers))
print(squares)  # 输出: [1, 4, 9, 16, 25]

# 使用filter来选择大于2的数
greater_than_two = list(filter(lambda x: x > 2, numbers))
print(greater_than_two)  # 输出: [3, 4, 5]

```

---
## 4.排序中的使用： 
可以在 `sorted` 函数中使用 `lambda` 来定义自定义的排序逻辑：
```
# 按照第二个元素排序的示例
pairs = [(1, 2), (4, 1), (3, 6)]
sorted_pairs = sorted(pairs, key=lambda x: x[1])
print(sorted_pairs)  # 输出: [(4, 1), (1, 2), (3, 6)]

```
---
# 注意事项

- `lambda` 函数只能包含一个表达式，不能包含多个语句或复杂的逻辑。
- `lambda` 函数返回表达式的值，但没有 `return` 语句。
- 使用 `lambda` 通常是在需要一个临时的、简单的函数的场景中。如果函数逻辑较复杂，建议使用 `def` 来定义。