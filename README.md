# Sunshine/Moonlight+ZerotierFix 低延迟 Pad 远程串流 PC 主力机

Motivation：主力机游戏本携带困难，特别是教室上课没有电源很伤。由于宿舍-教室-工位均覆盖校园网环境，考虑将主力机固定在工位，通过内网串流的方式低延迟 Pad 访问，另外购置了 pxx 海外版 Matepad 磁吸键盘，小巧 ( 键盘保护壳一体 ) 且性价比高 ( 50r ) ，搭配逻辑 M240 几乎只相当于多带一本书。以下记录串流配置的详细过程，仅供参考。

硬件配置：HUAWEI MatePad 11 2021 + 宏碁 Nitro AN515-45

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

在平板的 Moonlight 添加电脑 ip 地址 ( 在 WLAN 属性中查看 IPv4 地址，校园网一般为 10. 开头 ) ，连接成功则局域网下的串流配置没问题。

### 2. ZerotierFix 内网穿透 ( 校园网环境强烈推荐跳过2.使用新方案3. ) 

由于校园网可能会有内网隔离/保护问题，导致在共享电脑 Wifi 时能连接到电脑，但在连同一校园网 Wifi 时会被墙。

![image](https://github.com/user-attachments/assets/07ec234a-78b0-49ac-a1f1-c4534a79d16a)

这时候我们需要使用 Zerotier 创建虚拟局域网，即可像在同一局域网中访问 PC 进行串流。

注：如果不是使用校园网，几种可能的解决方案：https://www.bilibili.com/opus/500980726464030822

推荐！参考教程：https://zhuanlan.zhihu.com/p/585817694

进入 Zerotier 官网注册：https://www.zerotier.com/

创建虚拟局域网，记住 NETWORK ID：

![image](https://github.com/user-attachments/assets/c588669b-93b4-404e-9bb2-788094f14f99)

进入 Zerotier 官网下载 Windows 版本：www.zerotier.com/download/

![image](https://github.com/user-attachments/assets/5d235a8f-b980-4598-b87a-85f79dd8f10a)

同样安装均采用默认，安装完成后在状态栏右击 Zerotier 图标，选择 Join New Network，输入刚刚的虚拟局域网 NETWORK ID，点击 Join 加入网络。

回到官网后台界面，会出现一个未加入网络的设备ID信息，点击左侧小方框打勾，IP地址会自动生成，此时网络状态会变成 ONLINE，至此 PC 端设置完成。

![image](https://github.com/user-attachments/assets/dad07810-56b8-40c7-be99-07f44162c79f)

注意！此时电脑的 ip 地址已发生改变，在状态栏右击 Zerotier 图标，查看 Managed Addresses 中的 ip 地址，这就是你的电脑在 Moonlight 中所需填入的公网 ip 地址。

![image](https://github.com/user-attachments/assets/d3bce89a-7b1d-42a1-bbc6-c44f47965a5d)

配置平板的 Zerotier，由于貌似只有 ios 的美区应用商店才可下载，安卓端找到一个支持的 ZerotierFix：https://github.com/kaaass/ZerotierFix/releases/tag/1.0.10

下载安装 app-release.apk 在右下角点击添加，输入之前的网络 ID ( 即前述 NETWORK ID )：

![abe7a55b597c185be6565d3afe239c1](https://github.com/user-attachments/assets/7a77640d-4cb9-4048-a49f-8c540ce0d9be)

同样回到官网后台界面，在出现的未加入网络的设备 ID 信息前打勾。

平板端重新开启连接，显示成功连接至 ... ( NETWORK ID )，则表明内网穿透完成，此时重新回到 Moonlight，添加刚刚记录的公网 ip 地址，即可识别到 PC 端。

![image](https://github.com/user-attachments/assets/cd73f7ed-9e3f-4124-8147-7498f15eb337)

### 3. [ 强烈推荐 ] 校园网 IPv6 串流

其实一开始使用的方案是 Moonlight+Zerotier 进行内网穿透，几乎适用于任何不同局域网下的串流。

不过由于使用的 IPv4 本身载荷过高，网络环境不稳定；且可能在较差网络环境下不得不经过 Zerotier 中转服务器转发，其帧率实在感人 ( 大概只能 1080p 15-35fps 浮动 ) 时不时发生丢包，最难受的还是鼠标延迟过高带来的卡顿和漂移。尝试锁帧更是白日做梦，直接断连。

此时开启 Moonlight 配置中的实时性能分析，主机处理延迟 ( PC 端 ) 平均 3-5ms、平均解码时长 3-4ms ( Pad 端 ) 都比较正常，平均网络延迟 10-25ms 也还能接受，那么到底是哪一步的问题呢。

首先 PC 端作为主力机，视频编码这一块不成问题；Pad 端的确可能带不动，毕竟是 2021 年的老款 Matepad 11，内核还是晓龙 865，但视频解码 3-4ms 看似也不错；最后是校园网的问题，免费套餐单用户限制带宽为 30Mbps，而 1080p 30fps 码率就可达到约 20Mbps，再考虑设备本身的其他带宽支出，30Mbps 就显得很紧张了。

针对上面的分析，研究了几种可能可行的方案：

1. 虽然我们无从知晓是否是因为网络环境太差而导致不得不走 Zerotier 的中转转发节点，但毕竟 Zerotier 的根服务器部署在国外，或许可以尝试使用其他的内网穿透方案代替，比如皎月连。

2. 使用校园网 vpn，可能可以直接建立内网连接，不再需要穿透 ( 不一定对暂未验证 ) 

3. [ 推荐 ] 使用 IPv6 直连

   通过查询各类资料得知，很多学校的校园网针对 IPv4 是插入网线即分配 IP，认证后方可上网，为了保护隐私常进行内网隔离；但 IPv6 一般不会隔离，而且有说法是可以不受校园网带宽限制 ( 目前教育网 IPv6 使用量远不及 IPv4 ) 甚至可以绕过校园网验证。同时，即使是相隔很远的教育网 IPv6 设备，互联速度也能跑满带宽极限，因此可以通过 IPv6 公网地址尝试直连：

首先，通过 [IPv6 测试工具](https://test-ipv6.com/) 测试设备是否已接入 IPv6。

[ 注意 ]：如果 Android 端使用了 Clash 记得关闭，这会影响你的 IPv6 接入，原因未知。

记录 PC 端的公网 IPv6 地址，在平板端添加设备，输入对应的 IPv6 地址，[ 注意 ]：IPv6 地址需要用 [] 括起来。

IPv6 校园网串流效果：宿舍 → 工位几乎无延迟 2K 90fps 丝滑无卡顿

![5a36a2ea47da0f015070d6e18fff119](https://github.com/user-attachments/assets/78d12930-5d0a-43e8-81f7-cfafb6173266)

注意此处的渲染帧数低于接受帧数，只需要把 Moonlight 端的配置：视频帧速调节更改为 有FPS限制的平衡 即可，实测 90 甚至 120 帧都无压力。

![2336267b9422823013c9b850d93dd5f](https://github.com/user-attachments/assets/dcae08af-b1a4-4707-8323-6d2a92392c65)


