# arm linux嵌入式环境搭建

## 安装软件

+ *vim*

    `sudo apt install vim`

+ *ifconfig*

    `sudo apt install net-tools`

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

    `sudo apt install gcc`
