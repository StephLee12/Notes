# Little Summary

## 安装Ubuntu双系统

[B站链接](https://www.bilibili.com/video/av9855447?from=search&seid=2937186197372212305)

但是为了安装Nvidia驱动，在``BIOS Setup``中要设置``Secure Boot``为``Disabled``

## 安装Python

在安装``Python3.7.0``以上的版本时，要先安装一个依赖``sudo apt-get install libffi-dev``

这样才可以在编译安装``Python``时配套安装对应的``pip``

[安装``Python``相应链接](https://www.cnblogs.com/yjlch1016/p/10359169.html)

要使用``pip`` 必须安装``ssl``的依赖，[stackoverflow相应链接](https://stackoverflow.com/questions/41328451/ssl-module-in-python-is-not-available-when-installing-package-with-pip3)

在使用``pip``的时候，使用指令``pip install xxx``显示权限不够，但用``sudo pip install xxx``又会显示``current usr is not the directory's owner``类似的警告(具体的记不清楚了) 可以不用管 因为用了``sudo``之后提权了，可以在``Python``中输入以下的指令，查看``Python``搜索包的路径

```python
import sys
sys.path
```

使用``pip install xx``包安装在``/home``下，而使用``sudo pip install xxx`` 包安装在全局中，但这两个目录都包含在``sys.path``中

## 安装驱动

无需多说 [链接中的很详细](https://blog.csdn.net/wf19930209/article/details/81877822)

关于禁止nouveau 最好手动``blacklist``

## 配置deepmimic

1. Bullet

    按照``readme``没有问题

2. Eigen

    安装都没有问题 但是在写测试程序的时候遇到了问题

    在用``gcc``编译源码时会报错 好像是无法识别头文件

    测试程序中的两条语句为

    ```c
    #include<Eigen/Dense>
    #include<unsupported/Eigen/FFT>
    ```

    安装的eigen3实际位于``/usr/local/include``目录下，可以用``ls``或者``less``具体查看

    解决办法:符号链接

    ``sudo ln -sf eigen3/Eigen Eigen``

    ``sudo ln -sf eigen3/unsupported unsupported``

    再次编译 没有问题

3. freeglut

    安装``freeglut``的时候没有问题

    在写一个小程序验证的时候出现了问题,记得报错是``找不到libglut.so.3`` 但该文件明明安装在了``/usr/local/lib``下

    原因: ``/etc/ld.so.conf``文件记录了动态链接库的路径，系统默认搜索的是``/lib /usr/lib``(i.e. 可以通过``ldd``命令来查看程序调用的包的路径 以及包的缺失情况)

    解决方法: 只需将``/usr/local/lib``写入配置文件即可

    ``sudo echo "/usr/local/lib" >> /etc/ld.so.conf``

    添加了之后一定要执行``ldconfig``才会生效

4. 测试OpenGL是否安装成功

    [Demo](https://blog.csdn.net/san1156/article/details/74923025)

    其他的安装过程按照``readme``即可