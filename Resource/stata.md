
## Stata实证分析套路 
+ 基本包括了常见（所有）的量化分析的套路，仅仅是Panel面板数据分析我就尝试了几天没成功，好复杂，还有时间序列分析和离散数据的logistic回归的什么时候用，拿捏不准，来自于知乎，人大论坛等等好多地方的搜集。

数据导入和清洗：
use filename：导入数据文件；
describe：展示数据中的所有变量；
summarize：展示数据中各变量的概要统计信息，包括均值、中位数等；
tabulate varname：展示变量的频数统计信息；
search string或findit string：搜索数据集中是否包含特定字符或字符串；
drop varlist：删除数据集中的指定变量；
gen newvar = expression：创建新变量，根据某些现有变量计算而来；
replace varname = newvalue：将原变量中符合某些条件的值替换为新值；
数据分析：
regress dependent_var indep_var：进行线性回归，确定因变量与一个或多个自变量之间的关系；
logit dependent_var indep_var：进行逻辑回归，研究分类因变量如何被一个或多个自变量影响；
ttest varname, by(group)：进行t检验，用来检验两组样本均值之间是否存在显著差异；
anova depvar indepvar1 indepvar2...indepvarN：进行方差分析，用来研究一个因变量在不同组之间是否存在显著差异；
graph twoway scatter var1 var2，by(group)：绘制散点图，用来观察两个变量之间的关系；
graph box var1, over(var2)：绘制箱线图，用来观察一个变量在不同组之间分布的差异；
xtline depvar, i(timevar)：绘制时间序列图，用来观察某个变量随时间的变化趋势；
数据收集和整理：
input var1 var2：手动输入数据，可以用来填补数据缺失的情况；
append using filename：将两个或多个数据集连接在一起；
merge 1:1 varname using filename：将两个数据集按照共同的变量值连接在一起；
*sort rep78
drop if (rep78 != 1)&(rep78 != 2)

-----
1、input: 输入数据

2、by: 按照某一变量的取值来进行分析

3、weight: 加权或者頻数

4、if: 用条件语句指定条件

5、in:指定观察值的范围，对在范围内的观察值做分析处理

6、for: 用来指定变量

7、函数：

abs(x)      绝对值

exp(x)      指数函数

log(x)       自然对数

log10(x)  常用对数

sqrt(x)      平方根

uniform(x)  生成（0,1）内均匀分布的伪随机数

length(x)   计算长度

substr(s,n1,n2)   获得从S的n1个字符开始的n2个字符组成的字符串

real(x)     将字符串s转换为数值函数

trim(x)      去除字符串前面和后面的空格

int(x)         去掉x的小数部分，得到整数

sum(X)    求和

max(x)  min(x)   最大值最小值

_n        当前观察值的位置

_N       观察值的总个数

8、ren: 重命名

9、des:描述数据库的基本情况

10、label: 为变量添加一些说明，以示说明

11、sort: 按照某一变量从小到大排序

gsort  +/-：按照某一变量从大到小或者从小到大排序

sort var1 var2:按照var1大小排序，相同的var1按照var2大小排序

12、drop:删除变量或者记录

drop _all      //清空数据库

13、keep: 与drop对应，保存变量

14、append:纵向连接数据库

15、merge:横向连接数据库

16、gen: 生成新变量

17、replace:更改变量值

renvars: 批量修改变量名

18、set obs: 增加空记录

19、format: 改变数据格式

20、l: list 将结果列出

21、su: 对分析数据进行描述，均值标准差等，与des不同，des是描述数据库变量个数，格式等

Stata软件 常用命令
22、centile: 百分位数计算

23、tab:頻数表达

24、ci: 计算可信区间

25、直方图：

b1/t1/l1/r1(“”)  给各个坐标轴加标题

b2/t2/l2/r2(“”)  给各个坐标轴加副标题

title  给图加总标题

条图：gra x1 x2, bar by(group) sh(31) l1(“rate of die”) b1(“comparison of rate of die”)

饼图：gra x1 x2 x3 x4 x5, pie by(group) sh(31) total

散点图与线图：connect（简写c）——连接散点的方式：

.   不连接

l   直线连接

s  平滑曲线连接

||  直线连接在同一纵向上的两点

J  阶梯式线条连接

symbol(简写s)——各个散点的图形：

O  大圆圈

S   大方块

T   大三角型

o   小圆圈

d   小菱形

p   小加号

.     小点

gra y x,  xlab ylab c(l) s(d)

箱式图： gra y x, oneway/twoway box

26、方差分析：

方差齐性检验：sdtest x1=x2

sdtest x, by (group)

正态性检验： sktest   x

单因素方差分析：  oneway 相应变量 分组变量

两因素方差分析：anova 相应变量 分组变量1 分组变量2

多因素方差分析：anova x a b c … a*b b*c a*b*c…        //乘积项代表交互作用

27、率、构成比的比较： tab var1  var2 [fw=頻数变量]

chi2  pearson卡方检验

exact  fisher确切概率法

28、等级资料：

genrank  编秩                genrank rankx=x

signtest   符号检验         类似t检验，signtest x=常数，signtest x1=x2, signrank x1=x2

signrank  符号秩和检验

ranksum/Wilcoxon  两样本秩和检验    wilcoxon var, by (group_var)

