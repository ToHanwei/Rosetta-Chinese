---
description: >-
  该页面翻译自：https://new.rosettacommons.org/docs/latest/getting_started/Rosetta-canon
---

# 😣 Rosetta法则

起初，罗塞塔是由Centroid和Fragment创造的。 全套原子的姿势是没有构型的，是空的；势能表面上是未知的。Baker的学生在蛋白质结构的表面改动。 Rosetta站出来说，让我们来建立一个标准。 Rosetta看到了折叠漏斗，并看到它是好的。就这样，贝克的学生把模型和诱饵分开了。

Rosetta有较长的学术历史，有大量的论文对代码库的内容和用户的成就都是基础性的。我们将这些参考文献提炼成一个核心规范：我们假设对方读过的论文，我们希望读过的论文，我们应该读过的论文，以及在幸运的情况下，我们已经读过的论文。

这些论文按罗塞塔进入该领域的顺序排列，并在每组中按时间顺序排列。

可以在[这里](http://www.rosettacommons.org/about/pubs)找到更完整（但可能不是100%完整）的清单。

## 蛋白质结构预测

* Simons K, Kooperberg C, Huang E, Baker D (1997)\
  [Assembly of Protein Tertiary Structures from Fragments with Similar Local Sequences using Simulated Annealing and Bayesian Scoring Functions.](http://www.ncbi.nlm.nih.gov/pubmed/9149153) (pubmed link)\
  J. Mol. Biol. 268:209-225\
  Simons et al. describe the method of combining simulated annealing with fragment libraries to generate native-like structures.
* Simons K, Ruczinski I, Kooperberg C, Fox B, Bystroff C, Baker D (1999)\
  [Improved Recognition of Native-Like Protein Structures Using a Combination of Sequence-Dependent and Sequence-Independent Features of Proteins.](http://www.ncbi.nlm.nih.gov/pubmed/) (pubmed link)\
  Proteins 34:82-95\
  Simons et al. describe the development of an improved score function containing secondary structure packing terms.
* Simons KT, Bonneau R, Ruczinski I, Baker D (1999)\
  [Ab initio protein structure prediction of CASP III targets using ROSETTA.](http://www.ncbi.nlm.nih.gov/pubmed/10526365) (pubmed link)\
  Proteins Suppl 3:171-6\
  The first use of the Rosetta algorithm successfully predicted ab initio protein structures to an RMSD within 6.4, 6.0, and 3.8Å.
* Raveh B, London N, Schueler-Furman O (2010)\
  [Sub-angstrom modeling of complexes between flexible peptides and globular proteins.](http://www.ncbi.nlm.nih.gov/pubmed/20455260) (pubmed link)\
  Proteins 78:2029-40\
  Raveh et al. describe algorithms to predict the bound state of flexible peptides in protein pockets.
* DiMaio F, Leaver-Fay A, Bradley P, Baker D, Andre I (2011)\
  [Modeling symmetric macromolecular structures in Rosetta3.](http://www.ncbi.nlm.nih.gov/pubmed/21731614) (pubmed link)\
  PLoS One 6:e20450\
  DiMaio et al. describe a framework for efficiently modeling highly symmetric oligomers using a single monomer, the inter-monomer interface, and mathematical relationships between subunits.

## 打分 <a href="#scoring" id="scoring"></a>

**See also** [**Scorefunction History#publications timeline**](https://new.rosettacommons.org/docs/latest/rosetta\_basics/scoring/Scorefunction-History#publications-timeline)

* Rohl CA, Strauss CE, Misura KM, Baker D (2004) [Protein structure prediction using Rosetta.](http://www.ncbi.nlm.nih.gov/pubmed/15063647) (pubmed link)\
  Methods in Enzymology.\
  This paper, often called the **Rohl review**, is a window into Rosetta's early scorefunction, and remains an excellent reference for early forms of the score function terms. It can be a little hard to find online, but paper photocopies float around most Rosetta labs.
* Kuhlman B, Dantas G, Ireton GC, Varani G, Stoddard BL, Baker D (2003)\
  [Design of a novel globular protein fold with atomic-level accuracy.](http://www.ncbi.nlm.nih.gov/pubmed/14631033) (pubmed link)\
  Science 302:1364-8\
  This paper, often called the **Top7 paper**, is primarily a design paper (see below), but is important for scoring as it introduces sequence-related energy terms (reference energies, p\_aa\_pp, etc). The supplemental is most relevant for scoring.
* Leaver-Fay A, O'Meara MJ, Tyka M, Jacak R, Song Y, Kellogg EH, Thompson J, Davis IW, Pache RA, Lyskov S, Gray JJ, Kortemme T, Richardson JS, Havranek JJ, Snoeyink J, Baker D, Kuhlman B (2013)\
  [Scientific benchmarks for guiding macromolecular energy function improvement.](http://www.ncbi.nlm.nih.gov/pubmed/23422428) (pubmed link)\
  Methods Enzymol 523:109-43\
  Leaver-Fay et al. describe OptE, a methodology for using sequence-recovery and rotamer-recovery benchmarks to improve weights sets for scoring functions. This was used in a [separate paper](http://www.ncbi.nlm.nih.gov/pubmed/25866491) to generate [Talaris2013/4](https://new.rosettacommons.org/docs/latest/rosetta\_basics/scoring/score-types), the current state-of-the-art general purpose Rosetta energy function.
* REF2015: Park H, Bradley P, Greisen Jr. P, Liu Y, Mulligan VK, Kim DE, Baker D, DiMaio F (2016) [Simultaneous Optimization of Biomolecular Energy Functions on Features from Small Molecules and Macromolecules.](https://www.ncbi.nlm.nih.gov/pubmed/27766851) (pubmed link) J Chem Theory Comput. 2016;12(12):6201–6212. PubMed PMID 27766851
* Review: Alford RF, Leaver-Fay A, Jeliazko JR, O'Meara MJ, DiMaio FP, Park H, Shapovalov MV, Renfrew PD, Mulligan VM, Kappel K, Labonte JW, Pacella MS, Bonneau R, Bradley P, Dunbrack RL, Das R, Baker D, Kuhlman B, Kortemme T, Gray JJ (2017) [The Rosetta all-atom energy function for macromolecular modeling and design.](http://pubs.acs.org/doi/abs/10.1021/acs.jctc.7b00125)(acs link) J Chem Theory Comput. 2017;13(6):3031-3048

## 对接 <a href="#docking" id="docking"></a>

* Gray JJ, Moughon S, Wang C, Schueler-Furman O, Kuhlman B, Rohl CA, Baker D (2003)\
  [Protein-protein docking with simultaneous optimization of rigid-body displacement and side-chain conformations.](http://www.ncbi.nlm.nih.gov/pubmed/12875852) (pubmed link)\
  J Mol Biol 331:281-99\
  Gray et al. produce the first effort in Rosetta to couple rigid-body docking and sidechain optimization; in so doing, they frequently obtain binding funnels that typically recapitulate at least 25% of binding contacts.
* Chaudhury S, Gray JJ (2008)\
  [Conformer selection and induced fit in flexible backbone protein-protein docking using computational and NMR ensembles.](http://www.ncbi.nlm.nih.gov/pubmed/18640688) (pubmed link)\
  J Mol Biol 381:1068-87\
  Chaudhury and Gray demonstrate algorithms that echo traditional lock-in-key complexing (rigid body docking) and more sophisticated models (conformer selection via EnsembleDock; induced fit via backbone minimization on the smaller partner of the complex; a combination of both) and validate the EnsembleDocking protocol by illustrating that docking-competent conformers exist in the unbound ensemble.
* Sircar A, Chaudhury S, Kilambi KP, Berrondo M, Gray JJ (2010)\
  [A generalized approach to sampling backbone conformations with RosettaDock for CAPRI rounds 13-19.](http://www.ncbi.nlm.nih.gov/pubmed/20535822) (pubmed link)\
  Proteins 78:3115-23\
  Sircar et al. describe their use of the EnsembleDock and SnugDock algorithms to generate improved docking models for the CAPRI competition.

## 设计 <a href="#design" id="design"></a>

* Kuhlman B, Dantas G, Ireton GC, Varani G, Stoddard BL, Baker D (2003)\
  [Design of a novel globular protein fold with atomic-level accuracy.](http://www.ncbi.nlm.nih.gov/pubmed/14631033) (pubmed link)\
  Science 302:1364-8\
  Kuhlman et al. demonstrate the computational design of a protein with an entirely novel fold. The significance of this result arises because prior design efforts involved stabilizing or modifying existing, known folds; the ability to _de novo_ create a protein was wholly original.
* Guntas G, Purbeck C, Kuhlman B (2010)\
  [Engineering a protein-protein interface using a computationally designed library.](http://www.ncbi.nlm.nih.gov/pubmed/20974935) (pubmed link)\
  Proc Natl Acad Sci U S A 107:19296-301\
  Computational design at twenty amino acid positions was used to semi-direct two protein libraries, which greatly outperformed the control library where all residues were allowed: the former produced multiple mid-nanomolar binders while the latter could not produce bunders under fifty micromolar after four rounds of selection.

## 突变分析 <a href="#mutational-analysis" id="mutational-analysis"></a>

* Kortemme T, Kim DE, Baker D (2004)\
  [Computational alanine scanning of protein-protein interfaces.](http://www.ncbi.nlm.nih.gov/pubmed/14872095) (pubmed link)\
  Sci STKE 2004:pl2\
  Kortemme et al. exhibit an alanine scanning algorithm for protein-protein interfaces that correctly predicts 79% of hot spot residues.
* Kellogg EH, Leaver-Fay A, Baker D (2011)\
  [Role of conformational sampling in computing mutation-induced changes in protein structure and stability.](http://www.ncbi.nlm.nih.gov/pubmed/21287615) (pubmed link)\
  Proteins 79:830-8\
  Kellogg et al. explore methods for computing the stability change corresponding to a point mutation in a protein with variable conformational sampling and scoring function selection.

## 配体对接 <a href="#ligand-docking" id="ligand-docking"></a>

* Meiler J, Baker D (2006)\
  [ROSETTALIGAND: protein-small molecule docking with full side-chain flexibility.](http://www.ncbi.nlm.nih.gov/pubmed/16972285) (pubmed link)\
  Proteins 65:538-48\
  The original incorporation of ligand molecules into Rosetta, due to Meiler and Baker, permitted rotamer optimization on the protein partner and obtains a correlation of 0.63 for interaction energy versus experimental binding energy.
* Davis IW, Baker D (2009)\
  [RosettaLigand docking with full ligand and receptor flexibility.](http://www.ncbi.nlm.nih.gov/pubmed/19041878) (pubmed link)\
  J Mol Biol 385:381-92\
  Davis and Baker incorporate receptor flexibility via backbone minimization and obtain correct cross-docking ligand orientations within 2A RMSD in 64% of cases.
* Lemmon G, Meiler J. (2012) [Rosetta Ligand docking with flexible XML protocols.](http://www.ncbi.nlm.nih.gov/pubmed/22183535) (pubmed link)\
  Methods Mol Biol. 2012;819:143-55\
  The RosettaLigand logic was transitioned to XML.

## Loop建模 <a href="#loop-modeling" id="loop-modeling"></a>

* Wang C, Bradley P, Baker D (2007) [Protein-protein docking with backbone flexibility.](http://www.ncbi.nlm.nih.gov/pubmed/17825317) (pubmed link)\
  Mol Biol. 2007 Oct 19;373(2):503-19.\
  The title is a little misleading. This paper is valuable for introducing the [FoldTree](https://new.rosettacommons.org/docs/latest/rosetta\_basics/structural\_concepts/foldtree-overview) and [CCD](https://new.rosettacommons.org/docs/latest/application\_documentation/structure\_prediction/loop\_modeling/loopmodel-ccd) (cyclic coordinate descent) loop closure to Rosetta.
* Mandell DJ, Coutsias EA, Kortemme T (2009)\
  [Sub-angstrom accuracy in protein loop reconstruction by robotics-inspired conformational sampling.](http://www.ncbi.nlm.nih.gov/pubmed/19644455) (pubmed link)\
  Nat Methods 6:551-2\
  Mandell et al. describe the kinematic loop closure algorithm for remodeling protein loop geometry.

## RNA <a href="#rna" id="rna"></a>

* Das R, Baker D (2007)\
  [Automated de novo prediction of native-like RNA tertiary structures.](http://www.ncbi.nlm.nih.gov/pubmed/17726102) (pubmed link)\
  Proc Natl Acad Sci U S A 104:14664-9\
  Das and Baker describe successful prediction of RNA structure from sequence data. They reproduce 90% of Watson-Crick base pairs and more than one third of noncanonical features.
* Sripakdeevong P, Kladwang W, Das R (2011)\
  [An enumerative stepwise ansatz enables atomic-accuracy RNA loop modeling.](http://www.ncbi.nlm.nih.gov/pubmed/22143768) (pubmed link)\
  Proc Natl Acad Sci U S A 108:20573-8\
  Sripakdevong et al. discuss an ansatz by which they enumerate and score RNA loop conformations, enabling the solution of heretofore intractable "RNA puzzles".

## 酶设计 <a href="#enzyme-design" id="enzyme-design"></a>

* Jiang L, Althoff EA, Clemente FR, Doyle L, Röthlisberger D, Zanghellini A, Gallaher JL, Betker JL, Tanaka F, Barbas CF 3rd, Hilvert D, Houk KN, Stoddard BL, Baker D (2008) [De novo computational design of retro-aldol enzymes.](http://www.ncbi.nlm.nih.gov/pubmed/18323453) (pubmed link)\
  Science 319:1387-91
* Siegel JB, Zanghellini A, Lovick HM, Kiss G, Lambert AR, St Clair JL, Gallaher JL, Hilvert D, Gelb MH, Stoddard BL, Houk KN, Michael FE, Baker D (2010)\
  [Computational design of an enzyme catalyst for a stereoselective bimolecular Diels-Alder reaction.](http://www.ncbi.nlm.nih.gov/pubmed/20647463) (pubmed link)\
  Science 329:309-13\
  Siegel et al. design a stereoselective and chemoselective Diels-Alderase, obtain its crystal structure, and illustrate that mutations at the putative binding site can tune its substrate specificity.

## Rosetta开发 <a href="#rosetta-development" id="rosetta-development"></a>

* Leaver-Fay A, Tyka M, Lewis SM, Lange OF, Thompson J, Jacak R, Kaufman K, Renfrew PD, Smith CA, Sheffler W, Davis IW, Cooper S, Treuille A, Mandell DJ, Richter F, Ban YE, Fleishman SJ, Corn JE, Kim DE, Lyskov S, Berrondo M, Mentzer S, Popović Z, Havranek JJ, Karanicolas J, Das R, Meiler J, Kortemme T, Gray JJ, Kuhlman B, Baker D, Bradley P (2011)\
  [ROSETTA3: an object-oriented software suite for the simulation and design of macromolecules.](http://www.ncbi.nlm.nih.gov/pubmed/21187238) (pubmed link)\
  Methods Enzymol 487:545-74\
  This is the **Rosetta3 paper** that describes the transition from C++-but-monolithic Rosetta++ to [object-oriented](https://en.wikipedia.org/wiki/Object-oriented\_programming)-C++ Rosetta3. It introduces many of the major modern classes.
* Cooper S, Khatib F, Treuille A, Barbero J, Lee J, Beenen M, Leaver-Fay A, Baker D, Popović Z, Players F (2010)\
  [Predicting protein structures with a multiplayer online game.](http://www.ncbi.nlm.nih.gov/pubmed/20686574) (pubmed link)\
  Nature 466:756-60\
  Cooper et al.'s development of the [FoldIt](https://new.rosettacommons.org/docs/latest/FoldIt) game showed that highly parallel human intuition is a useful tool for, well, folding it (proteins).
* Chaudhury S, Lyskov S, Gray JJ (2010)\
  [PyRosetta: a script-based interface for implementing molecular modeling algorithms using Rosetta.](http://www.ncbi.nlm.nih.gov/pubmed/20061306) (pubmed link)\
  Bioinformatics 26:689-91\
  Chaudhury et al. developed a Python based scripting interface to Rosetta functionality ([PyRosetta](https://new.rosettacommons.org/docs/latest/scripting\_documentation/PyRosetta/PyRosetta)), permitting users to easily compose protocols without interacting with the C++ layer.
* Sarel J. Fleishman , Andrew Leaver-Fay, Jacob E. Corn, Eva-Maria Strauch, Sagar D. Khare, Nobuyasu Koga, Justin Ashworth, Paul Murphy, Florian Richter, Gordon Lemmon, Jens Meiler, David Baker (2011)\
  [RosettaScripts: A Scripting Language Interface to the Rosetta Macromolecular Modeling Suite](http://journals.plos.org/plosone/article?id=10.1371/journal.pone.0020161) (pubmed link)\
  PLoS ONE 6(6): e20161\
  Fleishman et al. develop an XML-like interface to directly access protocol-level functionalities (and as such requires a compiled version of C++ Rosetta). [RosettaScripts](https://new.rosettacommons.org/docs/latest/scripting\_documentation/RosettaScripts/RosettaScripts) allows the user to circumnavigate coding in C++, which in turn permits for the rapid development of new protocols.

## Peptidomimetics <a href="#peptidomimetics" id="peptidomimetics"></a>

* Drew K, Renfrew PD, Craven TW, Butterfoss GL, Chou FC, Lyskov S, Bullock BN, Watkins A, Labonte JW, Pacella M, Kilambi KP, Leaver-Fay A, Kuhlman B, Gray JJ, Bradley P, Kirshenbaum K, Arora PS, Das R, Bonneau R (2013)\
  [Adding diverse noncanonical backbones to rosetta: enabling peptidomimetic design.](http://www.ncbi.nlm.nih.gov/pubmed/23869206) (pubmed link)\
  PLoS One 8:e67051\
  Drew et al. create custom modes for backbone sampling to incorporate peptidomimetic scaffolds into Rosetta, enabling the design of amino acid-derived nonnatural foldamers.
* Renfrew PD, Craven TW, Butterfoss GL, Kirshenbaum K, Bonneau R (2014)\
  [A rotamer library to enable modeling and design of peptoid foldamers.](http://www.ncbi.nlm.nih.gov/pubmed/24823488) (pubmed link)\
  J Am Chem Soc 136:8772-82\
  Renfrew et al. demonstrate that peptoid residues (N-alkylated or arylated glycines) have sidechain conformations that fall neatly into rotamer bins much like peptides and demonstrate two methods for constructing rotamer libraries to model them.

## 更多资源 <a href="#see-also" id="see-also"></a>

* [Rosetta 概述](https://new.rosettacommons.org/docs/latest/rosetta\_basics/structural\_concepts/Rosetta-overview): Rosetta 主要概念概述
* [FAQ](https://new.rosettacommons.org/docs/latest/getting\_started/FAQ) : 常见问题
* [词汇表](https://new.rosettacommons.org/docs/latest/rosetta\_basics/Glossary/Glossary)：Rosetta 术语的简要定义
* [RosettaEncyclopedia](https://new.rosettacommons.org/docs/latest/rosetta\_basics/RosettaEncyclopedia)：Rosetta术语的详细说明
* [Rosetta时间线](https://new.rosettacommons.org/docs/latest/rosetta\_basics/RosettaEncyclopedia)：Rosetta释放版本和其他新闻
* [打分函数历史](https://new.rosettacommons.org/docs/latest/rosetta\_basics/scoring/Scorefunction-History)：Rosetta打分函数的历史

