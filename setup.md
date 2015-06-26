# Introduction #

在没有物理TPM的机器上，可以使用TPM Emulator完成TPM的相关实验。下面介绍一下如何安装TPM Emulator以及TSS。然后完成相应的实验。


# Details #

这里以Ubuntu 12.04为例，其它的发行版与其类似。

## 1、源码安装TPM Emulaot ##
### 1.1下载TPM Emulator源码 ###
TPM Emulator的下载网址为： http://code.google.com/p/trusted-computing-project/downloads/detail?name=tpm-emulator.tar.gz&can=2&q=

### 1.2然后解压并编译安装TPM Emulator： ###

```
tar xvzf tpm-emulator.tar.gz
cd tpm-emulator
sudo apt-get install libgmp-dev cmake #Ubuntu 10.04 下用：sudo apt-get install libgmp3-dev cmake
./build.sh
cd build
sudo make install
sudo depmod -a
```

## 2、安装TSS软件栈 ##
运行以下命令：

```
sudo apt-get install libtspi-dev trousers
```

## 3、启动实验环境 ##
要开启tpm模拟器，以及tcsd：

```
sudo modprobe tpmd_dev
sudo tpmd -d -f clear
```

再打开一个终端(注意：前面tpmd那个终端不要关)：

```
sudo tcsd
```
## 4、下载并编译实验源代码 ##
### 4.1下载实验源代码 ###
下载网址为：http://trusted-computing-project.googlecode.com/files/trusted-computing-projectv0.3.tar.gz

### 4.2然后解压并编译 ###

```
tar xvzf trusted-computing-projectv0.3.tar.gz
cd trusted-computing-projectv0.3
make clean
make
```

### 4.3参考trusted-computing-projectv0.3目录下的README，继续后面的实验 ###