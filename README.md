# raspberry-pi64-documents
在树莓派上安装 pi64 系统时所遇问题及解决方案

## wifi
参考这里：
https://wiki.debian.org/WiFi/HowToUse#wpa_supplicant

因为 pi64 上默认没有找到任何编辑软件，所以我上来添加 wifi 的方法如下：

```
sudo cp /etc/wpa_supplicant/wpa_supplicant.conf /etc/wpa_supplicant/wpa_supplicant.conf.bak
sudo cat /etc/wpa_supplicant/wpa_supplicant.conf > ~/wpa.conf
wpa_passphrase Moxian Moxian0712 >> ~/wpa.conf
sudo cp ~/wpa.conf /etc/wpa_supplicant/wpa_supplicant.conf
```

然后重启系统生效

## 必备软件

```
sudo apt update -y
sudo apt upgrade -y
sudo apt install vim git -y
```

## 为 Hadoop 设置本地 openssl 互信

```
ssh-keygen -t rsa -P '' -f ~/.ssh/id_rsa
cat ~/.ssh/id_rsa.pub >> ~/.ssh/authorized_keys
chmod 0600 ~/.ssh/authorized_keys
```

## 安装配置 jdk（Oracle）

```
sudo apt install openjdk-8-jdk -y
sudo ln -s /usr/lib/jvm/java-8-openjdk-arm64 /usr/lib/jvm/default-java
vim .bashrc
export JAVA_HOME=/usr/lib/jvm/default-java
```
