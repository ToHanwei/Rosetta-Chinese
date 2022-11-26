---
description: >-
  本页面翻译自：https://www.rosettacommons.org/demos/latest/tutorials/Working_With_Rosetta/working_with_rosetta
---

# 😜 与Rosetta一起工作

作者:Frank Teets最后修改2016年6月21日

### 依赖软件

为了有效地使用Rosetta，还需要一些额外的程序:

* 一个能够输出纯文本文件的文本编辑器;对于命令行工具，大多数人使用[Emacs](https://www.gnu.org/software/emacs/manual/html\_node/emacs/index.html)、[Vim](https://www.washington.edu/computing/unix/vi.html)、[Nano](https://www.nano-editor.org/dist/v2.0/nano.html)或类似工具。对于基于GUI的工具，[Sublime Text](https://www.sublimetext.com/)和[TextMate](https://macromates.com/)在mac上非常好，Gedit包含在Ubuntu Linux中。注意，像Microsoft word和Libre/Open Office这样的文字处理程序并不令人满意，因为它们引入的额外格式会让Rosetta感到困惑。
* 一个分子可视化工具。Rosetta不包括能够可视化它所创建的输出文件的方法；必须使用[PyMOL](https://www.pymol.org/)或[Chimera](https://www.cgl.ucsf.edu/chimera/)这样的可视化工具来检查输出的PDBs。Rosetta包含一个PyMOLObserver，用于在PyMOL中直接查看其输出；设置PyMOLObserver的说明可[在此](https://www.rosettacommons.org/docs/latest/rosetta\_basics/graphics-and-guis)找到。
* 一个终端。Unix和Apple用户默认安装了合适的终端。试图在Mac或Unix机器上远程运行Rosetta的Windows用户将需要一个像PuTTY这样的工具来提供必要的接口。

它还可以帮助您熟悉命令行接口的基础知识。特别有用的命令包括:

<pre class="language-bash"><code class="lang-bash">ls foo #显示目录foo中的文件列表
mv foo #将当前工作目录移动到目录foo
<strong>mv foo bar #如果bar是一个目录，则将foo移动到bar中;如果不是，则移动到名为bar的文件中
</strong><strong>cp foo bar #如果bar是一个目录，则将foo复制到bar中;如果不是，则复制到名为bar的文件中
</strong>ln -s &#x3C;path_to_bar> foo #建立一个从foo到bar的软连接
top #列出当前运行的进程及其进程id</code></pre>
