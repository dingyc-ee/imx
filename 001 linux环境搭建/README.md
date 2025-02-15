# linux环境搭建

## 安装软件

+ *open-vm-tool*

    `sudo apt install open-vm-tools-desktop`

    安装完成后重启虚拟机。

+ *换源*

    查看ubuntu版本：`lsb_release -a`

    ```sh
    ding@linux:~$ lsb_release -a
    No LSB modules are available.
    Distributor ID:	Ubuntu
    Description:	Ubuntu 18.04.6 LTS
    Release:	18.04
    Codename:	bionic
    ```

    + 阿里源

    ```sh
    deb https://mirrors.aliyun.com/ubuntu/ bionic main restricted universe multiverse
    deb-src https://mirrors.aliyun.com/ubuntu/ bionic main restricted universe multiverse

    deb https://mirrors.aliyun.com/ubuntu/ bionic-security main restricted universe multiverse
    deb-src https://mirrors.aliyun.com/ubuntu/ bionic-security main restricted universe multiverse

    deb https://mirrors.aliyun.com/ubuntu/ bionic-updates main restricted universe multiverse
    deb-src https://mirrors.aliyun.com/ubuntu/ bionic-updates main restricted universe multiverse

    # deb https://mirrors.aliyun.com/ubuntu/ bionic-proposed main restricted universe multiverse
    # deb-src https://mirrors.aliyun.com/ubuntu/ bionic-proposed main restricted universe multiverse

    deb https://mirrors.aliyun.com/ubuntu/ bionic-backports main restricted universe multiverse
    deb-src https://mirrors.aliyun.com/ubuntu/ bionic-backports main restricted universe multiverse
    ```

    + 中科大源
  
    ```sh
    # 默认注释了源码仓库，如有需要可自行取消注释
    deb https://mirrors.ustc.edu.cn/ubuntu/ bionic main restricted universe multiverse
    # deb-src https://mirrors.ustc.edu.cn/ubuntu/ bionic main restricted universe multiverse

    deb https://mirrors.ustc.edu.cn/ubuntu/ bionic-security main restricted universe multiverse
    # deb-src https://mirrors.ustc.edu.cn/ubuntu/ bionic-security main restricted universe multiverse

    deb https://mirrors.ustc.edu.cn/ubuntu/ bionic-updates main restricted universe multiverse
    # deb-src https://mirrors.ustc.edu.cn/ubuntu/ bionic-updates main restricted universe multiverse

    deb https://mirrors.ustc.edu.cn/ubuntu/ bionic-backports main restricted universe multiverse
    # deb-src https://mirrors.ustc.edu.cn/ubuntu/ bionic-backports main restricted universe multiverse

    # 预发布软件源，不建议启用
    # deb https://mirrors.ustc.edu.cn/ubuntu/ bionic-proposed main restricted universe multiverse
    # deb-src https://mirrors.ustc.edu.cn/ubuntu/ bionic-proposed main restricted universe multiverse
    ```

    换源流程：

    + `sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak`

    + `sudo gedit /etc/apt/sources.list`
   
    + 复制源文件

    + `sudo apt update`
   
    + `sudo apt upgrade -y`

+ *卸载系统残留*

    `sudo apt-get autoremove`  

+ *安装vscode*

    [参考链接](https://blog.csdn.net/ly869915532/article/details/136588163)

    ubuntu 18.04支持的最新的为`code_1.85.2-1705561292_amd64.deb` [安装包](./src/code_1.85.2-1705561292_amd64.deb)

    安装命令：`sudo dpkg -i code_1.85.2-1705561292_amd64.deb`

    禁止vscode一直提示版本更新：`运行菜单File中Preferences子菜单中选择Settings项，搜索update mode，将其设置为none。`

    关闭预览模式：打开设置，输入`enable preview`，选择关闭预览。

    支持USB U盘([参考链接](https://zhuanlan.zhihu.com/p/451966343))：`先关闭 vm，用文本编辑器打开 host vm 目录的 vmx 文件，将属性 usb.restrictions.defaultAllow 由 FALSE 修改为 TRUE，保存然后启动 vm 就正常了。`

## 更换壁纸

![壁纸](./src/El%20Capitan.jpg)
