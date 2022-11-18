---
description: 翻译自：https://new.rosettacommons.org/docs/latest/getting_started/Getting-Started
---

# 😂 入门

此页面是为刚接触Rosetta的科学家们编写的: 或许是一年级研究生，或者年轻的博士后，他们收到/启动了一个需要“一些计算机建模”的项目。换句话说，一个从零开始的Rosetta初学者。Rosetta是您需要做建模的优秀工具吗？如果是这样，您将如何获取和使用Rosetta？如果您已经对这些概念感到熟悉，请随时跳过。

Rosetta是一个非常大的大分子建模软件套件。所谓软件套件，这里我们指的是大量计算机代码的集合（主要是C++,一些是Python，还有一些其他编程语言），但它不是单一的整体程序。通过大分子建模，我们指的是评估和排序生物大分子不同结构的物理学合理性的过程（通常是蛋白质，但核酸和配体【译者注：这里应该指的是小分子】也得到了显著地支持，并且对隐式脂质膜的支持正在增加）。通常，用户会在Rosetta中[选择一些特定的协议](https://new.rosettacommons.org/docs/latest/getting\_started/Solving-a-Biological-Problem)，并向该协议提供以下输入：A）要处理的结构；B）协议中的哪些选项适合于用户的需求。

<figure><img src="../../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

| 目录                                                                                       |
| ---------------------------------------------------------------------------------------- |
| [我准备好我需要的东西了吗？](./#wo-zhun-bei-hao-wo-xu-yao-de-dong-xi-le-ma)                           |
| [公共Rosetta服务](./#gong-gong-rosetta-fu-wu)                                                |
| [商用Rosetta服务](./#shang-yong-rosetta-fu-wu-1)                                             |
| [Rosetta入门教程](./#rosetta-ru-men-jiao-cheng)                                              |
| [在Mac/Linux上安装](./#zai-maclinux-shang-an-zhuang)                                         |
| [Windows系统](./#windows-xi-tong)                                                          |
| [在计算集群上使用Rosetta](./#zai-ji-suan-ji-qun-shang-shi-yong-rosetta-1)                        |
| [Rosetta在国家级超级计算机上的使用](./#rosetta-zai-guo-jia-ji-chao-ji-ji-suan-ji-shang-de-shi-yong-1) |
| [如何更新这些文档](./#ru-he-geng-xin-zhe-xie-wen-dang)                                           |
| [更多资源](./#geng-duo-zi-yuan)                                                              |

### 我准备好我需要的东西了吗？

做好大分子建模——做好科学——需要仔细思考您的输入、建模的执行方式以及对输出的分析。Rosetta本身可以作为一个“[黑匣子](https://en.wikipedia.org/wiki/Black\_box)”来运行，但如果您真这样使用的话，结果对您和您所做的项目都是不利的。

#### 1）Rosetta的输入

Rosetta的主要输入是输入结构【译者注：这里面这的“结构”，不特殊说明的话应该统一指的是蛋白结构】。通常，如果您的分子具有高分辨率结构（分辨率小于2埃），只需要[稍加优化](https://new.rosettacommons.org/docs/latest/rosetta\_basics/preparation/preparing-structures)即可与Rosetta一起使用。如果您有分辨率较差的结构、NMR结同源模型、或者根本没有结构，那么您的任务将会困难的多。您任然应该为建模任务[准备好结构](https://new.rosettacommons.org/docs/latest/rosetta\_basics/preparation/preparing-structures)，但是请注意，当从质量较差的结构开始时，建模的效率和效果会降低，并且[解释结果](https://new.rosettacommons.org/docs/latest/getting\_started/Analyzing-Results)也更具有挑战性。

#### 2）选择Rosetta协议

除了结构之外的其他输入是选择使用[哪个Rosetta协议](https://new.rosettacommons.org/docs/latest/getting\_started/Solving-a-Biological-Problem)，以及使用什么[选项](https://new.rosettacommons.org/docs/latest/rosetta\_basics/running-rosetta-with-options#specifying-options)【译者注：可选参数】和[文件输入](https://new.rosettacommons.org/docs/latest/rosetta\_basics/file\_types/file-types-list#commonly-used-input-files)。

#### 3）计算资源

Rosetta软件作为一个整体，是为在超级计算机上运行而编写的，但可以在[许多不同尺寸的规模](https://new.rosettacommons.org/docs/latest/getting\_started/Rosetta-on-different-scales)【译者注：任务需要计算的模型数量，任务的复杂程度，需要消耗多大的计算机算力】上运行。大多数的应用程序都可以在任何计算机上“试运行”以进行测试。一些应用程序可以在笔记本上运行。有些应用程序可以在实验室规模的强大计算机上（12-30核）运行。大多数应用程序假定您可以使用数万小时的计算机时间来积累足够多的计算结果，用以回答您的问题。本文档后面的部分描述了在不同规模计算资源上安装或使用Rosetta。

### 公共Rosetta服务

RosettaCommons维护了几个[公共服务](https://new.rosettacommons.org/docs/latest/Rosetta-Servers)，仅供非商业用途。此处涉及最受关注的服务，但请参阅[此处](https://new.rosettacommons.org/docs/latest/Rosetta-Servers)和[此处](https://www.rosettacommons.org/software/servers)获取更完整的列表。

对于商业用途，请参阅下面的部分和[Rosetta服务](https://new.rosettacommons.org/docs/latest/Rosetta-Servers)页面。

* [ROSIE](http://rosie.rosettacommons.org/)是一个服务，它通过简单的Web界面提供多个Rosetta应用程序。它非常适合Rosetta新手使用。尽管ROSIE多种多样，但是它只提供Rosetta全部功能中的一部分。
* [ROBETTA](http://robetta.bakerlab.org/)（Robot-Rosetta）是一个服务，提供从头折叠（_ab initio_）和结构预测，以及Rosetta本地运行的片段选择（fragment selection）。

### 商用Rosetta服务

[Cyrus Biotechnology](https://cyrusbio.com/)是一家提供 Bench 的公司，Bench 是一种面向商业用户的服务，拥有用于同源建模（如 Robetta）、蛋白质设计（RosettaDesign）、ddG 计算以及其他建模工具（如弛豫和最小化）的工具。（Cyrus Biotechnology 是 Rosetta 的商业许可方，为其客户提供基于 Web 的 Rosetta 图形用户界面。商业 Rosetta 被许可证持有者向华盛顿大学支付的许可费用于支持 RosettaCommons，投资于 Rosetta 的维护和进一步开发。)

### Rosetta的本地安装与使用

对于学术和商业用户，您可以[申请许可证](http://c4c.uwc4c.com/express\_license\_technologies/rosetta)【译者注：许可证是安装Rosetta所必须的】。这些许可证对于学术用户免费【译者注：首先您可能需要一个学术机构的邮箱】。获得许可证后，您可以在[此处下载代码](https://www.rosettacommons.org/software/license-and-download)。请注意，下载得到的是一个[.tar格式的压缩文件](http://en.wikipedia.org/wiki/Tar\_\(computing\))【译者注：您可能需要对应的解压缩工具对该文件进行解压，解压后才可以进行后续的安装步骤】。在大多数情况下，我们不会分发[可执行文件/程序](http://en.wikipedia.org/wiki/Executable)，我们分发的是[源代码](http://en.wikipedia.org/wiki/Source\_code)。因此，在使用之前，您需要[编译](http://en.wikipedia.org/wiki/Compiler)代码。

### Rosetta入门教程

下载Rosetta后，可以通过[这些详细的教程](https://www.rosettacommons.org/demos/latest/Home#tutorials)开始使用。完成入门教程后，您应该能够在Rosetta上完成最常见的分子建模任务。

### 在Mac/Linux上安装

本地安装意味着将通过[命令行界面（或者终端）](http://en.wikipedia.org/wiki/Command-line\_interface)使用Rosetta。对于本地用户。您不太可能希望将Rosetta安装到整个系统。Rosetta也很乐意由没有管理员权限【译者注：对于Linux系统来说，即使您没有root或者sudo权限，您也可以无障碍的编译和安装】的的普通用户编译和安装——这就是开发人员使用它的方式。你可能需要管理员权限才能安装[依赖项](https://new.rosettacommons.org/docs/latest/build\_documentation/Build-Documentation#dependencies)。

* 首先将您下载的代码解压

```bash
tar -xvzf Rosetta[releasenumber].tar.gz
```

* 接下来，切换到`source`目录下

```bash
cd main/source
```

* Rosetta使用[SCons](http://www.scons.org/)作为编译助手。您可能需要先[`下载`](http://www.scons.org/download.php)并安装它。基本的编译命令是：`./scons.py -j<number_of_processors_to_use> mode=release bin`
  * 这里将`number_of_processors`更换为比您的计算机处理器数量少一的数字。预计编译需要一段时间（在一个处理器上需要数个小时）。

有关进一步的说明和故障排除，请参见我们广泛的[开发文档](https://new.rosettacommons.org/docs/latest/build\_documentation/Build-Documentation#compiling-rosetta-3)。

### Windows系统

不幸的是，我们目前无法在Windows上支持整个Rosetta。这是因为，适用于Windows的免费、易于使用的C++编译器很少，而且他们使用的C++标准也略有不同。如果您没有Mac/Linux系统的计算机，可以选择在[Dual booting](http://en.wikipedia.org/wiki/Multi-booting#Windows\_and\_Linux)【译者注：译者在这里简单地理解为双系统，作者的意思可能是如果你只有Windows系统的电脑，或许你可以再Windows系统的基础上再装一个Linux系统来运行Rosetta】或者[虚拟机](https://en.wikipedia.org/wiki/Virtual\_machine)上运行Mac/Linux。我们无法帮助您设置Windows/Linux双系统，但是我们可以帮助您在Linux分区上设置Rosetta。[PyRosetta](https://new.rosettacommons.org/docs/latest/scripting\_documentation/PyRosetta/PyRosetta)是一个基于Python的Rosetta接口，它所需要的Rosetta子集在Windows系统上得到了支持，并且在[http://www.pyrosetta.org](http://www.pyrosetta.org)可用。

### 在计算集群上使用Rosetta

如果您需要在科学计算集群上使用Rosetta，则该集群上可能已经安装了一个一般的使用的Rosetta版本。也许您可以与集群的管理员谈谈，看看是否有一个集群中提供版本供您使用。

如果您的集群没有安装Rosetta，或者您希望使用与集群中不同的版本，不用担心，因为Rosetta被设计为普通用户服务，可被普通用户编译和安装而不需要管理员权限。只要有常用的编译工具供你使用，你应该能够在你的用户目录【译者注：该目录你的账户拥有正常的可读可写可执行权限的目录即可，例如你账户的home目录】中编译和运行Rosetta，而不需要集群管理员的参与。只需要把它当作一个[本地安装](https://new.rosettacommons.org/docs/latest/getting\_started/Getting-Started#local-installation-and-use-of-rosetta\_installation-on-mac-linux)就可以了。

### Rosetta在国家级超级计算机上的使用

作为XSEDE计划的一部分，[TACC/Stampede](https://new.rosettacommons.org/docs/latest/build\_documentation/TACC)集群为授权用户集中安装了Rosetta和[PyRosetta](https://new.rosettacommons.org/docs/latest/scripting\_documentation/PyRosetta/PyRosetta)。有关详细信息，强参阅[TACC](https://new.rosettacommons.org/docs/latest/build\_documentation/TACC)页面。

### 如何更新这些文档

开发人员可以通过[交互式wiki](https://www.rosettacommons.org/docs/wiki/Home)更新这些文档页面。注意：需要登录Github。

### 更多资源

* [Rosetta 入门教程](https://www.rosettacommons.org/demos/latest/Home#tutorials)
* [学习生物物理学和计算建模的资源](https://new.rosettacommons.org/docs/latest/getting\_started/Resources-for-learning-biophysics-and-computational-modeling)
* [构建文档](https://new.rosettacommons.org/docs/latest/build\_documentation/Build-Documentation)：有关设置 Rosetta 的信息
* [我想做某某](https://new.rosettacommons.org/docs/latest/getting\_started/I-want-to-do-x)：使用RosettaScripts进行特定类型的结构扰动的指南
* [应用程序文档](https://new.rosettacommons.org/docs/latest/application\_documentation/Application-Documentation)：链接到各种 Rosetta 应用程序的文档
* [分析结果](https://new.rosettacommons.org/docs/latest/getting\_started/Analyzing-Results)：分析使用 Rosetta 生成的结果的技巧
* [比较结构](https://new.rosettacommons.org/docs/latest/getting\_started/Comparing-Structures)：关于比较结构的论文
* [命令集合](https://new.rosettacommons.org/docs/latest/application\_documentation/commands-collection)：用于运行 Rosetta 可执行文件的示例命令行列表
* [Rosetta服务](https://new.rosettacommons.org/docs/latest/Rosetta-Servers)：基于Web服务的Rosetta应用程序
* [脚本文档](https://new.rosettacommons.org/docs/latest/scripting\_documentation/Scripting-Documentation)：Rosetta 的脚本接口
* [Rosetta 概述](https://new.rosettacommons.org/docs/latest/rosetta\_basics/structural\_concepts/Rosetta-overview): Rosetta 主要概念概述
* [FAQ](https://new.rosettacommons.org/docs/latest/getting\_started/FAQ) : 常见问题
* [词汇表](https://new.rosettacommons.org/docs/latest/rosetta\_basics/Glossary/Glossary)：Rosetta 术语的简要定义
* [RosettaEncyclopedia](https://new.rosettacommons.org/docs/latest/rosetta\_basics/RosettaEncyclopedia)：Rosetta术语的详细说明
