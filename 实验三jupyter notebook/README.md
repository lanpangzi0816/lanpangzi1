
# jupyter notebook

## 创建一个新的Notebook

在anaconda promote 中输入jupyter notebook



![在这里插入图片描述](https://img-blog.csdnimg.cn/f54f3927b26d4a2eb196415a700f834b.png#pic_center)



会弹出如下页面

![在这里插入图片描述](https://img-blog.csdnimg.cn/784e9d4b08eb4d28bd88612cff3a7d49.png#pic_center)
![在这里插入图片描述](https://img-blog.csdnimg.cn/ec17d720584a4f5db48fe8bd886fb1ee.png#pic_center)


点击python3之后：跳转到如下页面：
![在这里插入图片描述](https://img-blog.csdnimg.cn/f4ce39126b734ecf9e8bccc8f2414c23.png#pic_center)

这里有两个关键元素cell和kernal

- cell: 文本或者代码执行单元，由kernel执行。
- kernel: 计算引擎，执行cell的文本或者代码，本文基于Python 3 ipykernel引擎。



cell
主要包含两种类型的cell：

代码cell：包含可被kernel执行的代码，执行之后在下方显示输出。
Markdown cell：书写Markdown标记语言的cell。
试着输入一行代码，查看执行效果：

![在这里插入图片描述](https://img-blog.csdnimg.cn/586ad0492fd0469ea121468c5a208f22.png#pic_center)




代码执行之后，cell左侧的标签从`In [ ]` 变成了 `In [1]`。`In`代表输入，`[]`中的数字代表kernel执行的顺序，而`In [*]`则表示代码cell正在执行代码。以下例子显示了短暂的`In [*]`过程。

```python
import time
time.sleep(3)
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/ac36d8d993da4ce08c799304a890ce72.png#pic_center)


### cell模式

有两种模式，编辑模式（edit mode）和命名模式（command mode）

- 编辑模式：enter健切换，绿色轮廓
- 命令模式：esc健切换，蓝色轮廓



![在这里插入图片描述](https://img-blog.csdnimg.cn/62a96a2711634d3b99fb3757d48c0cdd.png#pic_center)


按esc之后变成蓝色：

![在这里插入图片描述](https://img-blog.csdnimg.cn/2dfc120c244c4783a741fd222c051499.png#pic_center)


快捷键
使用Ctrl + Shift + P命令可以查看所有Notebook支持的命令。

在命名模式下，一些快捷键将十分有帮助

上下键头可以上下cell移动
A 或者 B在上方或者下方插入一个cell
M 将转换活动cell为Markdown cell
Y 将设置活动cell为代码 cell
D+D（两次）删除cell
Z 撤销删除
H 打开所有快捷键的说明
在编辑模式，Ctrl + Shift + -将以光标处作为分割点，将cell一分为二。

![在这里插入图片描述](https://img-blog.csdnimg.cn/9d35d96b6e984d63bfa28196f260297d.png#pic_center)


Kernel
每个notebook都基于一个内核运行，当执行cell代码时，代码将在内核当中运行，运行的结果会显示在页面上。Kernel中运行的状态在整个文档中是延续的，可以跨越所有的cell。这意思着在一个Notebook某个cell定义的函数或者变量等，在其他cell也可以使用。例如：

![在这里插入图片描述](https://img-blog.csdnimg.cn/766a74a0336b4fdbb90edd87210907c6.png#pic_center)




以下教程将分两个例子实现基本的Notebook编写，包括简单的Python程序和Python数据分析的例子。首先，重命名文档，更改`Untitled`并输入相关文件名。注意，在写作过程中，常用`Ctrl + S`保存已有的文档。

python快速排序：

```python

def sort(a,l,r):
    if l >= r:return
    # 1、确定分界点
    x = a[(l + r) // 2]
    i, j = l - 1, r + 1
    while i < j :
        i+=1
        j-=1
        # 当左边区间的值放小于x，指针不断右移；右边的相反
        while a[i] < x :
            i += 1
        while a[j] > x :
            j -= 1
        # 2、调整区间，使得左边区间是<=x的数，右边区间是>=x的数
        # 移动过后，如果i还是小于j，说明左边或者右边有逆向数据，所以交换。
        if i < j:
            a[i], a[j] = a[j], a[i]
    # 3、递归处理左右两个区间   
    sort(a,l,j)
    sort(a,j+1,r)


#sort(a, 0, n-1)
#print(' '.join(map(str, a)))


```

在notebook上执行：

![在这里插入图片描述](https://img-blog.csdnimg.cn/5bfb7a5dc8e146c8a3f10c6489333584.png#pic_center)

## 数据分析的例子(使用pandas)



加载数据集。
```python
df = pd.read_csv('fortune500.csv')
```

因为还没有将数据集加载到notebook出现如下错误：

![在这里插入图片描述](https://img-blog.csdnimg.cn/2f8b3bd5e01d49988cd6368b43ccb6df.png#pic_center)


接下来将数据集导入到jupyter notebook

![在这里插入图片描述](https://img-blog.csdnimg.cn/4b6ca155e49b449da8e26293713b5017.png#pic_center)



重新执行导入语句：

![在这里插入图片描述](https://img-blog.csdnimg.cn/ce670a9c07a548f894e475554d51dc78.png#pic_center)


## 检查数据集

上述代码执行生成的df对象，是pandas常用的数据结构，称为`DataFrame`，可以理解为数据表。

```python
df.head()
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/9e0a7f011c13479f9d2e9dd3d95946ef.png#pic_center)


```python
df.tail()
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/9ac4932d646845a797f2a135223ef83a.png#pic_center)


对数据属性列进行重命名，以便在后续访问

```python
df.columns = ['year', 'rank', 'company', 'revenue', 'profit']
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/d1a80b45ead5471c8bb0cca9bfda8ab2.png#pic_center)


接下来，检查数据条目是否加载完整。

```python
len(df)
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/3f9ab8404c0c432b9b9ec373eac7d78a.png#pic_center)


从1955至2055年总共有25500条目录。然后，检查属性列的类型。

```python
df.dtypes
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/79ce3c3d650f4fe89764d2c6d9c5a02e.png#pic_center)


其他属性列都正常，但是对于profit属性，期望的结果是float类型，因此其可能包含非数字的值，利用正则表达式进行检查。

```python
non_numberic_profits = df.profit.str.contains('[^0-9.-]')
df.loc[non_numberic_profits].head()

```

![在这里插入图片描述](https://img-blog.csdnimg.cn/6394d99f602347dab8bd57aa56ba144d.png#pic_center)


确实存在这样的记录，profit这一列为字符串，统计一下到底存在多少条这样的记录。

```python
len(df.profit[non_numberic_profits])
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/6366ef4edb51431aa56fc4300964e648.png#pic_center)


总体来说，利润（profit）列包含非数字的记录相对来说较少。更进一步，使用直方图显示一下按照年份的分布情况。

```python
bin_sizes, _, _ = plt.hist(df.year[non_numberic_profits], bins=range(1955, 2006))
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/ef2017848ccc45dcbed71f16eaf033ae.png#pic_center)


可见，单独年份这样的记录数都少于25条，即少于4%的比例。这在可以接受的范围内，因此删除这些记录。

```python
df = df.loc[~non_numberic_profits]
df.profit = df.profit.apply(pd.to_numeric)
```






## 使用matplotlib进行绘图

接下来，以年分组绘制平均利润和收入。首先定义变量和方法。

```python
group_by_year = df.loc[:, ['year', 'revenue', 'profit']].groupby('year')
avgs = group_by_year.mean()
x = avgs.index
y1 = avgs.profit
def plot(x, y, ax, title, y_label):
    ax.set_title(title)
    ax.set_ylabel(y_label)
    ax.plot(x, y)
    ax.margins(x=0, y=0)

```

绘图：

```python
fig, ax = plt.subplots()
plot(x, y1, ax, 'Increase in mean Fortune 500 company profits from 1955 to 2005', 'Profit (millions)')

```

![在这里插入图片描述](https://img-blog.csdnimg.cn/305a4ca074a940b894d6b3e6229268ce.png#pic_center)


看起来像指数增长，但是1990年代初期出现急剧的下滑，对应当时经济衰退和网络泡沫。再来看看收入曲线。

```python
y2 = avgs.revenue
fig, ax = plt.subplots()
plot(x, y2, ax, 'Increase in mean Fortune 500 company revenues from 1955 to 2005', 'Revenue (millions)')
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/018d054e25714b2ea041f716a95299f6.png#pic_center)


公司收入曲线并没有出现急剧下降，可能是由于财务会计的处理。对数据结果进行标准差处理。



```python
def plot_with_std(x, y, stds, ax, title, y_label):
    ax.fill_between(x, y - stds, y + stds, alpha=0.2)
    plot(x, y, ax, title, y_label)
fig, (ax1, ax2) = plt.subplots(ncols=2)
title = 'Increase in mean and std Fortune 500 company %s from 1955 to 2005'
stds1 = group_by_year.std().profit.values
stds2 = group_by_year.std().revenue.values
plot_with_std(x, y1.values, stds1, ax1, title % 'profits', 'Profit (millions)')
plot_with_std(x, y2.values, stds2, ax2, title % 'revenues', 'Revenue (millions)')
fig.set_size_inches(14, 4)
fig.tight_layout()

```

![在这里插入图片描述](https://img-blog.csdnimg.cn/d584d3f008274f9b81a4a31f67596ab0.png#pic_center)


可见，不同公司之间的收入和利润差距惊人，那么到底前10%和后10%的公司谁的波动更大了？此外，还有很多有价值的信息值得进一步挖掘。



分享Notebooks
分享Notebooks通常来说一般存在两种形式：一种向本文一样以静态非交互式分享（html,markdown,pdf等）；另外一种通过Git版本工具或者Google Colab进行协同开发

分享之前的工作
分享的Notebooks应包括代码执行的输出，要保证执行的结果符合预期，需完成以下几件事：

点击"Cell > All Output > Clear"
点击"Kernel > Restart & Run All"
等待所有代码执行完毕
这样做的目的使得Notebook不含有中间的执行结果，按照代码执行的顺序，产生稳定的结果。



## 导出Notebooks

使用"File > Download as"可以以多种格式导出Notebooks，例如：html, pdf, markdown文档等。如果希望以协同方式共享.ipynb，则可以借助相关的在线平台，如[Github](https://github.com/)或者[Google Colab](https://colab.research.google.com/)。




