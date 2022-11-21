---
description: >-
  本篇翻译自：https://new.rosettacommons.org/docs/latest/getting_started/I-want-to-do-x
---

# 😀 我想采样X

&#x20;通常情况下，用户带着他们[想要解决的生物学问题](解决一个生物学问题.md)的想法来到Rosetta。有时，用户会带着一个输入结构和他们想要进行特定类型采样的方法，无论是通过运行一个应用程序还是使用RosettaScripts mover。在这里，我们按照结构扰动的类型对RosettaScripts支持的movers进行了分类，但是[生物问题页面](解决一个生物学问题.md)将更好地满足你对应用的需求。如果这两个页面都没有帮助，也许你还没有确定[问题出在哪里](https://new.rosettacommons.org/docs/latest/getting\_started/Determining-what-a-problem-is)？

## 通过片段替换确定结构

* AbscriptLoopCloserCM
* 在 ab initio relax 环境中处理loop
* AbscriptMover

## 结构生成

* [BackboneGridSampler](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/BackboneGridSamplerMover)
* BuildSheet
* [BundleGridSampler](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/BundleGridSamplerMover)
* [PerturbBundle](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/PerturbBundleMover)
* PerturbBundleHelix
* [MakeBundle](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/MakeBundleMover)
* MakeBundleHelix
* [MakePolyX](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/MakePolyXMover)
* BackboneSampler
* FitSimpleHelix
* InsertPoseIntoPoseMover pose combination
* [build\_Ala\_pose](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/BuildAlaPoseMover)
* [SetupForSymmetry](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/SetupForSymmetryMover) Necessary before doing anything else symmetrically
* [AddHydrogens](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/AddHydrogensMover) adds and optimizes missing hydrogens
* SymmetricAddMembraneMover
* GrowPeptides
* 从电子密度：
  * IdealizeHelices
  * RecomputeDensityMap
  * CartesianSampler

## 残基插入和删除

* [AddChain](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/AddChainMover)
* [AnchoredGraftMover](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/grafting/AnchoredGraftMover)
* [CCDEndsGraftMover](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/grafting/CCDEndsGraftMover)
* [CutOutDomain](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/CutOutDomainMover)
* [DeleteRegionMover](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/grafting/DeleteRegionMover)
* [InsertPoseIntoPoseMover](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/grafting/InsertPoseIntoPoseMover)
* [KeepRegionMover](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/grafting/KeepRegionMover)
* [MotifGraft](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/MotifGraftMover)
* [ReplaceRegionMover](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/ReplaceRegionMover)
* [Splice](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/SpliceMover)
* [SwitchChainOrder](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/SwitchChainOrderMover)

## 结构优化

* [IdealizeMover](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/IdealizeMover)

> 用数据库中的键长和键角的版本替换每个残基。添加约束条件以保持原始氢键。然后，使用dfpmin最小化每一个侧链和骨架二面角（除了脯氨酸phi）。

* [FinalMinimizer](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/FinalMinimizerMover)
* SaneMinMover
* [TaskAwareMinMover](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/TaskAwareMinMover)
* Symmetrizer

> 在功能上是一个优化mover；将采取一个与对称性有足够小的偏差的姿势并解决它们。

* [TaskAwareSymMinMover](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/TaskAwareSymMinMover)
* [SymMinMover](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/SymMinMover)
* minimize with symmetry
* LocalRelax
* [FastRelax](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/FastRelaxMover)

> 反复地重新填充，尽量减少侧链和骨干，同时将排斥性的权重向上和向下提升。尊重resfiles，movemaps，和task operations。

* [RepackMinimize](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/RepackMinimizeMover)就像弛豫的一个周期，有一个恒定的排斥性权重
* [MinPackMover](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/MinPackMover)
* [EnzRepackMinimize](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/EnzRepackMinimizeMover)
* [MinMover](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/MinMover)
* [MinimizationRefiner](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/MinimizationRefinerMover)
* NormalModeMinimizer

## 系综生成

* [FastRelax](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/FastRelaxMover)
* [Backrub](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/BackrubMover)
* [ParallelTempering](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/composite\_protocols/metropolis\_hastings/Tempering-MetropolisHastings#ParallelTempering)
* CanonicalSampling
* BBGaussian
* [GenericSimulatedAnnealer](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/GenericSimulatedAnnealerMover)
* [GeneralizedKIC](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/composite\_protocols/generalized\_kic/GeneralizedKIC)

