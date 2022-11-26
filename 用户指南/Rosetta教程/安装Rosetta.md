---
description: >-
  该页面翻译自：https://www.rosettacommons.org/demos/latest/tutorials/install_build/install_build
---

# 😝 安装Rosetta

### 下载Rosetta

对于任何学术或商业用途，你需要申请一个[许可证](https://els.comotion.uw.edu/express\_license\_technologies/rosetta)。【译者注：申请许可是下载这个软件的前提，申请许可后会得到几个PDF文件，其中一个上面记录了下载软件需要用到的用户名和密码，注意这里不是你注册使用的用户名和密码，而是Rosetta给你的】获得许可证对学术用户来说是免费的。获得许可证后，你可以[下载Rosetta](https://www.rosettacommons.org/software/license-and-download)。请确保你下载的版本与你所拥有的许可证相对应。当你点击时，你可以看到最新编号的版本以及每周几个的版本。有编号的版本（从Rosetta3.6开始）只是被特别标注的每周发布的版本--所有每周发布的版本都会通过与有编号的版本相同的测试套件【译者注：出于软件稳定性的个人喜好，我喜欢下载最后的稳定版本，而不是最新的版本】。

对于许多版本，我们同时提供源代码和二进制版本。二进制版本可以让你跳过编译阶段，但在工作平台上有更多限制。而 "源码 "版本应该在所有能运行Rosetta的平台上都有用。(如果你对非标准氨基酸感兴趣，也可以下载NCAA旋转异构体库）。

### 安装Rosetta

下载的文件是以.tgz为扩展名的[tar文件格式](https://en.wikipedia.org/wiki/Tar\_\(computing\))。在linux或mac系统中，你可以通过双击文件或在终端运行这个命令来解压这个压缩文件。

```bash
tar -xvzf rosetta[releasenumber].tar.gz
```

不幸的是，目前在Windows上没有支持整个Rosetta的版本。双系统或运行Linux/MacOS的虚拟机是一种替代方案。

### 编译Rosetta

在文件夹中打开你解压后的文件：Rosetta -> main -> source 或使用以下bash命令。

```bash
cd rosetta*/main/source
```

如果你下载了源代码包，你会发现bin/目录目前是空的。为了能够运行Rosetta，你需要首先编译代码。

要编译Rosetta，您需要一个c++编译器。尽管也可以使用其他符合标准的编译器，但是Rosetta开发人员通常使用[GCC](https://gcc.gnu.org/)或[Clang](http://clang.llvm.org/)来进行编译。(有关[安装编译器](https://www.rosettacommons.org/demos/latest/tutorials/install\_build/install\_build#Install-a-Compiler)的更多信息，请参见安装编译器。)

Rosetta使用SCons作为构建系统。虽然Scons可以单独下载，但Rosetta的下载包含一个版本，这是编译Rosetta时推荐使用的版本。

现在你可以用这个一般的命令行来构建Rosetta（确保你在`source`文件夹中）

```bash
./scons.py -j <number_of_cores_to_use> mode=release bin
```

\-j表示你想要使用多少个核心（core）进行编译。这个数字取决于你的电脑有多少核心。例如，下面的命令使用20个核心来构建:

```bash
./scons.py -j 20 mode=release bin
```

预计编译完成需要很长时间，一个核心可能需要几个小时。

编译完成后查看源文件夹，里面有几个新文件夹，包括bin。你现在可以运行Rosetta了!

### 更多的参数用于安装

正如您所注意到的，您运行的命令有一个“mode”选项，并且您特别提到了“bin”。您还可以使用其他一些标志和模式来安装特定的部件或功能。

* models：
  * mode=release：通过优化编译，生成一个更快的Rosetta版本
  * mode=debug (或不适用任何model)包括减慢Rosetta运行的额外检查，它主要用于开发和调试目的
* 指定要安装的部件
  * empty: 如果不提供任何位置，默认情况下只构建库
  * bin: 完成bin/目录下所有应用程序的编译
  * "bin/rosetta\_scripts.default.linuxgccrelease" or "rosetta\_scripts": 只编译上述应用程序(可以列出多个)
* extras
  * "extras=static": 安装静态二进制文件。这对于在其他系统上复制和运行应用程序非常有用
  * "extras=graphics": mode为那些支持OpenGL图形的应用程序启用OpenGL图形
  * "extras=opencl": 允许那些支持GPU的应用程序使用它
  * "extras=mpi"：将Rosetta编译为MPI[消息传递接口](https://computing.llnl.gov/tutorials/mpi/#What)格式(用于那些支持MPI运行的可执行文件)。以MPI模式运行Rosetta需要对站点进行编辑(可能非常重要)。设置文件。

例如，下面的代码只编译MPI格式的rosetta\_scripts应用程序，使用5核的发布模式:

```bash
./scons.py -j 5 mode=release bin/rosetta_scripts.mpi.linuxgccrelease extras=mpi
```

注意:当你使用不同的附加组件构建时，扩展将会改变。例如，如果您使用extras=mpi。使用rosetta\_scripts.mpi.Linuxgccrelease而不是rosetta\_scripts.default.linuxgccrelease。

编译器

默认情况下，scons使用GCC编译器构建Rosetta。但是，你可以通过使用"cxx"来指定你希望使用的编译器和版本。例如，下面的命令使用clang编译器4.5版本，使用10核在发布模式下完全构建Rosetta:

```bash
./scons.py -j 10 mode=release bin cxx=clang cxx_ver=4.5
```

### 使用Rosetta Xcode项目构建Rosetta (Mac)

如果你对使用Rosetta代码感兴趣，你可以使用Rosetta Xcode项目来构建Rosetta。您可以使用它来安装、运行、调试、浏览和编辑源代码。你可以在[这里](https://www.rosettacommons.org/docs/latest/build\_documentation/Build-Documentation)找到如何使用Xcode安装Rosetta的说明。

### PyRosetta的下载与安装

[PyRosetta](http://www.pyrosetta.org/)是一个基于Python的Rosetta交互式接口，允许用户使用Python脚本创建具有Rosetta采样和打分函数的自定义分子建模算法。PyRosetta是为Python 2.6编写的。你可以按照说明在[这里](https://www.rosettacommons.org/docs/latest/scripting\_documentation/PyRosetta/PyRosetta)和[这里](http://www.pyrosetta.org/dow)下载和安装PyRosetta。

### 带有Rosetta的集群

作为XSEDE计划的一部分，[TACC/Stampede](https://www.rosettacommons.org/docs/latest/build\_documentation/TACC)集群为授权用户集中安装了Rosetta和PyRosetta。

### 安装编译器

对于mac，安装XCode开发包。即使你不会通过XCode编译Rosetta，安装它也会安装一个编译器。(Clang，用于MacOS的最新版本) ，对于Linux，您需要从包管理系统安装编译器包。对于Ubuntu和类似的系统，可以通过`sudo apt-get install build-essential`这样的命令来安装“build-essential”包。

### 故障排除

有关安装过程中可能出现的常见错误以及如何处理这些错误的详细信息，请参阅[Rosetta安装文档](https://www.rosettacommons.org/docs/latest/build\_documentation/Build-Documentation)。

