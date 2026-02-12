---
tags:
  - software
---
### 1. 在Windows当中安装并运行SageMath 10

#### 1.1 安装WSL以及Linux子系统

遵照[Sagemath官方安装教程](https://doc.sagemath.org/html/en/installation/index.html)，首先我们需要给Windows的WSL安装一个Linux子系统。这是SageMath 10版本的安装方式，之前的版本例如9.x版本可以直接运行Windows的安装包进行安装。

![[Microsoft Store Ubuntu.png]]

#### 1.2 通过conda安装SageMath

我们现在正在使用一个名为[Conda](https://anaconda.org/anaconda/conda)的包管理器来安装SageMath。Conda能够帮助我们创建独立的“环境”，在这些环境中安装特定版本的软件包及其依赖项，从而避免不同项目之间的依赖冲突。

由于SageMath的依赖比较复杂，直接使用Ubuntu的系统包管理器（如apt）可能会遇到版本兼容性问题。因此，我们这里使用专门为科学计算设计的包管理器Conda是一个更可靠的方法。

首先运行
```bash
curl -L -O "https://github.com/conda-forge/miniforge/releases/latest/download/Miniforge3-$(uname)-$(uname -m).sh"
```

* 这一步的目的是从Conda-Forge社区提供的Miniforge的最新版本下载安装脚本。Miniforge是一个轻量级的Conda发行版，它预装了Conda包管理器和一些必要的依赖项。Conda-Forge是一个由社区驱动的大型Conda软件包仓库，其中包含了SageMath。
![[sagemath installation gif1.gif]]
然后运行:

```bash
bash Miniforge3-$(uname)-$(uname -m).sh
```

* 这一步的目的是运行下载的Miniforge安装脚本。这个脚本会引导你完成Miniforge的安装过程，包括询问安装位置、是否初始化 Conda等。安装成功后，你的系统中就会拥有conda这个命令。
![[sagemath installation gif2.gif]]
然后运行:
```bash
conda create -n sage sage python=3.11
```
* 这一步的目的是使用conda命令创建一个名为sage的独立环境，并在该环境中安装SageMath软件包以及指定版本的Python (此处是3.11，当然我们也可以自行选择别的版本的python) 和 SageMath所需的所有其他依赖项。通过将SageMath安装在一个独立的环境中，可以避免它与其他Python项目或系统库之间的潜在冲突。
![[sagemath installation gif 3.gif]]
到现在我们已经可以启动并运行SageMath：

```bash
conda activate sage
sage
```

![[sagemath installation gif 4.gif]]
#### 1.3 安装Jupyter Notebook

在之前的基础上，我们现在需要通过Conda安装Jupyter Notebook：
```bash
conda install -c conda-forge jupyter
```

![[sagemath installation gif 5.gif]]
#### 1.4 通过Jupyer Notebook运行Sage代码

因为Jupyter可以通过HTTP协议把Notebook的界面以网页的形式发送到浏览器当中，因此我们可以使用Web浏览器（比如Chrome,Firefox,Safari等）充当Jupyter Notebook的用户界面。

首先我们运行下面的程序，通过Jupyter Notebook启动Sage而不是按照1.3节末尾那样直接启动它：

```bash
conda activate sage
sage -n jupyter
```

然后我们需要把程序输出的链接复制粘贴到**Windows主系统的浏览器**当中（因为WSL的子系统和Windows主系统的网络是互通的），并访问。

![[sagemath installation gif 6.gif]]
打开以后的界面如下
![[sagemath installation gif 7.gif]]