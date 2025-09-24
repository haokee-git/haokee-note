> [!quote] 导读
> 
> $\LaTeX$，一种基于 $\TeX$ 的排版系统，由 [美国](https://baike.baidu.com/item/%E7%BE%8E%E5%9B%BD/125486?fromModule=lemma_inlink) 计算机学家莱斯利·兰伯特（[Leslie Lamport](https://baike.baidu.com/item/Leslie%20Lamport/3942241?fromModule=lemma_inlink)）在 20 世纪 80 年代初期开发，利用这种格式，即使使用者没有排版和程序设计的知识也可以充分发挥由 [TeX](https://baike.baidu.com/item/TeX/3794463?fromModule=lemma_inlink) 所提供的强大功能，能在几天、甚至几小时内生成很多具有书籍质量的印刷品。对于生成复杂表格和 [数学公式](https://baike.baidu.com/item/%E6%95%B0%E5%AD%A6%E5%85%AC%E5%BC%8F/10349953?fromModule=lemma_inlink)，这一点表现得尤为突出。因此它非常适用于生成高印刷质量的科技和数学类文档。这个系统同样适用于生成从简单的信件到完整书籍的所有其他种类的文档。

总的来说，$\LaTeX$ 适合那些理工科的论文，其源代码的编写方式也比较好进行协作，最主要是对 Git 版本控制友好，且生成文档非常专业。

## 安装 LaTeX

$\LaTeX$ 有很多实现。在 Windows 系统上，最为广泛使用的是 texlive。

打开 [清华大学开源镜像站](https://mirrors.tuna.tsinghua.edu.cn/CTAN/systems/texlive/Images/)，下载 texlive（版本）.iso 磁盘映像文件，下载后打开，打开解压后的 install-tl-windows.bat。

点击 Advanced 切换详细设置，如果不需要设置就直接安装就行了。texlive 的安装过程非常缓慢，因为 texlive 会将 $\LaTeX$ 的几乎所有包都安装至本地，因此较为笨重，需要等待较多时间。

安装之后用命令 `latex -v` 测试是否安装成功。·