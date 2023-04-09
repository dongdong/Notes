# Effective Python

### Part 1. Pythonic

##### 1. 【Version】Python 版本

##### 2. 【PEP】PEP 风格

##### 3. 【Text】bytes, str, Unicode

##### 4. 【辅助函数】用辅助函数代替复杂表达式

##### 5. 【Slicing】序列切割

##### 6. 【Slicing】

##### 7. 【列表推导】用列表推导取代 map 和 filter

##### 8. 【列表推导】不用使用含有两个表达式以上的列表推导

##### 9. 【列表推导】使用生成器表达式改写数据量大的列表推导

##### 10. 【enumerate】用 enumerate 取代 range

##### 11. 【zip】用 zip 同时遍历两个迭代器

##### 12. 【else】不要在 for 和 while 后写 else 块

##### 13. 【try】合理利用 try/except/else/finally 结构中的每个代码块

### Part 2. 函数

##### 14. 【异常】尽量用异常来表示特殊情况，而不是返回 None

##### 15. 【闭包】了解如何在闭包里面使用外围作用域中的变量

##### 16. 【生成器】考虑用生成器来改写直接返回列表的函数

##### 17. 【参数】在参数上面迭代时，要多加小心

##### 18. 【参数】用数量可变的位置参数减少视觉杂讯

##### 19. 【参数】用关键字参数来表达可选行为

##### 20. 【参数】用 None 和文档字符串描述具有动态默认值的参数

##### 21. 【参数】用只能以关键词形式指定的参数来确保代码明晰

### Part 3. 类与继承

##### 22. 【辅助类】尽量用辅助类来维护程序状态，而不是用 dict 和 tuple

##### 23. 【接口参数】简单的接口应该接受函数，而不是类的实例

##### 24. 【对象构建】以 @classmethod 形式的多态去通用的构建对象

##### 25. 【初始化】用 super 初始化父类

##### 26. 【Mixin】只在使用 Mix-in 组件制作工具类时使用多重继承

##### 27. 【属性】多用 public 属性，少用 private 属性

##### 28. 【自定义容器】继承 collections.abc 以实现自定义容器类型

### Part 4. 元类及属性

##### 29. 用纯属性取代 get 和 set 方法

##### 30. 【property】考虑用 @property 来代替属性重构

##### 31. 【property】用描述符来改写需要复用的 @property 方法

##### 32. 【属性】用\_\_getattr\_\_, \_\_getattribute\_\_ 和 \_\_setattr\_\_ 实现按需生成属性

##### 33. 【元类】用元类来验证子类

##### 34. 【元类】用元类来注册子类

##### 35. 【元类】用元类来注解类的属性

### Part 5. 并发与并行

##### 36. 【进程】用 subprocess 模块来管理子进程

##### 37. 【线程】可以用线程来执行阻塞式I/O，但不要用它做并行计算

##### 38. 【线程】在线程中使用Lock来防止数据竞争

##### 39. 【线程】用Queue来协调各线程之间的工作

##### 40. 【协程】考虑用协程来并发地运行多个函数

##### 41. 【并行计算】考虑用 concurrent.future 来实现真正的并行计算

### Part 6. 内置模块

##### 42. 【装饰器】用functools.wraps定义函数装饰器

##### 43. 【with】考虑以 contextlib 和 with 语句来改写可复用的 try/finnally 代码

##### 44. 【copyreg】用 copyreg 实现可靠的 pickle 操作

##### 45. 【datetime】用 datetime 模型来处理本地时间，而不是用 time 模块

##### 46. 【内置模块】使用内置算法和数据结构

##### 47. 【decimal】在重视精确度的场合，应该使用 decimal

##### 48. 【pip】学会安装由 Python 开发者社区所构建的模块

### Part 7. 协作开发

##### 49. 【文档】为每个函数，类和模块编写文档字符串

##### 50. 【API】用包来安排模块，并提供稳固的 API

##### 51. 【隔离】为自编的模块定义根异常，以便将调用者和 API 相隔离

##### 52. 【依赖】用适当的方式打破循环依赖关系

##### 53. 【虚拟环境】用虚拟环境隔离项目，并重建其依赖关系

### Part 8. 部署

##### 54. 【部署】考虑用模块级别的代码来配置不同的部署环境

##### 55. 【repr】通过 repr 字符串来输出调试信息

##### 56. 【unittest】用 unittest 来测试全部代码

##### 57. 【pdb】考虑用 pdb 来实现交互调试

##### 58. 【profile】先分析性能，然后再优化

##### 59. 【tracemalloc】用 tracemalloc 来掌控内存的使用及泄漏情况






