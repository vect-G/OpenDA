本章仅限于介绍矩形脉冲波形的产生和整形电路。

本章主要分析方法：

- 不到万不得已，绝不打开门电路。
- 所有门电路的输出都当成有内阻的电压源。

## 概述

获取矩形脉冲波形的途径不外乎两种:一种是利用各种形式的多谐振荡电路直接产生所需要的矩形脉冲,另一种则是通过各种整形电路将已有的周期性变化波形变换为符合要求的矩形脉冲。当然,在采用整形的方法获取矩形脉冲时,是以能够找到频率和幅度都符合要求的一种已有电压信号为前提的。

![image-20211212033558720](Pulse%20Wave.assets/image-20211212033558720.png)

在同步时序电路中，作为时钟信号的矩形脉冲控制和协调着整个系统的工作，因此，时钟脉冲的特性直接关系到系统能否正常地工作。为了定量描述矩形脉冲的特性，通常给出以下的主要参数：

- 脉冲周期T。周期性重复的脉冲序列中，两个相邻脉冲之间的时间间隔，有时也使用频率$f=\frac{1}{T}$表示单位时间内脉冲重复的次数
- 脉冲幅度$V_m$，脉冲电压的最大变化幅度
- 脉冲宽度$t_W$，从脉冲前沿到达$0.5V_m$起，到脉冲后沿到达$0.5V_m$为止的一段时间。
- 上升时间$t_r$，脉冲上升沿从$0.1 V_{\mathrm{m}}$ 上升到 $0.9 V_{\mathrm{m}}$ 所需要的时间
- 下降时间$t_f$, 脉冲下降沿从 $0.9 V_{\mathrm{m}}$ 下降到 $0.1 V_{m}$所需要的时间
- 占空比 $q$ ——脉冲宽度与脉冲周期的比值,亦即 $q=t_{\mathrm{w}} / T$

对于一个门电路与电阻组合电路的分析：

![image-20211212153429695](Pulse%20Wave.assets/image-20211212153429695.png)

分情况讨论电路的变化情况：

![image-20211212153751237](Pulse%20Wave.assets/image-20211212153751237.png)

![image-20211212153853739](Pulse%20Wave.assets/image-20211212153853739.png)

通过以上的分析可以得到这样的输入输出特性曲线：

![image-20211212154821267](Pulse%20Wave.assets/image-20211212154821267.png)

而这正是用门电路组成的施密特触发器。

![image-20211212165613110](Pulse%20Wave.assets/image-20211212165613110.png)

如果$R_1 > R_2$怎么样？应该从定性分析入手，即分类进行讨论并观察电压的变化情况，即物理情况，如果$R_1 > R_2$，则即使$V_I$达到了$V_{DD}$,则$V_A$也无法到达$V_{TH}$,则电路就被锁死了，无法翻转。

## 施密特触发电路

![image-20211212155716997](Pulse%20Wave.assets/image-20211212155716997.png)

![image-20211212155940196](Pulse%20Wave.assets/image-20211212155940196.png)

![image-20211212162752277](Pulse%20Wave.assets/image-20211212162752277.png)

![image-20211212163313939](Pulse%20Wave.assets/image-20211212163313939.png)

施密特触发电路的应用相当广泛，不仅有单独做成的集成电路产品，而且也经常被用作某些集成电路的输入接口电路。

![image-20211212163428876](Pulse%20Wave.assets/image-20211212163428876.png)

![image-20211212164550912](Pulse%20Wave.assets/image-20211212164550912.png)

为了降低输出电阻以提高电路的驱动能力，在整个电路的输出部分设置了倒向级和推拉式输出级电路。

![image-20211212164658191](Pulse%20Wave.assets/image-20211212164658191.png)

下图为集成施密特触发电路7413的电压传输特性。对每个具体的器件而言，它的$V_{T+} 、V_{T-}$都是固定的，不能调节。

![image-20211212164818174](Pulse%20Wave.assets/image-20211212164818174.png)

## 施密特触发电路的应用

### 波形变换

利用施密特触发电路状态转换过程中的正反馈作用，可以将边沿变化缓慢的周期性信号变换为边沿很陡的矩形脉冲信号。

如下，输入信号是由直流分量和正弦分量叠加而成的，只要输入信号的幅度大于$V_{\mathrm{T+}}$，即可在施密特触发电路的输出端得到同频率的矩形脉冲信号。

![image-20211212165835605](Pulse%20Wave.assets/image-20211212165835605.png)

### 鉴幅

![image-20211212173304999](Pulse%20Wave.assets/image-20211212173304999.png)

### 脉冲整形

在数字系统中，矩形脉冲经传输后往往发生波形畸变。

