---
title: anaconda安装tensorflow报错 No module named 'tensorflow'解决方法(windows)
layout: post
---
这个错误的原因可能是，anaconda安装的python版本为3.7，现在tensorflow仅支持python 3.6
 
改变python版本：首先在命令行创建一个名为python36的环境，指定的Python版本是3.6。如下：
    conda create --name python36 python=3.6
    activate python36
    python --version #查看 发现已经是3.6版本
    
现在在命令行里试一下：
    python
    import tensorflow
    
发现可以用了，但是在jupyter notebook里还是不行。
在命令行：
    jupyter kernelspec list
    
给出的地址指向一个包含kernel.json的文件夹，打开这个json文件，发现里面指向的python.exe仍然是python3.7，错误的原因找到了。
在命令行：
    conda install jupyter notebook #重新安装Jupyter
    
完美解决。（用deactivate可以退出Python36环境）