kwallis    多样本秩和检验（Kruskal-Wallis） kwallis var,by (group_var)

spearman   等级相关                spearman x y

ktau      等级相关（kendall）                 ktau x y

29、直线相关与回归：   相关 corr y x

回归 reg y x

估计与预测 pre yhat

画图 gra y yhat l1 l2 l3 l4 x, c(.lssss) s(oiiii) xlab() ylab()

30、多元线性回归及逐步回归：

散点图矩阵： gra y x1 x2, matrix

相关系数矩阵：  corr

多元回归方程： reg y x1 x2

逐步回归： stepwise y x1-x4, forward fe(2.73)

fe代表fenter选入标准，fs代表fstay剔除标准

逐步回归法：forward,backward,stepwise,stepwise forward

例如：step y x1-x4, step fe(2.5)  fs(2.6) back

31、logistic回归：

logit y x [fw=f]

blogit y x1 x2 x3/ glogit y x1 x2 x3

也可以同上做逐步Logistic回归

32、生存曲线：

中位生存时间：survsum 时间变量 截尾变量, by(分组变量)

生存曲线：kapmeier 时间变量 截尾变量, by(分组变量) // kaplan-meier生存曲线

生存率比较： 两组：wilcoxon 时间变量 截尾变量, by(分组变量)

多组：logrank 时间变量 截尾变量, by(分组变量)

COX分析： cox 时间变量 自变量， dead(截尾变量)
导入间隔符为制表符或逗号等格式 的文本文件：insheet

导入固定列格式的文件：infix

导入自由格式的文本文件：infile

导入XML格式文件：xmluse

更改变量的存储格式：recast

建立新变量：generate或egen

重命名变量rename

变量排序：order

删除变量或观测值：drop

生成分类变量：recode

字符串与数值变量间转换：destring或encode

升序或降序排列：gsort

升序排列：sort

检查数据是否存在重复观测值：isid

报告、标记或删除重复观测值：duplicates

长数据与宽数据间转换：reshape

生成变量的统计指标数据：collapse

横向合并数据：merge

纵向添加数据：append

根据组内配对合并变量：joinby

标量：scalar

随机抽样：sample

有放回的抽样：bsample

从多元正态分布随机变量中抽样：drawnorm

生成特定相关结构的变量：corr2data

统计制图

直方图：histogram

一般绘图命令：graph或twoway

对称图：symplot

分位数图：quantile

正态分布分位数图：qmorm

QQ分位数图：qqplot

标准化正态概率图：pnorm

描述统计

数据概要描述：summarize或describe

生成汇总统计表：tabstat或tabulate

相关性：correlate或pwcorr

假设检验

t检验：ttest

方差检验：sdtest

比率检验：prtest

二项概率检验：bitest

K-S检验：ksmirnov

符号检验：signtest

Wilcoxon符号秩检验：signrank

Wilcoxon秩和检验：ranksum

Kruskal-Wallis：H检验：kwallis

方差分析

方差分析：anova

单因素方差分析：oneway

多元统计分析

主成分分析：pca

主成分散点图：loadingplot

因子分析：factor

因子旋转：rotate

模型适切度检验：estat smc及estat anti及estat kmo

计算主成分得分或因子得分：predict

碎石图：screeplot

聚类分析：cluster

典型相关分析：canon

回归分析

OLS线性回归：regress

受约束的线性回归：cnsreg

非线性最小二乘估计：nl

多变量回归：mvreg

似不相关回归：sureg

Probit回归：probit

Logistic回归：logit

定序probit模型：oprobit

定序logit模型：ologit

归并模型：cnreg

Tobit模型：tobit

多层线性模型：mixed

泊松回归：poisson

负二项回归：nbreg

时间序列分析

定义时间序列：tsset

ARIMA，ARMAX和其它动态回归模型：arima

自相关：ac

偏自相关：pac

预测：predict

时间序列图：tsline

蒙特卡罗模拟：simulate

ADF单位根检验：dfuller

PP单位根检验pperron

DF-GLS单位根检验：dfgls

跨相关图：xcorr

结构向量自回归模型：svar

自回归条件异方差模型：arch

门限回归：threg

状态空间模型：sspace

面板数据分析

定义面板：xtset

面板数据结构：xtdescribe

面板OLS模型：xtreg

面板GLS模型：xtgls

面板GEE模型：xtgee

面板probit模型：xtprobit

面板logit模型：xtlogit

差分GMM模型：xtabond

系统GMM模型：xtdpdsys

Hausman检验：hausman

似然比检验：lrtest

空间计量
使用 "tabulate" 命令：它可以通过频数和百分比来对单个变量进行分组。例如：tabulate 变量名

使用 "collapse" 命令：您可以使用此命令对多个变量进行分组并计算其平均值、总和等。例如：collapse (mean) 变量名, by(分组变量名)

使用 "group" 命令：您可以使用此命令对单个变量根据其值的范围进行分组。例如：group 变量名, into(分组名1 数学表达式1 分组名2 数学表达式2 ...)

前10笔观察值 dataex in 1/10
mean varname [if exp] [in range] [, options]
其中：

varname 是要求平均值的变量名。
if exp 是一个表达式，表示只对满足该条件的数据进行求平均值。
in range 表示对指定的范围内的数据进行求平均值。
options 是可选参数，可以用来控制输出的格式。