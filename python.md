如果出现ssl  connect error
cat /etc/yum.repos.d/nss.repo 
[updates]
name=centos-updates
baseurl=https://mirrors.aliyum.com/centos/6.9/os/x86_64
gpgcheck=0
yum repolist
yum update nss
安装pyenv参照如下两个地址，pyenv实际就是python版本管理器
https://github.com/pyenv/pyenv
https://github.com/pyenv/pyenv-installer
安装python的依赖环境
yum install -y gcc make patch gdbm-devel openssl-devel sqlite-devel readline-devel zlib-devel bzip2-devel
pyenv install --list 查看pyenv可以安装的包
pyenv  install 3.5.3  --verbose

在做垃圾回收时，程序是不能操作数据的，相当于程序处于停止状态，所以垃圾回收要慎重

命名元组：返回一个元组的子类，并定义了字段

filed_names可以是逗号或者空格分开的字段的字符串，也可以是字段的列表

命令元组有点类似自定义了一个类

排序建议使用list的sort方法或者直接使用冒泡排序，冒泡排序的关键是相邻元素一一比较，一轮比较下来，最大数或者最小数一定在最左边或者最右边

习惯大泡或者小泡往右跑，冒泡排序案例如下，加flag主要是为了提升效率，只要有一轮没有发生交换，说明已经是我们想要的顺序了，可以不做排序了

 l1=[1,10,9,300,45,78]
for i in range(len(l1)-1):
        flag = False
        for n in range(len(l1)-1-i):
                if l1[n]<=l1[n+1]:
                        l1[n],l1[n+1]=l1[n+1],l1[n]
                        flag = True
        if not flag:
                break
print(l1)

直接插入排序的核心

1）有一个哨兵，可以理解为一个临时变量，该哨兵存放当前这轮要和其他数据比较的数据

2）存在一个假设的有序区，哨兵和有序区里面的元素按照索引逆序逐一比较

3）找到哨兵在有序区里面的位置，然后把哨兵插入进去

4）如果数据量很大时，优化点是，哨兵在和有序区里面的元素比较时，可以使用二分法和有序区里面的元素比较s

方法一
l2[0]就是哨兵
cat   py14.py 
l1=[25,10,18,12,16,6,9,15]
l2=[0]+l1
a=len(l2)
for i in range(2,a):
     l2[0]=l2[i]
     if l2[i-1]>l2[0]:
                while l2[i-1]>l2[0]:
                        l2[i]=l2[i-1]
                        i-=1
                l2[i]=l2[0]
print(l2)



方法二
使用变量b来充当哨兵，注意有序区就是拍好顺序的，所以只有l1[i-1]>b才会进入循环，否则不需要进入循环
cat py13.py 
l1=[25,10,18,12,16,6,9,15]
a=len(l1)
for i in range(1,a):
        b=l1[i]
        if l1[i-1]>b:
                while l1[i-1]>b:
                        l1[i]=l1[i-1]
                        i-=1
                        if i == 0:
                                break
                l1[i]=b
print(l1)

程序要注意时间复杂度和空间复杂度