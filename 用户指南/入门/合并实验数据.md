---
description: >-
  本页面翻译自：https://new.rosettacommons.org/docs/latest/rosetta_basics/Incorporating-Experimental-Data
---

# 😒 合并实验数据

潜在的有用的实验数据有很多形式。蒙特卡洛（Monte Carlo）模拟的本质强烈支持纳入任何类型的实验约束，因为你所需要做的就是让它影响生成结构的分布。

## 约束 vs. 限制（Constraints vs. Restraints）

Rosetta称_constraints_为其他计算软件包所称的_restraints_。在Rosetta中，约束并不是固定一个自由度并将其从采样和评分中移除。相反，我们是在增加一个评分项，对偏离该自由度的特定值进行惩罚。约束没有特定的名称--它只是确保该自由度不自由，例如在[MoveMap](https://new.rosettacommons.org/docs/latest/rosetta\_basics/Glossary/Glossary#movemap)中。

## 生物物理学

实际上，对生物问题来说，最大的实验性采样偏差是任何可能存在的输入结构。毕竟，你之所以使用这些结构，正是因为你足够信任它们，不想进行从头开始的结构预测，所以你希望从它们开始提供偏差。同时，输入结构并不完美。

* 晶体结构的分辨率是可变的，而且经常缺乏氢。 晶体结构在单个结构中的质量变化之大令人震惊。
* 在氢不能被看到的分辨率下（至少90%的PDB），天冬酰胺和谷氨酰胺的氧和氮不能相互区分（同理，组氨酸互变异构体），并且经常被分配错误。 NMR结构经常通过几百个约束条件来解决这一问题，而不是在晶体结构中成千上万的约束条件。

最重要的是，这些优化工作中使用的力场在算术上和算法上与Rosetta能量函数不同。获得与起始结构几何上相似但更接近评分函数局部最小值的结构是至关重要的。这一点很重要，因为起始结构中的每个单位应变能都可能不适当地偏置采样：可以接受本来会被拒绝的不良移动，因为它们减轻了本应解决的应变。关于如何适当地准备起始结构，有一篇[完整的文章](https://new.rosettacommons.org/docs/latest/rosetta\_basics/preparation/preparing-structures)。

## 专门的 Rosetta 可执行文件

Rosetta 有单独的模块来处理特定形式的实验约束：

* [mr\_protocols](https://new.rosettacommons.org/docs/latest/application\_documentation/structure\_prediction/mr-protocols)通常_与_Phaser 一起使用；它使用Rosetta的比较建模从片段中重建模板中的gap和insertions，以及缺失的密度，然后通过对实验密度的约束进行弛豫。然后您可以再次使用Phaser根据晶体学数据重新评分。
* [ERRASER](https://new.rosettacommons.org/docs/latest/application\_documentation/rna/erraser)根据电子密度（晶体学数据）优化RNA结构；它构成了_erraser\_minimize_、_swa\_rna\_analytical\_closure_和 \_swa\_rna\_main 的工作流程。它需要使用优化程序PHENIX。
* [loops from density](https://new.rosettacommons.org/docs/latest/loops-from-density)是一个脚本，用于获取不理想的电子数据和一个提示你愿意重建多少构象的截止值，并生成用于loop建模的"loops"输入文件。
* [Chemical shift files](https://new.rosettacommons.org/docs/latest/rosetta\_basics/file\_types/chemical-shift-file)为通常统称为 CSROSETTA 的各种协议提供数据，这些协议结合了NMR约束以改进结构

## 实验约束

您经常会遇到这样的情况，您对实验系统的了解并不完全符合上述任何情况，或者提供的信息非常稀少甚至相互矛盾。没关系：请使用Rosetta处理约束的能力：RosettaScripts进行特定类型的结构扰动的指南。

## 更多资源

* [学习生物物理学和计算建模的资源](学习生物物理学.md)
* [CS-Rosetta](https://new.rosettacommons.org/docs/latest/CS-Rosetta):  利用RNA化学位移数据与Rosetta进行结构预测
* [解决一个生物学问题](解决一个生物学问题.md)：使用Rosetta解决生物学问题的指南
* [入门：为新接触罗塞塔的人提供的页面](./)
* [应用程序文档](https://new.rosettacommons.org/docs/latest/application\_documentation/Application-Documentation)：链接到各种 Rosetta 应用程序的文档
* [分析结果](分析结果.md)：分析使用 Rosetta 生成的结果的技巧
* [脚本文档](https://new.rosettacommons.org/docs/latest/scripting\_documentation/Scripting-Documentation)：Rosetta 的脚本接口

