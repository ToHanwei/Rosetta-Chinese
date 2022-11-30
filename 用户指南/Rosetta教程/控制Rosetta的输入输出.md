---
description: >-
  本页面翻译自：https://www.rosettacommons.org/demos/latest/tutorials/input_and_output/input_and_output
---

# 🤪 控制Rosetta输入和输出

## 摘要

有多种方法可以控制Rosetta协议如何读取输入和产生输出。在本教程结束时，你应该明白：

* Rosetta支持哪些输入格式
* 如何处理经常导致Rosetta崩溃的奇怪残基
* 如何最好地准备一个输入结构
* 如何要求Rosetta将其与已知结构进行比较
* 如何改变Rosetta的输入和输出路径
* 尽管是蒙特卡洛协议，如何确保得到一致的运行轨迹
* 如何在PyMOL中对观察结构的变化
* 如何覆盖现有的输出

## 导航到demos

演示可在`<path_to_Rosetta_directory>/demos/tutorials/input_and_output`中获得。本教程中列出的所有演示命令都应该在此目录中执行。这里的所有演示都使用`linuxgccrelease`二进制文件。您可能需要根据您的操作系统和编译器将其更改为任何合适的值。

## 控制输入

### 通用的输入文件

您可以为Rosetta提供各种各样的输入文件，其中包含您的生物分子结构的坐标【译者注：每个原子的三维空间内的笛卡尔坐标】。

#### PDB

