![image-20210607142617472](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210607142617472.png)

> 这种问题，在windows下出现得频率高些。我估计主要是git本身就是基于linux开发的，在windows上，容易缺失一些环境。

方法如下：

- 1.创建临时环境变量：

> windows上命令行输入：

`set GIT_SSL_NO_VERIFY=true git clone`

> Linux下：

`env GIT_SSL_NO_VERIFY=true git push`
