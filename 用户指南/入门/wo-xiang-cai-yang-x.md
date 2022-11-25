---
description: >-
  本篇翻译自：https://new.rosettacommons.org/docs/latest/getting_started/I-want-to-do-x
---

# 😀 我想采样X

通常情况下，用户带着他们[想要解决的生物学问题](jie-jue-yi-ge-sheng-wu-xue-wen-ti.md)的想法来到Rosetta。有时，用户会带着一个输入结构和他们想要进行特定类型采样的方法，无论是通过运行一个应用程序还是使用RosettaScripts mover。在这里，我们按照结构扰动的类型对RosettaScripts支持的movers进行了分类，但是[生物问题页面](jie-jue-yi-ge-sheng-wu-xue-wen-ti.md)将更好地满足你对应用的需求。如果这两个页面都没有帮助，也许你还没有确定[问题出在哪里](https://new.rosettacommons.org/docs/latest/getting\_started/Determining-what-a-problem-is)？&#x20;

| 目录                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <ul><li><a href="wo-xiang-cai-yang-x.md#tong-guo-pian-duan-ti-huan-que-ding-jie-gou">通过片段替换确定结构</a></li><li><a href="wo-xiang-cai-yang-x.md#jie-gou-sheng-cheng">结构生成</a></li><li><a href="wo-xiang-cai-yang-x.md#can-ji-cha-ru-he-shan-chu">残基插入和生成</a></li><li><a href="wo-xiang-cai-yang-x.md#jie-gou-you-hua">结构优化</a></li><li><a href="wo-xiang-cai-yang-x.md#xi-zong-sheng-cheng">系综生成</a></li><li><a href="wo-xiang-cai-yang-x.md#gu-jia-zi-you-du">骨架自由度</a></li><li><a href="wo-xiang-cai-yang-x.md#ce-lian-zi-you-du">侧链自由度</a></li><li><a href="wo-xiang-cai-yang-x.md#ren-yi-gou-xiang-zi-you-du">任意构象自由度</a></li><li><a href="wo-xiang-cai-yang-x.md#loop-gou-xiang-cai-yang">Loop构象采样</a></li><li><a href="wo-xiang-cai-yang-x.md#dui-jie">对接</a></li><li><a href="wo-xiang-cai-yang-x.md#hua-xue-lian-tong-xing">化学连通性</a></li><li><a href="wo-xiang-cai-yang-x.md#she-ji">设计</a></li><li><a href="wo-xiang-cai-yang-x.md#fen-xi">分析</a></li><li><a href="wo-xiang-cai-yang-x.md#dui-cheng-jie-kou">对接接口</a></li><li><a href="wo-xiang-cai-yang-x.md#fen-zi-dong-li-xue-dai-ma">分子动力学代码</a></li><li><a href="wo-xiang-cai-yang-x.md#lei-tai-peptidomimetics">类肽</a></li><li><a href="wo-xiang-cai-yang-x.md#kang-ti-jian-mo-yu-she-ji">抗体建模与设计</a></li><li><a href="wo-xiang-cai-yang-x.md#geng-duo-zi-yuan">更多资源</a></li></ul> |

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

## 骨架自由度

* [Backrub](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/BackrubMover)
* [BackrubDD](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/BackrubDDMover)
* BackrubSidechain
* ShortBackrubMover

> 一种特殊形式的骨架运动，旨在协调保持特定的侧链位置。

* [Small](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/SmallMover)

> 对骨架自由度做小的扰动

* Shear

> 对残基的一个二面角进行小的扰动，对另一个二面角进行反向扰动，以避免“杠杆臂效应”（lever arm effect）

* [SetTorsion](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/SetTorsionMover)

> 将扭转（torsion）【译者注：猜测是可旋转键的扭转角】设置为一个值或者通过一个值进行扰动（使用perturb标签）

* MinimizeBackbone

> 只最小化骨架

* RandomOmegaFlipMover

> 随机翻转一个欧米茄角（omega angle），对肽最有用

* BackboneTorsionPerturbation
* BackboneTorsionSampler
* BBGaussian

## 侧链自由度

* SetChiMover
* [SymRotamerTrialsMover](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/SymPackRotamersMover)
* [PackRotamersMover](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/PackRotamersMover)
* [RotamerTrialsMinMover](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/RotamerTrialsMinMover)
* [RotamerTrialsMover](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/RotamerTrialsMover)
* [RotamerTrialsRefiner](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/RotamerTrialsRefinerMover)
* [Sidechain](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/SidechainMover)
* [SidechainMC](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/SidechainMCMover)
* RepackTrial
* [RepackingRefiner](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/RepackingRefinerMover)
* BoltzmannRotamerMover
* [PackRotamersMoverPartGreedyMover](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/PackRotamersMoverPartGreedyMover)
* [Prepack](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/PrepackMover)
* [SymPackRotamersMover](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/SymPackRotamersMover)
* PerturbRotamerSidechain
* [DnaInterfacePacker](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/DnaInterfacePackerMover)
* PerturbChiSidechain

## 任意构象自由度

* RandomTorsionMover

> 从移动图（movemap）中选择随机的角度进行扭转

## Loop构象采样

* AnchoredGraftMover

> 一个复合的移动器（mover），它进行大量的loop建模，然后重新填充嫁接的残基

* [KicMover](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/KicMover)
* LegacyKicSampler
* SmallMinCCDTrial
* ShearMinCCDTrial
* [LoopBuilder](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/LoopBuilderMover)
* LoopCM
* [LoopCreationMover](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/LoopCreationMover)
* [LoopFinder](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/LoopFinderMover)
* LoopHash
* LoopHashDiversifier
* LoopHashLoopClosureMover

> LoopHash算法构成了一种非常快速的方式，从可以实现给定闭包的片段库中提取loop构象

* [LoopLengthChange](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/LoopLengthChangeMover)
* [LoopModeler](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/LoopModelerMover)
* [LoopMoverFromCommandLine](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/LoopMoverFromCommandLineMover)
* LoopMover\_Perturb\_CCD
* LoopMover\_Perturb\_KIC
* LoopMover\_Perturb\_QuickCCD
* LoopMover\_Perturb\_QuickCCD\_Moves
* LoopMover\_Refine\_Backrub
* LoopMover\_Refine\_CCD
* LoopMover\_Refine\_KIC
* LoopMover\_SlidingWindow
* [LoopProtocol](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/LoopProtocolMover)
* LoopRefineInnerCycleContainer
* LoopRelaxMover
* [LoopRemodel](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/LoopRemodelMover)
* [LoophashLoopInserter](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/LoopCreationMover)
* LoopmodelWrapper
* CCDEndsGraftMover
* CCDLoopCloser
* CCDLoopClosureMover
* DefineMovableLoops
* [GeneralizedKIC](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/composite\_protocols/generalized\_kic/GeneralizedKIC)

> 一个庞大而复杂的系统，它主要独立运行以对任意原子序列执行动态的loop闭合。

## 对接

* [DARC](https://new.rosettacommons.org/docs/latest/application\_documentation/docking/DARC) app

> 通过光线投射（ray casting）算法在gpu上加速

* [FlexPepDock](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/FlexPepDockMover)

> 同时对肽的骨架自由度进行采样

* SymDockProtocol

> 对低聚物对接

* [RigidBodyTransMover](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/RigidBodyTransMover)

> 手动操纵跨越跳跃的两个物体的相对位置

* RigidBodyPerturbNoCenter
* UnbiasedRigidBodyPerturbNoCenter
* UniformRigidBodyCM
* Docking
* [DockingInitialPerturbation](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/DockingInitialPerturbationMover)
* [DockingProtocol](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/DockingProtocolMover)
* DnaInterfaceMinMover
* SymFoldandDockRbTrialMover
* [HighResDocker](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/HighResDockerMover)
* DockSetupMover
* [DockWithHotspotMover](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/DockWithHotspotMover)

## 化学连通性

* [ForceDisulfides](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/ForceDisulfidesMover)

> 给定残基对列表（例如，二硫化物），重新填充它们周围的残基，但不要改变 CYS 类型残基本身。

* DisulfideInsertion

> 将两个残基位突变为CYS:二硫位，将它们构象连接，并添加约束条件，使其对位姿具有良好的二硫位距、角度和二面体。用于在短的潜在的大环肽中添加二硫键。

* [DisulfideMover](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/DisulfideMover)

> 给定两个残基位置，将两者突变为CYS:二硫键，并将其构象连接;没有重新填充或最小化

* [Disulfidize](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/DisulfidizeMover)

> 在一个姿势中尝试每一对可能的残基，尝试引入一个或多个新的二硫化物，只要它们得分好

## 设计

* [FastDesign](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/FastDesignMover)

> [在设计中控制氨基酸组成](https://new.rosettacommons.org/docs/latest/rosetta\_basics/scoring/AACompositionEnergy)

* CoupledMover

> FastRelax mover在重新填充时的设计

* [RemodelMover](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/RemodelMover)

> 功能极为多样:可做设计、重新填充、完成骨架重塑、二硫键构建、酶设计等

* EnzdesRemodelMover
* [PredesignPerturbMover](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/PredesignPerturbMover)
* [DesignMinimizeHbondsMover](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/DesignMinimizeHBondsMover)
* [GreedyOptMutationMover](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/GreedyOptMutationMover)
* ParetoOptMutationMover
* [MutateResidue](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/MutateResidueMover)
* [RandomMutation](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/RandomMutationMover)
* [ConsensusDesignMover](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/ConsensusDesignMover)
* AntibodyDesignMover
* AntibodyDesignProtocol
* DesignProteinBackboneAroundDNA
* MatDesGreedyOptMutationMover
* FlxbbDesign

> 可以被赋予一个蓝图文件以推断成一个移动图（movemap）；做设计，可以做一些弛豫；在设计之前将你的姿势转换为丙氨酸

* DnaInterfaceMultiStateDesign
* NcbbDockDesign

> 非标准骨架的对接与设计(类似肽（peptidomimetics）)

* LigandDesign

> 不是设计移动本身，但他们偏向氨基酸组成的序列，因此可以有助于设计协议。
>
> * SetAACompositionPotential
> * [FavorNativeResidue](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/FavorNativeResidueMover)
> * FavorNonNativeResidue
> * [FavorSequenceProfile](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/FavorSequenceProfileMover)
> * [FavorSymmetricSequence](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/FavorSymmetricSequenceMover)
> * FindConsensusSequence

## 分析

* [InterfaceAnalyzerMover](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/analysis/InterfaceAnalyzerMover)
* [ComputeLigandRDF](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/ComputeLigandRDFMover)
* [InterfaceScoreCalculator](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/InterfaceScoreCalculatorMover)
* [MetricRecorder](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/MetricRecorderMover)
* LoadVarSolDistSasaCalculatorMover
* LoadZnCoordNumHbondCalculatorMover

## 对称接口

* [SymRotamerTrialsMover](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/SymPackRotamersMover)
* [SymPackRotamersMover](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/SymPackRotamersMover)
* SymDockProtocol
* Symmetric oligomer docking
* Symmetrizer

> 在功能上是一个优化推动者；将采用与对称性有足够小偏差的姿势并解决它们。

* [TaskAwareSymMinMover](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/TaskAwareSymMinMover)
* [SymMinMover](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/SymMinMover)

> 最小化对称

* [DetectSymmetry](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/DetectSymmetryMover)
* GenericSymmetricSampler
* fold and dock
  * SymFoldandDockMoveRbJumpMover
  * SymFoldandDockSlideTrialMover
  * SymFoldandDockRbTrialMover

## 分子动力学代码

* CartesianMD
* [HamiltonianExchange](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/composite\_protocols/metropolis\_hastings/Tempering-MetropolisHastings#HamiltonianExchange)

## 类肽（Peptidomimetics）

* NcbbDockDesign
* OopCreatorMover
* OopDockDesign

## 抗体建模与设计

* [AntibodyDesignMover](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/antibodies/AntibodyDesignMover)
* [AntibodyDesignModeler](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/antibodies/AntibodyDesignModeler)
* [AntibodyDesignProtocol](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/antibodies/AntibodyDesignProtocol)
* [CDRDihedralConstraintMover](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/antibodies/CDRDihedralConstraintMover)
* [ParatopeSiteConstraintMover](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/antibodies/ParatopeSiteConstraintMover)
* [ParatopeEpitopeSiteConstraintMover](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/movers\_pages/antibodies/ParatopeEpitopeSiteConstraintMover)

## 更多资源

* [RosettaScripts](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/RosettaScripts)：RosettaScripts 主页
* [RosettaScripts Movers列表](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/Movers/Movers-RosettaScripts)
* [入门](./)：Rosetta 新用户的页面
* [学习生物物理学和计算建模的资源](学习生物物理学.md)
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
* [Rosetta 概述](https://new.rosettacommons.org/docs/latest/rosetta\_basics/structural\_concepts/Rosetta-overview): Rosetta 主要概念概述