当传输线上电容较大时，波形的上升沿和下降沿将明显变化，如图（a）所示；当传输线较长，且接收端的阻抗与传输线的阻抗不匹配时 ，在波形的上升沿和下降沿将产生振荡现象，如图（b）所示，当其它脉冲信号通过导线间的分布电容或公共电源线叠加到矩形脉冲信号上时，信号上将出现附加的噪声，如图（c）所示。

![image-20211212173624800](Pulse%20Wave.assets/image-20211212173624800.png)

以上情况都可以通过施密特触发电路整形而获得比较理想的矩形脉冲波形。只要施密特触发电路的$V_{\mathrm{T+}}$ 和 $V_{\mathrm{T}-}$设置的合适，均能获得满意的整形效果。

## 单稳态触发电路

![image-20211212175101015](Pulse%20Wave.assets/image-20211212175101015.png)

### 用门电路组成的单稳态电路

单稳态电路的暂稳态通常都是靠RC电路的充、放电过程来维持的，根据RC电路的不同接法，将单稳态电路分为微分型和积分型两种。

#### 积分型单稳态电路

![image-20211212175845061](Pulse%20Wave.assets/image-20211212175845061.png)

这个电路用正脉冲触发。

![image-20211212181413912](Pulse%20Wave.assets/image-20211212181413912.png)

输出脉冲的宽度等于从电容C开始放电的一刻到$V_A$下降至$V_{TH}$的时间。为了计算$t_w$,需要画出电容C放电的等效电路。鉴于$V_A$高于$V_{TH}$期间$G_2$的输入电流非常小，可以忽略不计，因而电容C放电的等效电路可以简化为$(R+R_o)$与C串联，这里的$R_O$是$G_1$输出为低电平时的输出电阻。

![image-20211212182536553](Pulse%20Wave.assets/image-20211212182536553.png)

将$v_{c}(0)=V_{OH}, v_{c}(\infty)=V_{OL}$代入公式可得：
$$
t_{w}=\left(R+R_{0}\right) C \ln \frac{V_{OL}-V_{\text {OH}}}{V_{\mathrm{OL}}-V_{\text {TH}}}
$$
输出脉冲的幅度则为：
$$
V_{\mathrm{m}}=V_{\mathrm{OH}}-V_{\mathrm{OL}}
$$
![image-20211212182741313](Pulse%20Wave.assets/image-20211212182741313.png)

#### 微分型单稳态电路

![image-20211212192059106](Pulse%20Wave.assets/image-20211212192059106.png)

![image-20211212192826179](Pulse%20Wave.assets/image-20211212192826179.png)

> 这里说的电容上的电压不可能发生突跳，是说两个极板间的电压差不能发生突变，原来电压差为0，故现在电压差也应为0

![image-20211212192957106](Pulse%20Wave.assets/image-20211212192957106.png)

![image-20211212193228643](Pulse%20Wave.assets/image-20211212193228643.png)

> 注意$V_{12}$那里的一个“尖”，如果更仔细地刻画的话应该是先升到1.5$V_{DD}$,再迅速地降至$V_{DD}+1.7$

![image-20211212193314189](Pulse%20Wave.assets/image-20211212193314189.png)

![image-20211212193611691](Pulse%20Wave.assets/image-20211212193611691.png)

脉冲电路的分析方法：

- 分析工作过程、画波形、画出决定电路状态转变的关键电压
- 画出这点电压充、放电等效电路，化简
- 确定并修订充放电的几个关键值
- 计算充放电时间，求出所需要的结果

关键公式：
$$
t_{W}=R C \ln \frac{V_{(\infty)}-V_{(0)}}{V_{(\infty)}-V_{(t)}}
$$

$$
t_{r e}=(3 \sim 5)\left(R / / r_{D 1}+R_{O N}\right) C \approx(3 \sim 5) R_{O N} C
$$

$$
t_{d}=t_{w}+t_{r e}
$$

输出脉冲宽度$\left(V_{o}=1\right.$ 时间 $)$ 等于 $V_{12}$ 从 0 充电至 $V_{T H}$ 的时间

### 集成单稳态电路

在TTL和CMOS电路的产品中，都生产了单片集成的单稳态电路器件。使用这些器件时只需要很少的外接元件和连线，而且器件内部电路一般还附加了上升沿与下降沿触发的控制和置零功能，使用较为方便。

下图为TTL集成单稳态电路74121简化的原理性逻辑图，它是在普通微分型单稳态电路的基础上附加以输入控制电路和输出缓冲电路而形成的。

![image-20211221202410179](Pulse%20Wave.assets/image-20211221202410179.png)

![image-20211221202434957](Pulse%20Wave.assets/image-20211221202434957.png)

根据门$G_6$输出端的电路结构和门$G_7$输入端的电路结构可以求出计算输出脉冲宽度的公式：$t_{\mathrm{w}} \approx R_{\mathrm{ext}} C_{\mathrm{ex}} \ln 2=0.69 R_{\mathrm{ext}} C_{\mathrm{ext}}$

