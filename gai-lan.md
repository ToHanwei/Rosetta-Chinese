---
description: 这篇文档翻译自：https://www.rosettacommons.org/support/overview。水平有限，如有错误或不当之处欢迎修改。
---

# 概览

### &#x20;Rosetta软件套件概述

Rosetta是一套用于大分子建模的软件库，用户可以以不同的方式使用该库中的不同功能:

* 一组预先开发的应用程序可用于执行特定任务的协议；
* 一组框架(PyRosetta，RosettaScripts)允许新用例创建您自己的协议；
* 各种网络服务器，特别是[ROSIE](https://www.rosettacommons.org/software/servers)，被设置并出借他们的计算资源来提供可以远程使用的应用程序，而无需在您的计算机上安装任何东西。

[用户指南](https://www.rosettacommons.org/docs/latest/application\_documentation/Application-Documentation)中提供了协议、框架和应用程序的详细列表 。

### 使用案例

Rosetta最好的描述是我们的社区以及其他社区所使用的科学。如果你需要的话，它是可以扩展和适应的。

### 协议

Rosetta试图提供一个灵活的函数库来完成一组不同生物分子的建模任务。函数库中定义的基本任务和操作统称为算法，我们称之为协议(protocols)，每个算法都是用Rosetta灵活的分子建模库来完成特定的建模任务。这些协议既可以独立单元使用，也可以通过依次使用不同的应用程序或通用框架内的组合协议，将它们链接在一起来完成更加复杂的任务，

Rosetta算法能够完成对各种生物分子系统的预测、设计和分析，包括蛋白、RNA和DNA、肽、小分子以及非标准或衍生氨基酸。一些协议更改/评估单个单体单元（loop 重模建、从头折叠）的内部结构，而其他协议则建模/评估两个独立单体之间的相互作用（蛋白-蛋白对接、蛋白-肽对接、蛋白-配体对接）。这些协议中的许多部分可以合并来自各种实验结果的数据，包括X-ray、NMR和EPR。Rosetta协议可以跨越一系列的尺度；例如，从局部的Loop重建模到完整结构设计，从单个单体到生物分子之间的相互作用再到大分子复合物。

以下是部分协议列表。如需完整列表，请参见[用户指南](https://www.rosettacommons.org/docs/latest/application\_documentation/Application-Documentation)

| 协议                                                                                                                            | 说明                                                                                                                                  |
| ----------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------- |
| [RosettaAbinitio](https://www.rosettacommons.org/docs/latest/application\_documentation/structure\_prediction/abinitio-relax) | 从头蛋白质结构预测                                                                                                                           |
| [RosettaDesign](https://www.rosettacommons.org/docs/latest/application\_documentation/design/design-applications)             | 识别目标蛋白骨架的低能量序列                                                                                                                      |
| Rosetta Design PyMol Plugin                                                                                                   | 一个用户友好的PyMOL插件，用于使用RosettaDesig 提交蛋白质设计模拟                                                                                           |
| [RosettaDock](https://www.rosettacommons.org/docs/latest/application\_documentation/docking/docking-protocol)                 | 从单体成分的各个单个结构预测蛋白-蛋白复的结构                                                                                                             |
| [RosettaAntibody](https://www.rosettacommons.org/docs/latest/application\_documentation/antibody/antibody-protocol)\*         | 预测抗体Fv区域的结构。参见PubMed [24519881](http://www.ncbi.nlm.nih.gov/pubmed/24519881)[19062174](http://www.ncbi.nlm.nih.gov/pubmed/19062174) |
| RosettaFraments                                                                                                               | 生成片段库供Rosetta从头构建蛋白结构                                                                                                               |
| RosettaNMR                                                                                                                    | 合并NRM数据到基本的Rosetta协议来加速NMR结构预测的过程                                                                                                   |
| [RosettaDNA](https://www.rosettacommons.org/docs/latest/application\_documentation/design/rosetta-dna)                        | 用于设计与特定DNA序列相互作用的蛋白                                                                                                                 |
| [RosettaRNA](https://www.rosettacommons.org/docs/latest/application\_documentation/rna/rna-denovo)                            | RNA片段组装                                                                                                                             |
| [RosettaLigand](https://www.rosettacommons.org/docs/latest/application\_documentation/docking/ligand-dock)                    | 小分子-蛋白对接                                                                                                                            |
| RosettaSymmetry                                                                                                               | 在Rosetta中强制对称                                                                                                                       |
| [RosettaEnzdes](https://www.rosettacommons.org/docs/latest/application\_documentation/design/enzyme-design)                   | 酶设计                                                                                                                                 |
| RosettaMembrane                                                                                                               | 膜蛋白从头建模                                                                                                                             |
| RosettaDDG\*                                                                                                                  | 评估序列变化对蛋白稳定性的影响                                                                                                                     |
| RosettaScripts                                                                                                                | 一种基于XML的脚本语言，用于控制建模流程。支持所有主要的Rosetta功能                                                                                              |
| RosettaSnugDock\*                                                                                                             | 使抗体Fv区域能够与抗原对接，并允许抗原结合位点蛋白骨架的灵活性                                                                                                    |
| RosettaMultigraft                                                                                                             | 在支架蛋白上进行功能基于(motifs)的匹配、骨架和侧链嫁接                                                                                                     |
| [Rosetta FlexPepDock](https://www.rosettacommons.org/docs/latest/application\_documentation/docking/flex-pep-dock)            | 肽-蛋白对接                                                                                                                              |
| [Rosetta ERRASER](https://www.rosettacommons.org/docs/latest/application\_documentation/rna/erraser)                          | 使用电子密度约束重建模RNA晶体学模型                                                                                                                 |
| [RosettaVIP](https://www.rosettacommons.org/docs/latest/application\_documentation/design/vip-app)                            | 通过识别和填充空腔来稳定蛋白                                                                                                                      |
|                                                                                                                               |                                                                                                                                     |

用\*标记的协议可能在最新版本的Rosetta中不可用
