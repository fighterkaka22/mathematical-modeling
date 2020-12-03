# SymPy符号整理

* **定义变量（符号）**：symbols
* **定义函数**：Function
# SymPy函数整理

## 积分与泰勒展开

* **表达式展开**：*expand*()

expand(,complex=True):表达式分为实数、虚数两部分

* **泰勒展开**：*series*(函数表达式,自变量,0,余项次数)
* **不定积分运算**：*integrate*(表达式，自变量)

**定积分运算**：*integrate*（表达式，（自变量，积分下界，积分上届））

* **算式中x换成y**：*subs*(x,y)

**IN：**

```python
import numpy as np
from sympy import *
#将x定义为符号
x=Symbol("x",real=True)
#创建多个符号：x,y,r=symbols('x,y,r')
#参数：positive=True，表示符号为正
#var():快速创建变量和Symbol对象
#泰勒展开
tmp=series(exp(I*x),x,0,10)
tmp
#获得tmp实部
re(tmp)
#获得tmp虚部
im(tmp)
```
**OUT:**
```plain
1 + I*x - x**2/2 - I*x**3/6 + x**4/24 + I*x**5/120 - x**6/720 - I*x**7/5040 + x**8/40320 + I*x**9/362880 + O(x**10)
x**8/40320 - x**6/720 + x**4/24 - x**2/2 + re(O(x**10)) + 1
```
## 表达式化简

* **化简数学表达式**：simplify()
* **分母有理化**：radsimp()
* **通分**：fraction()
* **约分**：trim()
* **三角函数化简**：trigsimp()

deep=True：对所有子表达式化简

recursive=True：递归进行最大程度化简

* **乘法展开**：mul()
* **整数次幂展开**：multinomial()
* **log展开**：expand()
* **合并同类项**：collect()

**IN:**

```python
var("a,b,x")
#展开eq得到eq2
eq=(1+a*x)**3+(1+b*x)**2
eq2=expand(eq)
eq2
#合并同类项
collect(eq2,x)
#得到x的各次幂系数，如获得x的二次项系数
p=collect(eq2,x,evaluate=False)
p[x**2]
```
**OUT:**
```plain
a**3*x**3 + 3*a**2*x**2 + 3*a*x + b**2*x**2 + 2*b*x + 2
a**3*x**3 + x**2*(3*a**2 + b**2) + x*(3*a + 2*b) + 2
3*a**2 + b**2
```
#### 
## 解方程

* **解方程**：solve()

IN:

```python
var("a,b,c")
#解一元二次方程
solve(a*x**2+b*x+c,x)
#解二元二次方程，结果每个元组表示方程的一组解
solve((x**2+x*y+1,y**2+x*y+2),x,y)
```
OUT:
```plain
[(-b + sqrt(-4*a*c + b**2))/(2*a), -(b + sqrt(-4*a*c + b**2))/(2*a)]
[(-sqrt(3)*I/3, -2*sqrt(3)*I/3), (sqrt(3)*I/3, 2*sqrt(3)*I/3)]
```
## 微分

* **得到导函数**：t=Derivative(f(x),x)
* **计算出导函数：**t.doit()
* **高阶导函数**：Derivative(f(x),x,3)
* **多个变量导函数**：Derivative(f(x,y),x,2,y,3)
* **微分方程符号求解**：dsolve((Derivative(f(x),x)-f(x),f(x))

hint=best，返回最简单的解，得到最简单的显函数表达式

## 积分

* **不定积分运算**：*integrate*(表达式，自变量)
* **定积分运算**：*integrate*（表达式，（自变量，积分下界，积分上届））
* **二重不定积分运算**：*integrate*（表达式，x,y）
* **二重定积分运算**：*integrate*（表达式，(x,a,b),(y,c,d)）
* **计算出积分函数**：doit()
* 无法表示为初等函数的积分——数值计算：evalf()

（不够精确，且不适合计算无穷积分）

# 其他

一些基础语句补充：

* E:自然底数
* I:虚数单位
* pi:π
* **:^
* exp():e^x
# 参考资料

* 《Python科学计算》