![image-20211221202558469](Pulse%20Wave.assets/image-20211221202558469.png)

![image-20211221202721882](Pulse%20Wave.assets/image-20211221202721882.png)

## 多谐振荡电路

多谐振荡电路（Astable Multivibrator）是一种自激振荡电路，在接通电源以后，不需要外加触发信号，便能自动地产生矩形脉冲。由于矩形波中含有丰富的高次谐波分量，所以习惯上又将矩形波振荡电路称为多谐振荡电路。

### 用施密特触发器构成的多谐振荡器

![image-20211222130906857](Pulse%20Wave.assets/image-20211222130906857.png)

![image-20211222130951090](Pulse%20Wave.assets/image-20211222130951090.png)

$T=T_{1}+T_{2}=R C \ln \frac{V_{D D}-V_{T-}}{V_{D D}-V_{T_{+}}}+R C \ln \frac{0-V_{T_{+}}}{0-V_{T_{-}}}$

那么如何调整相关参数呢？利用二极管的单向导电性！

![image-20211222131211223](Pulse%20Wave.assets/image-20211222131211223.png)

$T=T_{1}+T_{2} \approx R_{2} C \ln \frac{V_{D D}-V_{T-}}{V_{D D}-V_{T+}}+R_{1} C \ln \frac{0-V_{T+}}{0-V_{T-}}$

### 环形振荡器

#### 最简单的环形振荡器

利用闭合回路中的延迟负反馈作用同样也能产生自激振荡，只要负反馈信号足够强。环形振荡电路就是利用延迟负反馈产生振荡的，它是利用门电路的传输延迟时间将奇数个反相器首尾相接而构成的。

![image-20211222131959789](Pulse%20Wave.assets/image-20211222131959789.png)

由三个反相器构成的电路的输入输出特性曲线和由一个反相器构成的电路类似，而输出和输入连接起来相当于过原点斜率为45度的直线。其图解法过程如下：

![image-20211222132155587](Pulse%20Wave.assets/image-20211222132155587.png)

则由于输入的细微变化也会产生很大的偏移，因此整个电路处于不稳定的状态，即开始振荡。

![image-20211222133718886](Pulse%20Wave.assets/image-20211222133718886.png)

从波形图中可以看出，振荡的周期为$6t_{PD}$（高电平$3t_{PD}$，低电平$3t_{PD}$）。且基于上述原理可知，将任何大于、等于3的奇数个反相器首尾相连地接成环形电路，都能产生自激振荡，而且振荡周期为$T=2 n t_{\mathrm{pd}}$，其中n为串联反相器的个数。

但是问题是，振荡的周期由于和电路中的$t_{PD}$有关，因此不好改变也很难控制。并且，门电路的传输延迟时间极短，TTL电路只有几十纳秒，CMOS电路也不过一二百纳秒，所以想获得稍低一些的振荡频率是很困难的。

#### 实用的环形振荡器

![image-20211222133950208](Pulse%20Wave.assets/image-20211222133950208.png)

为了能够控制电路振荡的时间参数，我们首先想到了第一步，即将中间的反相器外接RC延迟电路。

但是，对波形进行分析，开始未上电时电容电压为0，G2输出端电压为1，开始充电，充到$V_{TH}$后，由于电路延迟，还要经过$3t_{PD}$G2才会变成0，因此继续充电；$3t_{PD}$后，G2变成0，电容开始放电，假设经过$3t_{PD}$放电到$V_{TH}$，同理由于传输延迟时间，经过$3t_{PD}$后G2才会变成1，因此继续放电。从整个过程中我们可以看出，我们虽然接入了电阻电容，但是对整个电路的时间没有什么改变，只是把整个振荡周期延长到了12$t_{PD}$而已。这就像生活中我们用一个大水桶蓄水，但是每次只用到水桶的很小一部分一样。

![image-20211222135119684](Pulse%20Wave.assets/image-20211222135119684.png)

我们把电容接到前端：

![image-20211222135736336](Pulse%20Wave.assets/image-20211222135736336.png)

> 核心：电容上的电压不能发生突变，所以当$v_{12}$电压发生变化时，通过电容先传达到了$v_{13}$，而$v_{O2}$处还要经过$t_{PD}$才会发生改变，所以发生了电容的充放电。

![image-20211222140129039](Pulse%20Wave.assets/image-20211222140129039.png)

![image-20211222140212477](Pulse%20Wave.assets/image-20211222140212477.png)

![image-20211222140230008](Pulse%20Wave.assets/image-20211222140230008.png)

### 非对称式多谐振荡器

以CMOS反相器组成的非对称多谐振荡电路为例说明其工作原理：

![image-20211222141728444](Pulse%20Wave.assets/image-20211222141728444.png)

