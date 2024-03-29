# Windows计算机启动过程分析2

  **UEFI把efi文件识别并列在启动引导菜单里后,他可以说就已经完成了大部分的任务.接下来就要看各路efi程序的伸手了.**

  **bootmgfw.efi作为启动引导菜单里的Windows boot manager选项,一般情况下会被系统默认选中.下一步,这个efi程序即将读取一个极为重要的系统启动信息存储文件:BCD文件.**

## BCD文件

  **BCD文件是一个记录着各个操作系统启动引导信息的文件.他在本质上属于一个注册表文件.它的体积很小,毕竟几行代码不会占用很大空间.**

  **BCD文件被存储在和bootmgfw.efi同一个文件夹内.bootmgfw.efi被运行后第一步就是要读取这个BCD文件.**

  **学会编辑BCD文件是计算机运维迈向高级阶段的必经之路.BCD文件如果设置错误,将导致操作系统无法启动.**

## BCD编辑

  **我们无法直接打开BCD文件.但是,BOOTICE这个极其优秀的小工具可以辅助我们编辑BCD.**

### 编辑本机BCD文件

  **在Windows10系统里(最好是虚拟机)打开BOOTICE软件.点击BCD编辑,选择 当前系统BCD->智能编辑模式.**

#### 熟悉BOOTICE

  **软件分为左右两栏.左上方是BCD文件里包含的操作系统菜单,右侧是编辑区.**

![63354b2d0eec582eaf031cb51fa12ca4.png](https://i.miji.bid/2024/03/02/63354b2d0eec582eaf031cb51fa12ca4.png)

  **具体介绍:**

  **1.设备类型:共三种,分区:普通安装Windows的方式.Ramdisk:虚拟内存加载系统的方式.VHD:VHD安装系统的方式.**

  **2.启动磁盘:Windows系统所在的磁盘.**

  **3.启动分区:安装操作系统的分区(其实就是C盘)**

  **4.设备文件,SDI文件:在未来介绍.**

  **5.GUID:唯一识别序列号,与我们无关.**

  **6.菜单标题:显示在Windows boot manager里面的菜单名.**

  **7.启动文件:Windows系统启动时运行的第一个文件.一般都是 \Windows\system32\winload.efi**

  **8.系统路径:系统Windows文件夹所在的位置.**

  **9.safeboot:安全启动模式,可以选择普通模式,安全模式,能联网的安全模式等.**

  **10.PAE:一种技术,使32位的计算机能够识别并使用超过4GB的内存.**

  **11.NX:一种功能,可以阻止恶意代码在内存中运行.**

  **12.启动到winpe:如果操作系统是pe系统,此选项必须打钩.**

  **13.启用win8metro启动界面:win8metro启动界面是微软在Windows8系统中引入的一种新的启动界面,适用于平板操作.**

  **传统界面:**

![8ac1a030411efb175fd06788bb963939.png](https://i.miji.bid/2024/03/02/8ac1a030411efb175fd06788bb963939.png)

 **win8metro:**

![e53a26fb4ffaf666b5157fea0b826bdd.png](https://i.miji.bid/2024/03/02/e53a26fb4ffaf666b5157fea0b826bdd.png)

  **14.超时时间:若有多系统,显示选择操作系统菜单的时间.**

  **15.显示菜单(displaybootmenu):强制显示传统启动界面的启动菜单,即使计算机中只有一个系统.**

  **BOOTICE的BCD编辑功能十分实用,但是如果想要弄懂每一个选项的具体含义,需要自己勤于动手尝试.**

  **对于启用win8metro这一项,在虚拟机中建议关闭,因为加载metro界面往往比传统的启动菜单要慢很多.除了更加美观以外,作用不大.**

  **你可能很快就会疑惑:选项的勾选状态有三种情况:对钩,不勾选以及黑色方块.**

  **对钩和不勾选都很好理解,黑色方块是什么意思呢?**

  **这个问题着实困扰了笔者良久,经过大量实验,笔者没有发现黑色方块和不勾选之间有较大的区别.截止2024年3月2日,互联网上搜索没有人给出关于此问题的可靠答案.所以,大家目前就把黑色方块和不勾选混为一谈吧!**

### 使用BOOTICE编辑BCD文件

  **1.点击 添加 ,可以在BCD里新建Windows启动项,对于Windows10,11系统,请选择新建Windows7/8/8.1启动项.**

  **2.如果你是用的是一般的系统安装方式(非VHD,Ramdisk)请选择 分区 模式启动.**

  **3.启动磁盘,启动分区最终把目标定位在Windows系统的系统盘即可.**

  **4.菜单标题随意设置.**

  **5.系统路径:\Windows**

  **6.safeboot,PAE,NX无需设置.**

  **7.建议不选择 启动win8metro界面.**

  **8.超时时间:可以随意,但前提是你能反应过来 :)**

  **9.其他无需设置,但是建议每个选项都改一改,亲自试验才是最扎实的学习方法.**

## 很多的操作系统启动问题都是BCD文件的配置错误导致的.若你的VM无法启动,请检查你的BCD文件配置!
