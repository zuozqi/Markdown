---
title: Machine Learning
date: 2016年10月23日18:52:26
categories: 工具
tags: [MachineLeaning, Note]  
---


回归线分析
===


单变量回归线
---

这里我们假设回归线的方程是

 $$ h_{\theta}(x) = \theta_{0} + \theta_{1} x $$

 单变量分析就是使

  $$J =\frac{1}{2m} \sum_{1}^{m} ( h_{\theta} (x^{(i)} ) - y^{(i)} ) ^ 2 $$

取得最小值，$h_{\theta}(x)$ 简写为 $h(x)$，是$x$ 的函数，$\delta$ 是$\theta$ 的函数。

<!--more-->


多变量回归线
---

回归方程更新为

 $$h_{\theta}(x) = \theta_{0}x_0 + \theta_{1} x_1 + \theta_(2)x_2 +...+\theta_n x_n $$ 

可以将 $x_1$  理解为1，这是由多个变量共同影响一个值时的线性方程。每个变量对应的参量为$\theta_i$ 。对应向量为$\theta$ 。

所以偏差为

$$ J_\theta = J(\theta_0,\theta_1,...,\theta_n) =\frac{1}{2m} \sum_{1}^{m} ( h_{\theta} (x^{(i)} ) - y^{(i)} ) ^ 2 $$

$x_j^{(i)}$ 的意思是，第i个样本，的第j个特性的取值。




Feature Scaling
---
确保各个变量处在相似的取值范围内，否则的话康托曲线会很畸形（竖直或者水平）。这样找到最适合的值就比较难。可以把各个参数做归一化处理
比如
>房子的面积取（0-2000）平方米
>拥有的卧室数取(0-5)个
>在定义对应的变量$x_1,x_2$时，可以取$x_1 = x_1/2000,   x_2 = x_2/5 $

习惯把所有的参数统一到 $-1 \le x_i \le 1 $ 范围内。取值范围差太多时不可以的，但相同数量级之间没什么问题。


Gradient descent
---

寻找参数的方法：梯度下降法
$$ \theta_j := \theta_j - \alpha \frac{\partial}{\partial \theta_j} J(\theta)$$
需要注意的有两点

- 能递归到结果
- $\alpha$ 取值使运算尽量快

随着迭代次数的增加，$J(\theta)$ 的最小值应该逐渐减少，并趋于稳定。
当迭代不稳定的时候，选取更小的 $\alpha$ 可以让迭代收敛。$\alpha$ 太小会让迭代很慢，太大可能不收敛，所以实际应用要先试着选几个值。


Polynomial Regression
---
使用一个参数的多次幂

$$ h(\theta) = \theta_0 + \theta_1 x +\theta_2 x^2 +...+\theta_n x^n$$

参数的取值范围非常重要，因为若$x\subset(0,10)$ ,那么$x^2 \subset (0,100),x^3 \subset (0,1000)$。

小tip:

对于渐增稳定的函数，可以选取

$$ h(\theta) = \theta_0 + \theta_1 x + \theta_2 \sqrt{x}$$




Normal Equation
---

有一种可以通过分析求得$\theta$的方法，就叫NF。

对方程的每一个参数的偏导，然后求得极值，得到的就是每一个参数的取值。

将变量，参数和结果向量化，最后的参数取值为：

$$ X = [ (x^{(1)})^T\quad(x^{(2)})^T...(x^{(n)})^T]^T$$

就是把每个已知量按顺序写一行，下面一行使第二个……组成的矩阵。

$$ \theta = (X^T X)^-1 X^T y$$

具体的过程略去...

在Octave中，矩阵计算表达式为：

```matlab
pinv(X'*X)*X'*y
```

计算结果就是最小$\theta$ 取值的向量。




Comparison of GD & NE
---

|     Gradient Descent      |   Normal Equation    |
| :-----------------------: | :------------------: |
|      Choose $\alpha$      |          -           |
|      Need iterations      |          -           |
| Work well when n is large | Slow when n is large |

所以当自变量不多时，NE方法很方便，当自变量多时，GD有优势。



当$X^T X $不可逆时，有另外的解决方法。在Octave中要用`pinv`而不是`inv`。出现的原因可能是：

- 自变量有冗余，比如变量中有线性关系。
- 有太多的自变量，以至于数量多过例子数。



Octave Tutorial
---

基本类似Matlab，处在CLI环境下

