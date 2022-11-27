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







