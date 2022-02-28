# proj140-RV-firmware-for-net
使用RISC-V固件的内核网络部署和维护方案


### 项目描述

RISC-V架构未来将被运用在服务器和数据中心平台上，部署量大，远程维护功能成为重要的解决方案。而RISC-V的主板固件是独立于操作系统的运行环境，它除了启动操作系统内核，还要保持在后台运行，以提供操作系统需要的功能。

本次赛题要求使用网络协议实现RISC-V架构的远程维护原型解决方案。合理运用RISC-V的嵌入式生态，可以良好地实现保持在后台运行的主板固件，从而完成内核部署和维护的技术功能。

此功能完成后，可以提高内核开发的自动化程度，提高开发设备的利用率，免去手动安装和升级操作系统的苦恼，可用于内核开发的单元测试等场景。RISC-V的硬件透明性更强，从引导程序环境到操作系统内核都可以自己定制，合理发挥RISC-V的开放透明优点，实现此类功能，将有助于完善RISC-V平台全过程安全可控的需求和生态市场。

### 所属赛道

2022全国大学生操作系统比赛的“OS功能设计”赛道

### 参赛要求

* 以小组为单位参赛，最多三人一个小组，且小组成员是来自同一所高校的本科生（2022年春季学期或之后本科毕业的大一~大四的学生）
* 如学生参加了多个项目，参赛学生选择一个自己参加的项目参与评奖
* 请遵循“2022全国大学生操作系统比赛”的章程和技术方案要求

### 项目导师

蒋周奇（洛佳）

* github [https://github.com/luojia65](https://github.com/luojia65)
* email [luojia@hust.edu.cn](mailto:luojia@hust.edu.cn)

### 难度

较高

### 特征

* 使用RustSBI（或其它SBI实现）的RISC-V固件开发
* 网卡驱动和网络协议栈
* 内核分发和下载应用方案

### License

* GPL3

### 预期目标

#### 第一题：远程下载和部署内核

* 选择一块RISC-V开发板。编写或选用裸机的网络协议栈和网卡驱动，使其能在此开发板的M态收或发网络包。
* 选用合适的通讯协议，从文件服务器上下载内核文件。
* 部署下载好的内核到内存并启动此内核。
  本题要求至少能下载和启动rCore-Tutorial级别的简单内核。

#### （附加题）第二题：固件与内核共享网卡

* 使用DMA环接续的方式，让使用DMA Ethernet MAC的网络外设能同时处理内核和固件的网络包收发工作。
* 运用M态的时钟信号，让操作系统内核和固件同时运行在处理器中。编写或修改固件，让它收到ICMP EchoRequest（ping）的时候能返回EchoResponse包。
* 为固件赋予一个IP地址，让内核能ping通固件。
  为减少代码量，本题实现的网络通信功能可以仅有IPv6和UDP支持。

#### （附加题）第三题：固件的故障维护功能

* 当操作系统向SBI发送关机指令时，SBI接口规定，操作系统可以返回一个错误代码。处理此错误代码，并合理地向用户反馈出现的错误。
* 修改固件，使它启动时能以某种方式接受用户输入，从而切换到特殊的维护模式。
  本题仅要求维护模式能显示一些处理器和开发板的状态信息，并且具备退出维护模式的功能。