```matlab
randn() %生成期望是0的随机数
rand() %生成0-1的随机数
hist() %将某个向量统计成柱状图
eye() %对角是1的那个矩阵
help xxx %帮助文件
```

下面一段是读入处理输出数据的例子

```matlab
A = [1 2 ; 3 4 ; 5 6]
size(A)
size(A,1) %返回行数
v = [1 2 3 4]
length(v)
length([1;2;3;4;5])
load xxx.dat %加载文件，文件要在当前目录下，切换目录和Linux一样
who %显示内存已有的变量，文件是作为矩阵加载进来
whos %显示的更详细一些
v = priceY(1:10) %假设已经加载了pricrY，这个命令是将前10个数据输入到v里
save hello.mat v
clear
load hello.mat
A(3,2)
A(2,:) %输出第二行所有元素，: 为所有元素的意思
A([1 3],:) %输出处在第一行，第三行的所有元素
A(:,2) = [ 10; 11; 12]
A = [A, [100; 101; 102]] %在A右侧加一列
A(:) %把A所有元素放到一个列向量
B = [11 12 ; 13 14 ; 15 16]
C = [A B] %左右拼接
A = [1 2 ; 3 4 ; 5 6]
C = [A;B] %上下拼接
```

以上就是Octave的基本的操作，可以看到和Matlab基本上是一样的，如果看输出的话两者长的更像。所以Octave和Matlab用哪个都无所谓，只是Octave是开源的，Matlab收费，后者稳定一点。

下面我们进行一些数据的计算

```matlab
A = [1 2; 3 4; 5 6]
B = [11 12; 13 14; 15 16]
C = [1 1;2 2]
A * C % 叉乘
A .* B %对应位置元素相乘
A .^ 2
v = [1; 2; 3]
1 ./ v
exp (v)
abs (v)
v + ones (length (v),1)
v + 1 %两行效果相同
A' 
(A')'
a = [1 15 2 0.5]
[val, ind] = max(a) %返回最大值的值和序号
a < 3 %返回逻辑判断
magic(3)
[r ,c] = find(A>=7) %返回位置
sum (a)
prod(a)
floor(a) %a的小数取下面整数
ceil(a) %上面整数
max(rand(3),rand(3)) %取两者大的
max[A,[],1] %返回A每一列的最大值
max[A,[],2] %返回A每一行的最大值
sum(A,1) %分列求和A
```

下面进行数据的展示，主要是画图

```matlab
t = [0: 0.01 : 0.98]
y1 = sin(2*pi*4*t)
y2 = cos(2*pi*4*t)
plot(t,y1)
plot(t,y2)
hold on;
plot(t,y1,'r')
xlable('time')
ylable('value')
title('Myplot')
print -dpng 't.png' %保存到当前目录，或者前面加cd '  '指定路径
close
figure(1);plot(t,y1)
figure(2);plot(t,y2)
subplot(1,2,1) %将图分为两个部分，访问第一个部分
plot(t,y1)
subplot(1,2,2)
axis([0.5 1 -1 1]) %设置轴取值范围
clf
A = magic(15)
imagesc(A),colorbar,colormap gray;
```

在Octave中，同样可以用 `for` ,`while`,`if break` 进行循环控制。




.m文件
---

假设有这样一个文件，1.m

```matlab
function[y1,y2] = squareandcube(x) %一个参量x，返回 y1 和 y2
y1 = x ^ 2
y2 = x ^ 3
```

将这个文件放在pwd下，运行下面这行命令

```octave
[a,b] = squareandcube(6)
```

则得到两个数值的结果。

下面是一个求偏差的函数

```matlab
function J = constfunction(X,y,theta)
m = size(X,1) %求X的行数，即例子数
predictions = X * theta;
sqrErrors = (predictions - y) .^ 2;
J = 1/(2*m) * sum(sqrErrors);
```

假设输入条件为：

```matlab
X = [1 1; 1 2;1 3]
y = [1;2;3]
theta = [0;1]
```

则可以得到偏差为0


向量化
---

向量化是很重要的简化方法,比如这个式子:

$$ h_{\theta} (x) = \sum_{j=0}{n} \theta_j x_j$$

$$ = \theta^T x $$

$\theta\quad x$ 均为列向量。

如果循环写的话，难免会用到for或者什么语句，而向量值需要一个点乘就可以。

需要注意的是，在Octave/Matlab中， 向量编号自1起。

 

