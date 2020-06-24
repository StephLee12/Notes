- [Anaconda环境配置](#anaconda%e7%8e%af%e5%a2%83%e9%85%8d%e7%bd%ae)
  - [Anaconda下载](#anaconda%e4%b8%8b%e8%bd%bd)
  - [安装Pytorch](#%e5%ae%89%e8%a3%85pytorch)
  - [在虚拟环境下启用Jupyter](#%e5%9c%a8%e8%99%9a%e6%8b%9f%e7%8e%af%e5%a2%83%e4%b8%8b%e5%90%af%e7%94%a8jupyter)

# Anaconda环境配置

👉 重装了Anaconda环境 记录一下

👉 卸载时在Anaconda目录下有``uninstall.exe``

👉 使用``nvcc --version``查看CUDA版本

## Anaconda下载

👉 [在清华的镜像站](https://mirrors.tuna.tsinghua.edu.cn/help/anaconda/)用**迅雷或者IDM**下载比较快

👉 安装过程

- 安装时不选择``Add PATH``
- 安装完成后将``Anaconda Anaconda\Scripts Anaconda\Library\mingw-w64\bin Anaconda\Library\bin``加入环境变量

👉 Anaconda添加镜像

- [见此Blog](https://blog.csdn.net/WannaSeaU/article/details/88427010)

👉 Anaconda创建虚拟环境

- ``conda create -n env_name python=3.7``

👉 Anaconda常用命令

- [Blog](https://blog.csdn.net/wdx1993/article/details/83660717)

## 安装Pytorch

👉 检查CUDA版本``nvcc --version``

👉 [官网有相关的命令](https://pytorch.org/) 但注意**最后的``-c pytorch``要去掉，否则无法用清华源安装

👉 安装之后可以用以下代码测试

```python
import torch
print(torch.cuda.is_available())
```

## 在虚拟环境下启用Jupyter

👉 步骤

- ``conda install nb_conda``
- ``conda install ipykernel``
- 将环境写入Jupyter的kernel ``python -m ipykernel install --user --name env_name --display-name "display_name"``
- 在终端执行``jupyter notebook``

👉 [安装插件](https://www.cnblogs.com/huabaixiaoduanku/p/7858479.html)