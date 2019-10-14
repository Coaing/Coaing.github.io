---
layout:     post
title:      Data-Mining-1
subtitle:   Data-Mining之数据探索
date:       2019-09-03
author:     XU
header-img: img/post-bg-cook.jpg
catalog: 	 true
tags:
    - DataMining
---

# 一、数据探索

通过检验数据集的数据质量、绘制图表、计算某些特征量等手段，对样本数据集的结构和规律进行分析的过程就是数据探索。

数据探索有助于选择合适的数据预处理和建模方法，甚至可以完成一些通常由数据挖掘解决的问题。

接下来将从数据质量分析和数据特征分析两个角度对数据进行探索

## 1.1 数据质量分析

数据质量分析的主要任务是检查原始数据中是否存在脏数据，脏数据一般是指不符合要求，以及不能直接进行相应分析的数据。在常见的数据挖掘工作中，脏数据包括如下内容：

- 缺失值
- 异常值
- 不一致的值
- 重复数据及含有特殊符号（如"#、￥、* "）的数据

接下来将主要对数据中的缺失值、异常值和一致性进行分析

### 1.1.1 缺失值分析

数据的缺失主要包括记录的缺失和记录中某个字段信息的缺失，两者都会造成分析结果的不准确

缺失值的影响

1）数据挖掘建模将丢失大量的有用信息

2）数据挖掘模型所表现出的不确定性更加显著，模型中蕴涵的规律更难把握

3）包含空值的数据会使建模过程陷入混乱，导致不可靠的输出

使用简单的统计分析，可以得到含有缺失值的属性的个数，以及每个属性的未缺失数、缺失数与缺失率等

从总体上来说，缺失值的处理分为删除存在缺失值的记录、对可能值进行插补和不处理3种情况

### 1.1.2异常值分析
异常值分析是检验数据是否有录入错误以及含有不合常理的数据。

忽视异常值的存在是十分危险的，不加剔除地把异常值包括进数据的计算分析过程中，对结果会产生不良影响；

重视异常值的出现，分析其产生的原因，常常成为发现问题进而改进决策的契机

异常值是指样本中的个别值，其数值明显偏离其余的观测值。异常值也称为离群点，异常值的分析也称为离群点分析。

(1)简单的统计量分析

最大值、最小值是否超过合理的范围

(2)若服从正态分布，可以采用3σ原则

偏差超过3倍标准差的值，在正态分布的假设下，距离平均值3σ之外的值出现的概率为P（|x-u|>3σ）≤ 0.003，属于极个别的小概率事件

如果数据不服从正态分布，也可以用远离平均值的多少倍标准差来描述

（3）箱型图分析
箱型图提供了识别异常值的一个标准：异常值通常被定义为小于QL-1.5IQR或大于QU+1.5IQR的值，QL称为下四分位数，表示全部观察值中有四分之一的数据取值比它小；

QU称为上四分位数，表示全部观察值中有四分之一的数据取值比它大；IQR称为四分位数间距，是上四分位数QU与下四分位数上界

QL之差，其间包含了全部观察值的一半

箱型图识别异常值的结果比较客观，在识别异常值方面有一定的优越性

