# Sunshine/Moonlight+ZerotierFix 实现校园网远程 PC 控制
硬件配置：HUAWEI MatePad 11 + 宏碁 Nitro AN515-45

网络环境：Campus network of Southeast University, Jiulonghu Campus.

### 1. Sunshine/Moonlight 串流配置

参考教程：https://www.bilibili.com/video/BV13i421U7zf/?spm_id_from=333.337.search-card.all.click&vd_source=39c18c601c931b21219fa4615b1bc24b

Sunshine官网：https://app.lizardbyte.dev/Sunshine/?lng=en#Download

![image](https://github.com/user-attachments/assets/1a2eb9b2-8f39-4c4a-a5a8-aa8d895c1188)

选择对应 windows 版本：

![image](https://github.com/user-attachments/assets/eae233ab-927d-41be-bd00-c4e402bf3bca)

安装均采用默认，安装完成后在状态栏右击 Sunshine 图标，Open Sunshine：

![image](https://github.com/user-attachments/assets/a1d81387-b802-48dd-89ba-bec9697b7cc3)

此时网页可能会报安全风险警告，高级-继续访问即可：

![230628a680c81b70fe42dc5b722291dc](https://github.com/user-attachments/assets/39c6400c-f2fa-4aa2-ad08-4024655f61ef)

进入 Welcome 页面，需要设置用户名和密码，确认后 Login 会跳转至 Sunshine 后台配置页面：

![b39c09a3f6d8b1cf42c0a4ce4c0fde2a](https://github.com/user-attachments/assets/585ab4b5-ad2f-482d-9b66-78813cfb6912)

根据刚刚设置的用户名和密码进行身份验证：

![3dc7149e56a8f972b7b5341dc88ee508](https://github.com/user-attachments/assets/fab2c59f-db81-4943-b72f-09de4fb83da4)

此时可以对 Sunshine 进行一些必要配置，在 Configuration 中将语言更改为简体中文，点击保存，等待其重启后在状态栏再次右击 Sunshine 图标，Restart 再 Open Sunshine，页面即变更为中文。

其他必要配置：Network-UPnP：启用； IP 地址族：IPv4+IPv6.

![image](https://github.com/user-attachments/assets/63776de5-ba98-47f0-b5df-1961b347b0a6)

点击保存-应用，Sunshine 会自动重启应用更改，此时 PC 端作为串流的发射端配置完成。

Moonlight官网：https://moonlight-stream.org/

![d04bfd3caab0adf750eb4ceb80f6751](https://github.com/user-attachments/assets/626183d3-a0d0-4caa-a6f7-6587dd00b6e9)

在 CLIENT DOWNLOADS 中下载安装 Android 版本：

![94e80426c85ffeb8309aa066cd3794f](https://github.com/user-attachments/assets/c2259e44-59ee-4dc1-8881-b127d7b7bd23)

注意！！首先测试平板和电脑在同一局域网下 Android 端是否可以搜索到 PC：

通过共享电脑 Wifi 在平板中进行连接：

![image](https://github.com/user-attachments/assets/cd24cd38-e367-45f7-afbd-9ce83ba43c8e)

在平板的 Moonlight 添加电脑 ip 地址（ 在 WLAN 属性中查看 IPv4 地址，校园网一般为 10. 开头），连接成功则局域网下的串流配置没问题。

### 2. ZerotierFix内网穿透

由于校园网可能会有内网隔离/保护问题，导致在共享电脑 Wifi 时能连接到电脑，但在连同一校园网 Wifi 时会被墙。

![image](https://github.com/user-attachments/assets/07ec234a-78b0-49ac-a1f1-c4534a79d16a)

这时候我们需要使用 Zerotier 创建虚拟局域网，即可像在同一局域网中访问 PC 进行串流。

注：如果不是使用校园网，几种可能的解决方案：https://www.bilibili.com/opus/500980726464030822

参考教程：https://zhuanlan.zhihu.com/p/585817694

进入 Zerotier 官网注册：https://www.zerotier.com/

创建虚拟局域网，记住 NETWORK ID：

![image](https://github.com/user-attachments/assets/c588669b-93b4-404e-9bb2-788094f14f99)

进入 Zerotier 官网下载 Windows 版本：www.zerotier.com/download/

![image](https://github.com/user-attachments/assets/5d235a8f-b980-4598-b87a-85f79dd8f10a)

同样安装均采用默认，安装完成后在状态栏右击 Zerotier 图标，选择 Join New Network，输入刚刚的虚拟局域网 NETWORK ID，点击 Join 加入网络。

回到官网后台界面，会出现一个未加入网络的设备ID信息，点击左侧小方框打勾，IP地址会自动生成，此时网络状态会变成 ONLINE，至此 PC 端设置完成。

![image](https://github.com/user-attachments/assets/dad07810-56b8-40c7-be99-07f44162c79f)

配置平板的 Zerotier，由于貌似只有 ios 的美区应用商店才可下载，安卓端找到一个支持的 ZerotierFix：https://github.com/kaaass/ZerotierFix/releases/tag/1.0.10

下载安装 app-release.apk 在右下角点击添加，输入之前的网络 ID ( 即前述 NETWORK ID )：

![abe7a55b597c185be6565d3afe239c1](https://github.com/user-attachments/assets/7a77640d-4cb9-4048-a49f-8c540ce0d9be)

同样回到官网后台界面，在出现的未加入网络的设备ID信息前打勾。

平板端重新开启连接，显示成功连接至 ... ( NETWORK ID )，则表明内网穿透完成，此时重新回到 Moonlight，已可识别到之前加入的电脑。


