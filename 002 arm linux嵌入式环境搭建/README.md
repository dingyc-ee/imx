# arm linux嵌入式环境搭建

## 安装软件

+ *vim*

    `sudo apt-get install vim`

+ *ifconfig*

    `sudo apt-get install net-tools`

+ *FTP*

    ```sh
    sudo apt-get install vsftpd
    sudo vim /etc/vsftpd.conf
    local_enable=YES
    write_enable=YES
    sudo /etc/init.d/vsftpd restart
    ```

+ *SSH*

    `sudo apt-get install openssh-server`

+ *gcc*

    `sudo apt-get install gcc`

+ *nfs*

    `sudo apt-get install nfs-kernel-server rpcbind`
    配置nfs共享目录(假如共享的nfs目录为`/opt/imx6ull_rootfs`)
    1. 编辑配置文件：`sudo vim /etc/exports`
    2. 在配置文件中添加如下内容
    `/opt/imx6ull_rootfs *(rw,sync,no_root_squash,no_subtree_check)`
        这里的 * 表示允许所有网络地址访问该共享目录。参数说明如下：
        + rw：允许客户端对共享目录进行读写操作。
        + sync：数据同步写入内存和硬盘。
        + no_root_squash：客户端使用 root 用户访问时，不将其映射为匿名用户。
        + no_subtree_check：不检查子目录权限。
    3. 修改完 /etc/exports 文件后，需要重新加载配置使改动生效：`sudo exportfs -ra`
    4. 重启NFS服务：`sudo /etc/init.d/nfs-kernel-server restart`

+ *TFTP*

    1. 安装TFTP

    ```sh
    sudo apt-get install tftp-hpa tftpd-hpa xinetd
    ```

    2. TFTP 服务的配置文件为 /etc/default/tftpd-hpa，使用以下命令编辑该文件：`sudo vim /etc/default/tftpd-hpa`

    ```sh
    TFTP_USERNAME="tftp"
    TFTP_DIRECTORY="/srv/tftp"
    TFTP_ADDRESS=":69"
    TFTP_OPTIONS="-l -c -s"
    ```

    3. 创建并设置 TFTP 根目录权限

    ```sh
    sudo mkdir -p /srv/tftp
    sudo chmod -R 777 /srv/tftp
    ```

## arm linux编译需要的库

+ *64位系统编译32位，安装库*

    `sudo apt-get install lsb-core lib32stdc++6`

+ *uboot图形界面menuconfig，安装库*

    ```sh
    sudo apt-get install build-essential
    sudo apt-get install libncurses5-dev
    ```

+ *kernel编译需要lzop库*

    `sudo apt-get install lzop`

+ *触摸屏驱动tslib需要的库*

    ```sh
    sudo apt-get install autoconf
    sudo apt-get install automake 
    sudo apt-get install libtool
    ```

+ *openssl编译需要的库*

    ```sh
    sudo apt-get install bison
    sudo apt-get install flex
    ```