![image-20211222141801189](Pulse%20Wave.assets/image-20211222141801189.png)

![image-20211222141957058](Pulse%20Wave.assets/image-20211222141957058.png)

![image-20211222142010433](Pulse%20Wave.assets/image-20211222142010433.png)

![image-20211222142039569](Pulse%20Wave.assets/image-20211222142039569.png)

![image-20211222142048759](Pulse%20Wave.assets/image-20211222142048759.png)

![image-20211222142122854](Pulse%20Wave.assets/image-20211222142122854.png)

### 对称式多谐振荡器

![image-20211222210717586](Pulse%20Wave.assets/image-20211222210717586.png)

为了产生自激振荡，电路不能有稳定状态，也就是说，在静态下（电路没有振荡时）它的状态必须是不稳定的，所以必须让$G_1$和$G_2$工作在放大状态。

![image-20211222211109405](Pulse%20Wave.assets/image-20211222211109405.png)

![image-20211222211252709](Pulse%20Wave.assets/image-20211222211252709.png)

这条直线与电压传输特性的交点就是反相器的静态工作点。只要恰当地选取$R_{FI}$值，定能使静态工作点P位于电压传输特性的转折区，计算结果表明，对于74系列的门电路而言，$R_{FI}$的阻值应取在$0.5 \sim 1.9 \mathrm{k} \Omega$之内。

![image-20211222214907119](Pulse%20Wave.assets/image-20211222214907119.png)

![image-20211222214939202](Pulse%20Wave.assets/image-20211222214939202.png)

![image-20211222215249180](Pulse%20Wave.assets/image-20211222215249180.png)

这个电路是有浪费的。因为静态时$G_1$工作在电压传输特性的转折区，所以只要把它的输出电压直接接到$G_2$的输入端，$G_2$即可得到一个介于高、低电平之间的静态偏置电压，从而使$G_2$的静态工作点也处于电压传输特性的转折区上，因此可以把$C_{1}$ 和 $R_{F2}$去掉

### 石英晶体多谐振荡器

![image-20211222220704326](Pulse%20Wave.assets/image-20211222220704326.png)

## 555定时器及其应用

555定时器是一种多用途的数字-模拟混合集成电路，利用它能极方便地构成施密特触发电路、单稳态电路和多谐振荡电路，且是目前产量最高的芯片。

![image-20211222223645444](Pulse%20Wave.assets/image-20211222223645444.png)

![image-20211222224039170](Pulse%20Wave.assets/image-20211222224039170.png)

![image-20211222224154291](Pulse%20Wave.assets/image-20211222224154291.png)

可以设想， 如果使$v_{\mathrm{C1}}$ 和 $v_{\mathrm{C2}}$的高电平信号发生在输入电压信号的不同电平，那么输出与输入之间的关系将为施密特触发特性；如果在$v_{12}$加入一个低电平触发信号以后，经过一定的时间能在$v_{\mathrm{CI}}$输入端自动产生一个高电平信号，就可以得到单稳态电路；如果能使$v_{\mathrm{C1}}$ 和 $v_{\mathrm{C2}}$的高电平信号交替地反复出现，就可以得到多谐振荡电路。

### 用555定时器接成施密特触发电路

![image-20211222225807012](Pulse%20Wave.assets/image-20211222225807012.png)

![image-20211222225940055](Pulse%20Wave.assets/image-20211222225940055.png)

### 用555定时器接成单稳态电路

![image-20211222231244681](Pulse%20Wave.assets/image-20211222231244681.png)

![image-20211222231303507](Pulse%20Wave.assets/image-20211222231303507.png)

注意，这里要求输入电压$V_I$不能太宽，但是，如果$V_I$很宽呢？这里应该利用微分电路，使得“只取一个尖”。

这个电路是否能够重复触发？重复触发的要求是，哪怕充到一半，只要来一个触发脉冲，就重新开始充电。我们实现的思路是，在脉冲来到的时候给C放电，所以我们在外边再接入一个三极管，在脉冲来到后，给电容进行放电。

### 用555定时器接成的多谐振荡电路

既然用555定时器能够很方便地接成施密特触发电路，那么我们就可以把它接成施密特触发电路，然后在施密特触发电路的基础上改接成多谐振荡电路。



![image-20211222231755012](Pulse%20Wave.assets/image-20211222231755012.png)

![image-20211222231828803](Pulse%20Wave.assets/image-20211222231828803.png)

![image-20211222231907568](Pulse%20Wave.assets/image-20211222231907568.png)

![image-20211222231932890](Pulse%20Wave.assets/image-20211222231932890.png)

![image-20211222232145127](Pulse%20Wave.assets/image-20211222232145127.png)

![image-20211222232211017](Pulse%20Wave.assets/image-20211222232211017.png)

