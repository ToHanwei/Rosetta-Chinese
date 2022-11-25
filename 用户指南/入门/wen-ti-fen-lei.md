---
description: >-
  该页面翻译自：https://new.rosettacommons.org/docs/latest/getting_started/Determining-what-a-problem-is
---

# 😭 问题分类

如果您无法确定如何通过我们关于“[解决一个生物学问题](jie-jue-yi-ge-sheng-wu-xue-wen-ti.md)”和“[我想采样X](wo-xiang-cai-yang-x.md)”页面来解决您的建模任务，那么您应该来这里。如果我们无法在Rosetta论坛上帮助您，您也可能被转送到这里。(这看起来像是循环，因为这个页面隐式地将用户从其中一个位置引导到另一个位置)。

有时，非Rosetta实验室的新研究生会得到问题陈述是模糊的。至少，他们对Rosetta和其文档的理解含糊不清。例如：“我们需要在这个位点检查这些突变是否正常。在您订购寡核苷酸之前，找一些计算蛋白质设计软件检查它们。” 这是一个伟大的项目，可能非常有价值，但这是一个[非常非常难的问题](http://xkcd.com/1430)；在序列数据和从Rosetta派生的集合中提取的数十种结构特征上训练的机器学习算法经常会得到正确的答案，但并非总是如此，而且仅仅查看Rosetta分数的变化并不能帮助你找到答案。不幸的是，没有简单的IsThisMutationTolerated模块可以回答这样的问题。

这不是你或你的 PI 的错误：这是一个重要的机会，让你弄清楚需要什么样的抽样来回答你的问题。例如，假设其中一个突变是α螺旋第二个位置的丙氨酸突变成脯氨酸。这是脯氨酸在α螺旋中第三常见的位置；因此，这可能性很小，但不是不可能。所以问题是：这种突变是如何打破折叠的？

一个起点可能是在固定的骨架上进行突变，重新填充在该残基周围的空腔中，并评估能量。如果它的结果太糟糕了，也许需要一些骨架上的运动来松弛结构。此外，这样做您可能会收益，采用低质量的NMR结构，从每一个模型生成一个系综，并从该系综的最佳簇质心出发。

此外，这些结果都不一定与您的 PI 提出的基本问题相关。您的PI是否想知道突变在结构上的耐受性如何？好吧，那么您可以从整个蛋白质的RMSD得到一些测量值、包括天然和突变体集合，或者可能是所讨论的突变体附近蛋白质的一个子集，或者它是否具有关键区域，例如与另一种蛋白质存在相互作用界面或一个活性位点的RMSD。当然，您也想加入能量测量；如果在突变体集合中，到原始模型最低RMSD的构象（即使在你的“最佳质心”内）也有可能具有最差的能量，反之亦然，这对于该突变的稳定性来说是一个不好的迹象。您的PI是否想知道突变在_功能上的耐受性如何？_你多半是运气不好。这是一个非常复杂的问题。也许“功能相关”残基的RMSD会有所帮助，但这只是一种可能性；不可能作为任何普遍有用的指标，并且识别“功能相关”残基通常是棘手的。

简而言之：大多数生物学问题都很复杂，需要广泛思考。与您的PI交谈以确保您将他们的请求转化为正确的建模类型。 [此页面](jie-jue-yi-ge-sheng-wu-xue-wen-ti.md)从生物学问题的角度考虑如何处理 Rosetta，[此页面](wo-xiang-cai-yang-x.md)从采样自由度的角度进行同样的操作。

在投入大量计算机时间之前，请确保您了解问题。（当然，很多计算机时间有时就是问题本身：难题需要大量计算机时间，可能比你可用的时间还要多【译者注：算力不够】。）

如果您可以很好地描述您的问题，但不确定如何处理它，[Rosetta论坛](http://www.rosettacommons.org/forum)（外部链接）通常是一个很好的资源。不幸的是，这份文档已经提炼出了许多可用的专业知识，所以有时答案是，我们就是做不到。

## Rosetta无法解决的问题

Rosetta无法解决三大类问题。一般来说，如果你付出了很多努力，你可能属于这些类别之一。

1. 该问题构思的良好并使用正确的解决方法，但是由于[大分子建模中的广泛挑战](https://new.rosettacommons.org/docs/latest/getting\_started/Challenges-in-Macromolecular-Modeling)（如评分问题和搜索问题）而失败。这100%是Rosetta的错。
2. 问题可以解决，但[没有足够的计算机时间可供使用](https://new.rosettacommons.org/docs/latest/getting\_started/Rosetta-on-different-scales)：问题是采样不足。
3. 这个问题构思的非常好，但非常复杂。它可能在Rosetta的能力范围内，但不能使用预先存在的协议——可能需要很长的[RosettaScript](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/RosettaScripts)。也许这超出了Rosetta的能力范围，需要一两个新的[Mover](https://new.rosettacommons.org/docs/latest/rosetta\_basics/structural\_concepts/Mover)。这种项目对于Rosetta开发人员来说是合理的，但对于非Rosetta实验室中的细胞生物学研究生来说可能不是一个小项目。我们确实经常在[Rosetta论坛](https://www.rosettacommons.org/forum)上看到这种复杂的项目。

## 我们不能帮助的问题，以及如何帮助我们帮助您

1. 上面的三个问题在广义上可以由Rosetta解决，但超出了我们帮助您解决的资源范围。Rosetta社区对诸如“我尝试将 Mover Foo与这些设置一起使用但遇到了这个问题”之类的具体问题非常敏感，但对诸如“我需要帮助编写我的脚本”之类的宽泛和模糊的问题则反应迟钝。我们知道学习编写PyRosetta/RosettaScripts，或者只是一般地使用Rosetta是很困难的——但我们没有资源来单独培训用户，所以我们创建了这个wiki。如果这是一个问题——请在您的查询中具体说明，尤其是从程序员的角度来看。（对您感兴趣的蛋白质高度明确并不能帮助我们帮助您。）
2. 与任何大型机构一样，我们确实遭受“人才流失”和机构知识流失的困扰。如果您对7年前的一篇论文中使用的特定应用程序感兴趣，而该论文在最初的论文之后没有太多的出版历史——可能是作者离开了 Rosetta社区，转而从事其他工作。如果他们没有留下好的文档，我们可能无能为力。如果这是一个问题——请让我们确切知道您尝试以哪篇论文为基础进行实验，以便我们知道应该联系谁。有时PI会有一个毕业学生的联系人，或者他们实验室的其他人会接手这个项目。
3. 有时我们只是不知道！Rosetta庞大而复杂，而且复杂程度与使用它的人数不成比例。您可能是第一个询问如何将Mover Foo与Filter Bar结合使用的人。恭喜！你在最前沿！让我们知道您在冒险中发现了什么！我们以前没有去过那里，所以我们真的不知道你会发现什么。

## 更多资源

* [学习生物物理学和计算建模的资源](学习生物物理学.md)
* [解决一个生物学问题](jie-jue-yi-ge-sheng-wu-xue-wen-ti.md)：使用Rosetta解决生物学问题的指南
* [我想采样X](wo-xiang-cai-yang-x.md)：在Rosetta中使用不同形式的采样指南的指导
* [Rosetta在不同尺度上应用](https://new.rosettacommons.org/docs/latest/getting\_started/Rosetta-on-different-scales)：关于解决一个问题需要做多少工作的讨论
* [大分子建模中的挑战](https://new.rosettacommons.org/docs/latest/getting\_started/Challenges-in-Macromolecular-Modeling)：讨论蛋白质建模中的采样和评分问题