![箱型图](https://raw.githubusercontent.com/codlx/codlx.github.io/master/img/box-figure.png "箱型图")

## 1.2数据特征分析

### 1.2.1分布分析

分布分析能揭示数据的分布特征和分布类型。

1、对于定量数据，欲了解其分布形式是对称的还是非对称的，发现某些特大或特小的可疑值，可通过绘制频率分布表、绘制频率分布

直方图、绘制茎叶图进行直观地分析；对于定性分类数据，可用饼图和条形图直观地显示分布情况。

（1）求极差

极差=最大值一最小值=3960-45=3915

（2）分组
eg:
这里根据业务数据的含义，可取组距为500

组数=极差/组距=3915/500=7.83÷8


2.定性数据的分布分析

对于定性变量，常常根据变量的分类类型来分组，可以采用饼图和条形图来描述定性变量的分布。

饼图的每一个扇形部分代表每一类型的百分比或频数，根据定性变量的类型数目将饼图分成几个部分，每一部分的大小与每一类型的频数成正比；条形图的高度代表每一类型

的百分比或频数，条形图的宽度没有意义。

3、对比分析

### 1.2.3统计量分析

用统计指标对定量数据进行统计描述，常从集中趋势和离中趋势两个方面进行分析。

平均水平的指标是对个体集中趋势的度量，使用最广泛的是均值和中位数；

反映变异程度的指标则是对个体离开平均水平的度量，使用较广泛的是标准差（方差）、四分位间距。

1、集中趋势

(1)均值

(2)中位数

(3)众数

2、离中趋势

(1)极差

(2)标准差

(3)四分位数间距

四分位数包括上四分位数和下四分位数。将所有数值由小到大排列并分成四等份，处于第一个分割点位置的数值是下四分位数，

处于第二个分割点位置（中间位置）的数值是中位数，处于第三个分割点位置的数值是上四分位数。

四分位数间距，是上四分位数与下四分位数之差，其间包含了全部观察值的一半。其值越大，说明数据的变异程度越大；反之，说明变异程度越小。

(4)变异系数

变异系数度量标准差相对于均值的离中趋势

std/mean

```
catering_sale = '../data/catering_sale.xls' #餐饮数据
data = pd.read_excel(catering_sale, index_col = u'日期') #读取数据，指定“日期”列为索引列
data = data[(data[u'销量'] > 400)&(data[u'销量'] < 5000)] #过滤异常数据
statistics = data.describe() #保存基本统计量

statistics.loc['range'] = statistics.loc['max']-statistics.loc['min'] #极差
statistics.loc['var'] = statistics.loc['std']/statistics.loc['mean'] #变异系数
statistics.loc['dis'] = statistics.loc['75%']-statistics.loc['25%'] #四分位数间距

print(statistics)

"""
          销量
count   195.000000
mean   2744.595385
std     424.739407
min     865.000000
25%    2460.600000
50%    2655.900000
75%    3023.200000
max    4065.200000
range  3200.200000
var       0.154755
dis     562.600000

"""

```

### 1.2.4周期性分析你

### 1.2.5贡献度分析

贡献度分析又称帕累托分析，它的原理是帕累托法则，又称20/80定律。

同样的投入放在不同的地方会产生不同的效益。

例如，对一个公司来讲，80%的利润常常来自于20%最畅销的产品，而其他80%的产品只产生了20%的利润。

### 1.2.6相关性分析

分析连续变量之间线性相关程度的强弱

1、直接绘制散点图

2、计算相关系数

(1)Pearson系数

Pearson线性相关系数要求连续变量的取值服从正态分布。

相关系数r的取值范围：-1 ≤ r ≤ 1

r>0为正相关，r<0为负相关

|r|=0表示不存在线性关系

|r|=1表示完全线性相关

0<|r|<1表示存在不同程度线性相关：

|r|≤0.3为不存在线性相关

|0.3<|r|≤0.5为低度线性相关|0.5<|r|≤0.8为显著线性相关|r|>0.8为高度线性相关

(2)Spearman系数

不服从正态分布的变量、分类或等级变量之间的关联性可采用Spearman秩相关系数，也称等级相关系数来描述。

```
import pandas as pd

catering_sale = '../data/catering_sale_all.xls' #餐饮数据，含有其他属性
data = pd.read_excel(catering_sale, index_col = u'日期') #读取数据，指定“日期”列为索引列

data.corr() #相关系数矩阵，即给出了任意两款菜式之间的相关系数

data.corr()[u'百合酱蒸凤爪'] #只显示“百合酱蒸凤爪”与其他菜式的相关系数

data[u'百合酱蒸凤爪'].corr(data[u'翡翠蒸香茜饺']) #计算“百合酱蒸凤爪”与“翡翠蒸香茜饺”的相关系数

"""
              百合酱蒸凤爪	   翡翠蒸香茜饺	金银蒜汁蒸排骨	乐膳真味鸡	蜜汁焗餐包	生炒菜心	铁板酸菜豆腐	香煎韭菜饺	香煎罗卜糕	原汁原味菜心
百合酱蒸凤爪      1.000000	      0.009206	0.016799	0.455638	0.098085	0.308496	0.204898	0.127448	-0.090276	0.428316
翡翠蒸香茜饺    	0.009206	        1.000000	0.304434	-0.012279	0.058745	-0.180446	-0.026908	0.062344	0.270276	0.020462
金银蒜汁蒸排骨	   0.016799	       0.304434	1.000000	0.035135	0.096218	-0.184290	0.187272	0.121543	0.077808	0.029074
乐膳真味鸡 	    0.455638	          -0.012279	0.035135	1.000000	0.016006	0.325462	0.297692	-0.068866	-0.030222	0.421878
蜜汁焗餐包	      0.098085	           0.058745	0.096218	0.016006	1.000000	0.308454	0.502025	0.155428	0.171005	0.527844
生炒菜心	       0.308496	           -0.180446	-0.184290	0.325462	0.308454	1.000000	0.369787	0.038233	0.049898	0.122988
铁板酸菜豆腐	   0.204898	       -0.026908	0.187272	0.297692	0.502025	0.369787	1.000000	0.095543	0.157958	0.567332
香煎韭菜饺	    0.127448	           0.062344	0.121543	-0.068866	0.155428	0.038233	0.095543	1.000000	0.178336	0.049689
香煎罗卜糕	    -0.090276	           0.270276	0.077808	-0.030222	0.171005	0.049898	0.157958	0.178336	1.000000	0.088980
原汁原味菜心	  0.428316	         0.020462	0.029074	0.421878	0.527844	0.122988	0.567332	0.049689	0.088980	1.000000
"""

"""
百合酱蒸凤爪     1.000000
翡翠蒸香茜饺     0.009206
金银蒜汁蒸排骨    0.016799
乐膳真味鸡      0.455638
蜜汁焗餐包      0.098085
生炒菜心       0.308496
铁板酸菜豆腐     0.204898
香煎韭菜饺      0.127448
香煎罗卜糕     -0.090276
原汁原味菜心     0.428316
Name: 百合酱蒸凤爪, dtype: float64
"""

"""
0.009205803051836475
"""
```

## 1.3Python主要数据探索函数

### 1.3.1基本统计特征函数

sum() 计算数据样本的总和（按列计算）|Pandas

mean()  计算数据样本的算术平均数|Pandas

var()   计算数据样本的方差|Pandas

std()   计算数据样本的标准差|Pandas

corr()  计算数据样本的Spearman（method='Pearson'）相关系数矩阵|Pandas

cov()   计算数据样本的协方差矩阵|Pandas

skew()  样本值的偏度（三阶矩）|Pandas

kurt()  样本值的峰度（四阶矩）|Pandas

describe()给出样本的基本描述（基本统计量如均值、标准差等）|Pandas

```
D=pd.DataFrame([range(1,8),range(2,9)1)#生成样本D,一行为1~7,一行为2~8

D.corr(method='spearson')#计算相关系数矩阵

S1=D.loc[0]#提取第一行

S2=D.loc[1]#提取第二行

S1.corr(S2,method='pearson')#计算S1、S2的相关系数

```