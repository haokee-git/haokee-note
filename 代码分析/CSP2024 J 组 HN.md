## 总览

一共有 $10,903$ 个文件夹，$8,481$ 个文件，这代表着有 $2,422$ 个文件夹里面没有源代码文件。最大选手文件夹编号为 HN-J02450，但只有 $2,289$ 个选手文件夹，至少 $161$ 名选手没有代码。

获得最长代码的是 HN-J00767 的 poker.cpp（并且 ta 没有开子文件夹），ta 的代码长度达到了 $26.6$ M。远看过去祥和，但是……

![[csp2024jhn23.png#pic_center]]

![[csp2024jhn24.png#pic_center]]

![[csp2024jhn25.png#pic_center]]

## 细节

### 头文件

共有 $9,081$ 个 `#include`，其中 $7,878$ 个文件包含了万能头，当中的选手 HN-J00015 使用了独树一帜的神奇操作。

![[csp2024jhn3.png#pic_center]]

### CCF

共有 $15$ 个文件出现了 CCF。出现 I love CCF 字眼的考号为：HN-J00654、HN-J00865、HN-J01116、HN-J01471、HN-J01639、HN-J01639、HN-J01639、HN-J01991，其中 HN-J00865 将 I love CCF 重复了十遍，运用反复的写作手法写出了作者对 CCF 的喜爱。

![[csp2024jhn2.png#pic_center]]

值得注意的是，没有一个文件出现了 fxxk/sxxt 的字眼，看来本届考生相对来说较为文明。没有在代码中发现表白的，看来选手们对 CCF 的喜爱远胜于其他人。

---

好家伙全字匹配忘关了，关掉还是有文明人的。HN-J00078 定义了宏常量 sbccf，HN-J00190 定义了数组 bydccf。

![[csp2024jhn26.png#pic_center]]

![[csp2024jhn27.png#pic_center]]

HN-J01550 还在代码内阐述了事实。

![[csp2024jhn28.png#pic_center]]

### y1

$108$ 个文件出现了 y1 作为变量名，向它们致敬。

![[csp2024jhn21.png#pic_center]]

### china

喜报！HN-J00943 将 chain 写成了 china，血的教训。

![[csp2024jhn22.png#pic_center]]

### 文件读写

考号为 HN-J00151、HN-J00283、HN-J00318、HN-J00447、HN-J00492、HN-J0073、HN-J00810、HN-J00922、HN-J00954、HN-J01015、HN-J01015、HN-J01127、HN-J01142、HN-J01151、HN-J01299、HN-J01345、HN-J01471、HN-J01690、HN-J01768、HN-J01774、HN-J01819、HN-J01990、HN-J02142、HN-J02191、HN-J02292、HN-J02317、HN-J02362 等的选手的输出文件后缀均为 .ans，这就是不仔细看比赛注意事项的后果。

![[csp2024jhn1.png#pic_center]]

已知 $9$ 名选手将后缀名 .cpp 放到了子文件夹的名字的里面。

### 数据类型

只有 $1,976$ 个文件使用了 int，但是总数量达到了 $20,006$ 个。有 $667$ 个文件使用了 signed 替代 int。共有 $1,847$ 个文件使用了 long long，有 $406$ 个文件使用了 ll 或 LL 进行替代。

$3,033$ 个文件使用了 char，$2,110$ 个文件使用了 string，$281$ 个文件使用了 [[vector]]，set 存在于 $103$ 个文件当中，没有选手使用 multiset，只有 $7$ 个文件使用了 unordered_set，[[map]] 存在于 $516$ 个文件当中，没有选手使用 multimap，unordered_map 倒是在 $26$ 个文件中出现，只有 HN-J00862 和 HN-J02131 使用了 [[deque]]，没有人使用 list 替代 deque，没有人使用 basic_string 替代 vector。

只有 $2$ 位巨佬：HN-J00176、HN-J00999 使用了冷门的 array。

![[csp2024jhn4.png#pic_center]]

### 输入输出

$3,127$ 个文件使用了 cin，$2,249$ 个文件使用了 cout；$601$ 个文件使用了 cout，$535$ 个文件使用了 printf。单从数量上来看，输入输出流远胜于标准 IO。

$150$ 个文件定义了 read 函数，应该均为手写快读的；但是只有 $46$ 个文件定义了 write，看来大部分选手希望更快的输入而不是输出。

$8,171$ 个文件使用了 freopen 作为文件读写，只有 $56$ 份代码使用了 i/ofstream。这证明 freopen 还是广大竞赛选手进行文件读写的方式。

但是约莫 $226$ 个文件将 freopen 注释了。。。

![[csp2024jhn6.png#pic_center]]

### 诈骗

只有一位选手 HN-J02066 使用了 Never Gonna Give You Up 施行诈骗。 

![[csp2024jhn7.png#pic_center]]

### 注释

$1,414$ 个文件使用了单行注释，只有 $334$ 个文件使用了多行注释。

### AFO

有 $7$ 个文件里面出现了 AFO 的字眼，祝福 ta 们。

![[csp2024jhn8.png#pic_center]]

![[csp2024jhn31.png#pic_center]]

HN-J02066 的代码内述说了一个悲伤的故事。

![[csp2024jhn9.png#pic_center]]

### 114514

有 $57$ 份代码使用了 $114,514$ 家族的成员。

![[csp2024jhn19.png#pic_center]]

### 3.1415926

HN-J01349 在自己的每一份代码里面都定义了常量 pi，值为 $\pi$。最长的达到了小数点后 $250$ 位。他的代码中还有许多鬼畜。

![[csp2024jhn20.png#pic_center]]

### 文明用语

HN-J01379 在代码里面使用了 Cnm 来进行调试。HN-J00322 和 HN-J01104 两位选手则是将其用为了变量名（也有可能是求组合数）。

![[csp2024jhn12.png#pic_center]]

![[csp2024jhn13.png#pic_center]]

唯一的 HN-J01166 定义并使用了 wc 函数，但是……

![[csp2024jhn14.png#pic_center]]

![[csp2024jhn15.png#pic_center]]

HN-J00013 使用了 nm 作为数组名，且进行了超长的打表（代码已格式化）。

![[csp2024jhn16.png#pic_center]]

### 牢

$6$ 个文件使用了 man 作为变量、数组、函数的标识符，没有人在代码中写出 What can I say。HNJ000171 牢哥还在后面写错了他的 man。

![[csp2024jhn29.png#pic_center]]

![[csp2024jhn30.png#pic_center]]

### 洛谷

共有 $10$ 个文件出现了洛谷的用户名或 UID。HN-J00254 对评测机进行了陈恳的祈祷。HN-J01784（疑似洛谷 fansj，读作发神经）可能与 XBT（小变态）有一段难以启齿的往事。

![[csp2024jhn17.png#pic_center]]

![[csp2024jhn18.png#pic_center]]

## 额外

HN-J00151 应该算是非常能整活的了。没有开子文件夹 + freopen 输出文件后缀为 .ans + 注释 freopen + 《comtinu》（正确的：`continue`）。

![[csp2024jhn5.png#pic_center]]

HN-J01053 还在 chain 子文件夹里面创建了一个 未命名1.cpp 文件，内容为自编的猜数游戏。这位选手还在 explore 开出了超大数组。

![[csp2024jhn10.png#pic_center]]

![[csp2024jhn11.png#pic_center]]