最常见的输入文件格式是PDB格式。关于PDB格式的详细描述可以在[WorldWide Protein Data Bank website](http://www.wwpdb.org/documentation/file-format-content/format33/v3.3.html)上找到。主要是与Rosetta有关的是以`ATOM`、`HETATM`和`TER`为开头的行。

```bash
...
ATOM   1477 3HD2 LEU A  94      10.910  -5.038   7.227  1.00  0.00           H  
TER                                                                             
HETATM 1479  O   HOH A 107      10.027  -4.206  14.093  1.00  0.00           O 
...
```

在上面的例子中，Rosetta识别到`ATOM`记录，它代表了`A`链中第94号的亮氨酸的一个`Hδ`原子，其坐标为（10.910, -5.038, 7.227），其占用率为1，温度系数为0。Rosetta忽略了第二列的原子编号（1477）和最后一列的元素符号（`H`）。`TER`记录表示链中断。类似地，`HETATM`记录表示与A链相关的水分子的氧原子，其坐标为（10.027，-4.206，14.093），占有率为1，温度系数为0，Rosetta也忽略了此记录中的原子编号和元素符号。Rosetta存储了温度系数，但假定所有非零的占有率都是1。

> 如果残基有多个构象，Rosetta只装入第一个构象。

要传入一个单一的PDB，请使用`in:file:s`选项。例如，下面命令可以用来计算一个优化后的PDB(1QYS)的[能量](https://www.rosettacommons.org/demos/latest/tutorials/scoring/scoring)。输入的PDB存在于`input_files`文件夹中。(`$ROSETTA3=path-to-Rosetta/main/source`目录中可以找到)

```bash
$ROSETTA3/bin/score_jd2.default.linuxgccrelease -in:file:s input_files/1qys.pdb
```

运行这个程序应该在你当前的工作目录中产生一个名为`score.sc`的文件，其中包含1QYS的能量分数。要继续进行下一步，请输入`rm score.sc`来删除`score.sc`。否则，从这里开始得分的所有结构的能量分数将被追加到这个文件中【译者注：score.sc没有删除的话，每运行一次的输出内容会写在原有内容那一行的后面】。

#### PDBs列表

假设你想把多个输入结构传给一个可执行文件，使用选项`in:file:l`。比如，你想给两个PDBs--1QYS和1UBQ打分。我们可以传递一个叫做`pdblist`的PDB列表【译者注：这里的pdblist是一个文本文件】，其中每行包含一个PDB的路径（空格分隔的PDB也可以，但不能用逗号或分号分隔），像这样:

```bash
input_files/1qys.pdb
input_files/1ubq.pdb
```

执行下面命令：

```bash
$ROSETTA3/bin/score_jd2.default.linuxgccrelease -in:file:l input_files/pdblist
```

运行这个程序应该会在你当前的工作目录中产生一个名为`score.sc`的文件。要继续进行下一步，请输入`rm score.sc`来删除`score.sc`。否则，从这里开始得分的所有结构的能量分数将被追加到这个文件中。

#### **沉默文件（Silent File）**

沉默文件一个Rosetta特有的紧凑的文件格式，它存储了多个结构的信息。在运行具有大量输出结构的模拟时，它特别有用，因为许多文件系统在运行批量操作时都会出现问题。许多Rosetta模拟可以产生沉默文件。在\<path\_to\_Rosetta\_directory>/demos/tutorials/input\_and\_output/input\_files/1qys\_10.o中可以找到一个二进制slient结构文件的例子。

前面几行代表了关于链的序列、能量和相对旋转/平移的信息。然而，主体部分并不是人类可以阅读的。

还有一种沉默文件格式叫蛋白质沉默结构文件，是人类可读的，但Rosetta有时无法以这种格式输出，因此，本教程不讨论它。关于这个问题的细节可以在[这里](https://www.rosettacommons.org/docs/latest/rosetta\_basics/file\_types/silent-file)找到。

要给Rosetta一个沉默文件作为输入，在运行你的命令时使用`in:file:silent选项`，像这样:

```bash
$ROSETTA3/bin/score_jd2.default.linuxgccrelease -in:file:silent input_files/1qys_10.o
```

您会在您的工作目录中再次生成一个名为`score.sc`的文件。其中包含1QYS的能量分数。要继续进行下一步，请删除分数。输入`rm score.sc`。否则，所有在此评分的结构的能量分数将追加到这个文件。

`in:file:silent`选项还可以用来传递静默文件列表。

#### 非标准残基与水分子的处理

大多数Rosetta协议期望他们正在处理的结构具有一定的属性集，例如。所有重原子都应该存在，所有残基的名称都应该是可识别的，等等。有时Rosetta可以猜到要添加哪些原子。在本例中，我们将直接从蛋白质数据库中获取PDB 1QYS进行评分:

```bash
$ROSETTA3/bin/score_jd2.default.linuxgccrelease -in:file:s input_files/from_rcsb/1qys.pdb
```

在日志中，您将看到以下行:

```bash
...
core.io.pose_from_sfr.PoseFromSFRBuilder: Reading MSE as MET!
...
core.pack.pack_missing_sidechains: packing residue number 13 because of missing atom number 6 atom name  CG
...
```

第一行表示它将残基MSE，即硒代蛋氨酸转化为MET，即标准蛋氨酸。第二行告诉你Rosetta发现13号残基中缺少Cγ原子，于是为13号残基建立了侧链。

#### 未识别的残基

一般情况下，直接从蛋白质数据库下载的PDB可能与Rosetta兼容，也可能与Rosetta不兼容。这里有一个例子，我们试图为PDB 3TDM评分。在正确的demo目录下，运行:

```bash
$ROSETTA3/bin/score_jd2.default.linuxgccrelease -in:file:s input_files/from_rcsb/3tdm.pdb
```

应用程序将退出并显示以下错误:【译者注：在我是用的版本（version:3.13）中并未遇到这个错误】

```bash
ERROR: Unrecognized residue: PO4
```

这个PDB含有一种磷酸离子，如果没有其他选择，Rosetta就无法处理它。为了给这个PDB评分，我们将添加一个选项-ignore\_unrecognized\_res，它将忽略PDB中的磷酸盐。

```bash
$ROSETTA3/bin/score_jd2.default.linuxgccrelease -in:file:s input_files/from_rcsb/3tdm.pdb -ignore_unrecognized_res
```

现在将对PDB进行评分，并且评分将显示在文件`score.sc`中。

> \-Ignore\_unrecognized\_res选项也会忽略结构中的水分子。这可能会改变你的结构的能量分数。

#### 零占有率（**Zero Occupancy**）

占用率表示观察到特定构象的情况的百分比。虽然大多数原子的占用率为1，但如果在多种构象中观察到残基，则占用率将低于1。占用数为0表示该原子从未在晶体中被观察到(但估计在这个位置存在)。Rosetta忽略了这些原子记录。如果它是非骨架重原子，它可能会为你构建侧链。如果它是像N或CA这样的骨架重原子，它会删除整个残留物。

我们已经修改了1QYS的占有率，以获得文件\<path\_to\_Rosetta\_directory>/demos/tutorials/input\_and\_output/input\_files/1qys\_zero\_occ.pdb。它的前几个原子的占有率为零：

```bash
ATOM      1  N   ASP A   3      -4.524  18.589  17.199  0.00  0.00           N  
ATOM      2  CA  ASP A   3      -3.055  18.336  17.160  0.00  0.00           C
...
```

运行命令：

```bash
$ROSETTA3/bin/score_jd2.default.linuxgccrelease -in:file:s input_files/1qys_zero_occ.pdb
```

在您的日志文件中，您会得到以下警告:

```bash
...
core.io.pose_from_sfr.PoseFromSFRBuilder: PDB reader is ignoring atom  N   in residue 3 A.  Pass flag -ignore_zero_occupancy false to change this behavior
core.io.pose_from_sfr.PoseFromSFRBuilder: PDB reader is ignoring atom  CA  in residue 3 A.  Pass flag -ignore_zero_occupancy false to change this behavior
...
core.io.pose_from_sfr.PoseFromSFRBuilder: [ WARNING ] skipping pdb residue b/c it's missing too many mainchain atoms:    3 A ASP ASP:NtermProteinFull

...
```

另外请注意，`score.sc`与之前的计算结果相比，得分更高。这是因为它删除了残基3，因此失去了3号残基的REU的分数。_要继续下一步，请通过输入`rm score.sc`来`score.sc。`否则，所有在此处评分的结构的能量分数都将追加到此文件中。_

有几个 Rosetta 应用程序，它们要求它们之间的序列长度恒定，例如_docking\_protocol_，如果存在零占有率的原子，它甚至可能崩溃而不提示错误信息。

要解决此问题，我们需要使用`-ignore_zero_occupancy`选项（默认设置为 true ）。将`-ignore_zero_occupancy`设置为`false`将强制Rosetta读入占有率0的原子，如下所示：

```bash
$ROSETTA3/bin/score_jd2.default.linuxgccrelease -in:file:s input_files/1qys_zero_occ.pdb -ignore_zero_occupancy false
```

此次运行产生的`score.sc`文件应与本章第一个示例中的输出文件相匹配。

#### 准备结构

为大多数Rosetta协议准备输入结构的推荐方法是运行优化协议，在运行你想要的Rosetta应用之前对你的结构进行弛豫。关于放松的详细教程可以在[这里](https://www.rosettacommons.org/demos/latest/tutorials/Relax\_Tutorial/Relax)找到。

虽然我们希望缓解输入结构中的冲突，并确保满足Rosetta的所有规范，但我们不希望主干发生太多变化。在`<path_to_Rosetta_directory>/demos/tutorials/input_and_output/flag_input_relax`中指定了一组通用选项。

```bash
-nstruct 2

-relax:constrain_relax_to_start_coords
-relax:ramp_constraints false

-ex1
-ex2

-use_input_sc
-flip_HNQ
-no_optH false
```



设置更高的`nstruct`，例如`nstruct 10`，会增加优化运行的次数，并可能产生更好的结果，但也可能会消耗大量时间。

我们将使用这个标签文件来完善直接从Protein Data Bank中提取的PDB 1QYS，这可能需要几分钟的时间来运行。

```bash
$ROSETTA3/bin/relax.default.linuxgccrelease -in:file:s input_files/from_rcsb/1qys.pdb @flag_input_relax
```

这将产生三个文件：`1qys_0001.pdb`,`1qys_0002.pdb`和`score.sc`. 使用分数文件中较低`total_score`的PDB作为协议的输入PDB。

> 如果需要，这些选项还可以由ignore\_unrecognized\_res和ignore\_zero\_occuany false补充。

使用ignore\_unrecognized\_res这样的标签可能会删除你想考虑的配体和水分子

> 确保您想要建模的所有残留都存在于优化的PDB中

#### 设置输入搜索路径

如果我们有多个输入文件，从一个路径位置搜索输入可能会有所帮助。例如，在`relax`同型二聚体PDB 4EQ1上运行协议时，我们可能希望限制蛋白质-蛋白质界面距离并防止它们移动。（可以在[此处](https://www.rosettacommons.org/demos/latest/tutorials/Constraints\_Tutorial/Constraints)找到有关约束的详细教程）。为此，我们需要一个`constrained_atompairs.cst`也位于目录中的约束文件`input_files`。当我们有多个这样的文件时，使用指定的 input\_directory运行`in:path`会有所帮助，如下所示：

```bash
$ROSETTA3/bin/relax.default.linuxgccrelease -in:path input_files -in:file:s 4eq1.pdb -constraints:cst_fa_file constrained_atompairs.cst -ignore_unrecognized_res @flag_input_relax
```

这将需要15分钟以上的时间来运行并产生4eq1\_0001.pdb、4eq1\_0002.pdb和score.sc文件。

#### 改变输入表示—质心或全原子

Rosetta使用两种结构表示法——更精细的_完整原子_表示和更粗糙的中心表示。可以在[此处](全原子表示与质心表示.md)找到关于两者的区别和使用的详细教程。为确保Rosetta了解您输入文件的表示形式，我们使用`in:file:centroid`或`in:file:fullatom`选项。示例运行可以在上面链接的教程中找到。

#### 输入一个已知的结构进行比较

_通常，比较 Rosetta与已知本地_结构的接近程度很有用。这对于基准测试特别有用。它还可用于检查 Rosetta将输入的PDB结构移动了多远。为此，我们使用该`-in:file:native`选项。

> **原始PDB必须与Rosetta的输出结构具有相同的残基数、相同的残基排序和相同的链排序。如果两者之间的残基数量不同，Rosetta 将给出错误；如果残基编号不匹配，则计算不正确的指标。**

在下面的示例中，我们将运行一个较旧的评分应用程序，_评分_以检查优化后的1QYS与原始PDB QYS有何不同。

```bash
$ROSETTA3/bin/score.default.linuxgccrelease -in:file:s input_files/1qys.pdb -in:file:native input_files/from_rcsb/1qys.pdb -ignore_waters
```

`default.sc`这会生成一个应该如下所示的打分文件：

```bash
SCORE:     score     fa_atr     fa_rep     fa_sol    fa_intra_rep    fa_elec    pro_close    hbond_sr_bb    hbond_lr_bb    hbond_bb_sc    hbond_sc    dslf_fa13       rama      omega     fa_dun    p_aa_pp    yhh_planarity        ref    allatom_rms    gdtmm    gdtmm1_1    gdtmm2_2    gdtmm3_3    gdtmm4_3    gdtmm7_4    irms    maxsub    maxsub2.0    rms description
SCORE:  -167.539   -414.834     48.380    225.004           1.040    -45.212        0.000        -25.491        -26.998         -2.986      -9.394        0.000     -4.905      4.211    109.662    -13.603            0.230    -12.643          1.050    1.000       1.000       1.000       1.000       1.000       1.000   0.000    92.000       92.000  0.135   1qys_0001
```

在这个打分文件中，该列`allatom_rms`表示与原始结构的全原子RMSD是1.050。这是因为Rosetta填充了侧链以在优化的过程中同时缓解冲突并优化相互作用。`rms`列表示与原始结构的Cα的RMSD要低得多，只有`0.135，`表明Rosetta没有移动主干。还给出了其他全局距离度量。

> **如果 Rosetta 发现输入结构中缺少太多的重原子，它会重建原始结构中残基的侧链，因此每次运行的指标可能略有不同。**

#### 其他选项列表

[此处](https://www.rosettacommons.org/docs/latest/full-options-list#in)给出了其他特定选项的完整列表。

## 控制输出

### 通用结构输出文件

Rosetta主要使用两种格式来输出结构——PDB文件和静默文件。这两个文件已在[上一节](控制Rosetta的输入输出.md#tong-yong-de-shu-ru-wen-jian)中进行了描述。

#### PDB结构

这是Rosetta的默认输出格式。对于默认不输出结构的应用程序，如打分应用程序，该选项`-out:pdb`强制Rosetta输出PDB。这在[评分教程](https://www.rosettacommons.org/demos/latest/tutorials/scoring/scoring)中进行了演示。

#### 静默文件

要将输出文件格式更改为静默文件，我们将使用标志`out:file:silent <filename>`. 由于静默文件能够在一个文件中存储多个结构，因此只有一个我们需要指定其名称的输出结构文件。我们将运行上面的[结构准备](控制Rosetta的输入输出.md#zhun-bei-jie-gou)示例来生成_二进制静默结构文件_。

```bash
$ROSETTA3/bin/relax.default.linuxgccrelease -in:file:s input_files/from_rcsb/1qys.pdb -out:file:silent output_files/1qys.o @c
```

这将需要几分钟的时间来运行并在`output_files`目录中生成一个静默文件`1qys.o`

#### 从静默文件中提取PDB

为了可视化和分析，您可能希望从静默文件格式中提取一些结构作为PDB。例如，提供的静默文件`<path_to_Rosetta_directory>/demos/tutorials/input_and_output/input_files/1qys.o`包含 10 个结构。比方说，我们想要将前 3 个结构提取为PDB。

要选择前3名，我们将首先将分数存储在一个单独的文件中，使用：

```bash
grep '^SCORE' input_files/1qys_10.o > output_files/1qys_silent_scores.sc
```

这应该会生成一个类似于以下内容的文件`<path_to_Rosetta_directory>/demos/tutorials/input_and_output/output_files/expected_output/1qys_silent_scores.sc`:

```bash
SCORE:     score     fa_atr     fa_rep     fa_sol    fa_intra_rep    fa_elec    pro_close    hbond_sr_bb    hbond_lr_bb    hbond_bb_sc    hbond_sc    dslf_fa13    coordinate_constraint       rama      omega     fa_dun    p_aa_pp    yhh_planarity        ref       time description
SCORE:  -145.658   -416.906     48.038    235.048           1.023    -47.764        0.000        -25.252        -27.431         -4.739     -10.754        0.000                   19.154     -4.561      4.169    110.657    -13.935            0.237    -12.643    121.000   1qys_0001
...
SCORE:  -146.560   -421.948     49.483    239.471           1.031    -49.106        0.000        -25.940        -27.309         -4.230     -13.052        0.000                   20.385     -5.436      4.646    110.952    -13.316            0.453    -12.643    115.000   1qys_0010
```

最后一列`description`包含我们将用于提取文件的标签。根据`score`使用对该文件进行排序：

```bash
sort -k1,1 -k2n output_files/1qys_silent_scores.sc
```

我们将得到：

```bash
SCORE:  -148.368   -417.523     46.620    235.293           1.049    -47.662        0.000        -25.448        -26.996         -3.816     -12.297        0.000                   20.283     -4.757      5.036    107.503    -13.480            0.470    -12.643    111.000   1qys_0007
SCORE:  -148.283   -423.099     47.967    241.560           1.046    -48.530        0.000        -25.397        -26.949         -4.226     -13.621        0.000                   19.796     -4.907      5.043    108.665    -13.450            0.461    -12.643    110.000   1qys_0005
SCORE:  -147.763   -416.130     46.386    235.877           1.023    -47.914        0.000        -25.787        -27.212         -3.864     -12.092        0.000                   20.623     -4.800      4.678    107.706    -13.821            0.205    -12.643    118.000   1qys_0009
...
```

我们看到`1qys_0007`，`1qys_0005`和`1qys_0009`是我们想要提取的3个得分最低的结构。您可以自由地对您想要的任何指标进行排序。为此，我们将准备这些标签的列表，如下所示：

```bash
1qys_0007
1qys_0005
1qys_0009
```

我们将使用该选项将此标记文件提供`in:file:tagfile`给可执行文件`extract_pdbs`以生成所需的结果。

```bash
$ROSETTA3/bin/extract_pdbs.default.linuxgccrelease -in:file:silent input_files/1qys_10.o -in:file:tagfile input_files/1qys_top3.tag
```

现在，您应该获得 3 个 PDB `1qys_0007.pdb`，`1qys_0005.pdb`并且`1qys_0009.pdb`位于当前工作目录中。

#### 压缩文件

为了在产生大量结构时节省空间，Rosetta可以自动gzip输出文件。添加选项`-out:pdb_gz`**而不是** `-out:pdb`生成压缩的PDB。在out:file:silent \<filename>生成后缀为.gz的压缩静默文件。

