# 使用微PE的ISO文件启动VM虚拟机

  **我们使用U盘启动PE系统的操作步骤繁琐复杂,涉及添加虚拟磁盘和磁盘脱机.现在,使用微PE的ISO光盘镜像文件即可直接启动VM虚拟机进入微PE.**

  **首先需要获得微PE的ISO镜像.**

**操作方法:**

    1.打开 微PE工具箱
    2.点击右下角的光盘图标,生成可启动的ISO.
    3.选择ISO的存储位置,自己喜欢的壁纸图片,包含DOS工具箱,不要选择 同时复制安装包,这很占空间.
    4.立即生成ISO

  **你将会得到微PE的ISO可启动镜像文件.**

![ac93516299de48405303270e86e73c65.png](https://i.miji.bid/2024/02/27/ac93516299de48405303270e86e73c65.png)

### 使用ISO启动虚拟机

  **其实这一步骤的操作就是为虚拟机添加一个虚拟光盘,选择ISO镜像文件的时候选择微pe的ISO就可以了.**

**操作方法:**

    1.编辑虚拟机设置->添加->CD/DVD驱动器,下一步
    2.选择 启动时连接,使用ISO映像文件,选择微pe的ISO文件.

  **微peISO添加成功.**

  **最好保证你的虚拟机只有一个虚拟光盘.因为若有多个,在启动界面可能不知道选择哪个.**

    1.启动虚拟机的启动模式选择 打开电源时进入固件
    2.选择包含CDROM Drive的选项,回车
    (若有多个CDROM,你可以依次尝试,或者根据添加虚拟光盘的顺序选择)

  **别忘了选择1024x768哦.**


