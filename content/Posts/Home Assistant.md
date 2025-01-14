---
title: 
date: 2025-01-13 10:56
permalink: home-assistant
aliases: 
tags:
  - 场景/智能家居
---
> **在物联网（IoT）飞速发展的今天，你是不是也遇到过这样的场景——家中五花八门的智能设备，各自都需要依赖自己的 App 或云端才能完成控制？**  
>
> 米家的灯、涂鸦的窗帘电机、Aqara 的传感器……这些品牌林林总总，但往往无法彼此联动，用户也只能在不同的 App 间频繁切换。对于刚开始接触智能家居的人来说，这还算勉强能接受；可一旦设备数量多起来，或你想做更复杂的自动化场景，操作就变得繁琐凌乱。
>
> 在这样的背景下，**Home Assistant（HA）** 横空出世。它是一个开源、免费且可在本地部署的智能家居控制平台，目标是为家庭中所有智能设备提供一个“中央大脑”。不论是 Wi-Fi、Zigbee、Z-Wave 等协议，还是国内外各大品牌，Home Assistant 都能用“集成（Integration）”的形式汇聚到同一个界面里，用一套逻辑来统一调度、管理和控制。

Home Assistant 最早于 2013 年在 GitHub 上发布，经过十年左右的发展，已成为 GitHub 上 Star 数量最多的智能家居项目之一（可以说是没有之一）。它的开发者社区异常活跃，不但保持了一周或两周就更新一次的频率，而且又衍生出丰富的官方/社区插件和可选功能。这种**高度的模块化与可扩展性**，让很多极客玩家和技术团队视它为搭建“私有智能家居中枢”的不二之选。

如果我们将居家的所有智能设备比作乐队里的不同乐器，那么 Home Assistant 就是那位指挥家，通过精准的指挥和规则安排，协同所有“乐器”在恰当的时间演奏、变调或休止，从而奏出和谐美妙的“音乐”——也就是高效、舒适并贴合个人需求的家居环境。

## 为什么选择 Home Assistant(HA)？

1. **打破单一品牌束缚，实现跨制造商的产品集成：**  
    无论是米家、涂鸦、Aqara 还是飞利浦、博联等厂商的设备，Home Assistant 都可以将它们纳入同一个管理面板，避免你在多个手机 App 间来回切换。对用户来说，这才是真正的“互联互通”。
2. **掌握自己的数据，守护隐私：**  
    当智能家居数据只存储在本地时，你就不必再担心被不断推送的广告或数据外泄可能带来的隐患。Home Assistant 作为一个“私有化平台”，可以让你的数据与操作习惯牢牢掌控在自己手里，不必依赖任何第三方云端。
3. **高度灵活的自动化逻辑：**  
    不同品牌设备之间的联动，往往是最能体现智能化价值的部分。比如：
    - 回家时，窗帘自动打开、灯光调到柔和模式。
    - 检测到温度或湿度超标时，自动开启空调或除湿机。
    - 夜间模式下，某些场景触发自动地更柔和，不会吵醒家人。 
        这些之前需要多个平台或大量编程才能实现的细致情景，在 Home Assistant 里通过图形化配置或简单的 YAML 配置就能完成。
4. **社区生态与可扩展性 (社区活跃、功能扩展性强)：**  
    Home Assistant 的插件系统异常活跃，像 HACS（Home Assistant Community Store）为你提供了海量的第三方扩展和主题皮肤。你可以毫不费力地下载并安装这些扩展，为自己的智能家居系统赋予更多创意功能。
5. **界面好看、配置简单**(不是核心，但不会第一眼把小白用户吓住)
   经过层层迭代，HA 于 2019 年采用的 Lovelace UI 提供了现代化且可定制的仪表板界面，不再需要你从头编写大量代码；即便是零基础用户也能快速上手。

>HA 作为开源智能家居平台的典范，GitHub Star 数量最大的 Smart Home 项目，让它受欢迎三个点 
>- 开源且免费（你不必太担心恶意代码，不用为强大的功能支付费用）
>- 社区活跃（插件集成丰富）、文档清晰
>- 简单易用（相对于其它开源平台，不用过多的进行代码配置）、界面好看而不失简约（Project Grace based on  Lovelace UI）；

## 选择什么样的 HA？

HA 现在提供了 Home Assistant Operating System、Home Assistant Container、Home Assistant Core 和 Home Assistant Supervised [四种安装方式](https://www.home-assistant.io/installation/#advanced-installation-methods)：

![[HA types.png]]
1. Home Assistant 的起源和核心：Home Assistant Core
	- **背景：**
		- **诞生时间：** 2013 年。
		 - Home Assistant 起初是一个纯 Python 应用，设计为在本地运行的开源家庭自动化平台，用户可以通过配置 YAML 文件来管理和控制智能设备。
	-  **定位：** Home Assistant Core 是 Home Assistant 最原始的形态，专注于平台核心功能和集成能力。它是一种灵活但需要一定技术基础的安装方式。
	- **特性：**
		- **运行环境：** 直接在 Python 环境中运行（需 Python 3.10+）
	- **适用人群：** 开发者、高级用户或想完全控制系统环境的人。
	- **优点：**
		- 灵活，用户可以自由选择运行环境（如裸机、虚拟环境）。
		- 依赖最少，更新周期灵活。
	- **缺点：**
		- 无图形化管理界面（如备份、插件管理）。
		-  手动管理依赖和更新。
	- **类比：** 就像一个 DIY 工具箱，功能强大但需要用户自己组装。
2. Home Assistant Container 的出现：轻量化与灵活性
	- **背景：**
		- **诞生时间：** 随着 Docker 容器技术的普及，Home Assistant 项目团队推出了 Home Assistant Container 版本。
		- **动机：** 解决开发者和高级用户希望在容器化环境中运行 Home Assistant 的需求，同时与更复杂的 Home Assistant Supervised 区分开。
	- **特性：**
		- **运行环境：** 作为 Docker 容器运行。
	- **适用人群：** 熟悉 Docker 的用户。
	- **优点：**
		- 易于部署和移植。
		- 支持用户自定义容器环境，与其他容器化服务（如数据库、Node-RED）无缝协作。
		- 不依赖特定操作系统。
	- **缺点：**
		- 无 Home Assistant 的附加功能（如插件系统和备份）。
	- **类比：** 像一个轻便的旅行箱，可以随时搬到任何 Docker 支持的地方，但功能需要手动配置。
3. Home Assistant Supervised 的诞生：插件与管理集成
	- **背景：**
		- **诞生时间：** Home Assistant 项目逐步扩展功能时，为了解决用户对更全面的管理工具需求而推出。
		- **动机：** 将 Home Assistant Core 和其附加功能（如插件、备份、更新管理）集成到一起，同时允许用户保留操作系统的完全控制权。
		- **曾称为：** 早期版本叫 “Hass.io”。
	- **特性：**
		- **运行环境：** Docker + Supervisor 服务（允许在任意 Linux 系统上安装）。
	- **适用人群：** 想使用 Home Assistant 的附加功能但又希望保留操作系统控制权的用户。
	- **优点：**
		- 支持插件（如 MariaDB、Mosquitto MQTT）。
		- 图形化管理界面。
		- 自定义性较强，用户可选择自己的底层 Linux 系统。
	- **缺点：**
		- 需要手动维护底层 Linux 环境，且可能与更新的官方要求不兼容。
		- 安装稍复杂。
	- **类比：** 像定制版操作系统，你可以享受高级功能但仍需自己维护基础环境。
4. Home Assistant Operating System：一体化与开箱即用
	- **背景：**
		- **诞生时间：** Home Assistant 团队发现部分用户对操作系统和依赖的配置缺乏兴趣，推出了 Home Assistant OS 版本。
		- **动机：** 提供开箱即用的完整解决方案，将 Home Assistant 和底层操作系统整合为一个独立系统。
		- **曾称为：** HassOS。
	- **特性：**
		- **运行环境：** 定制的轻量化 Linux 操作系统（基于 Buildroot）。
	- **适用人群：** 普通用户或不熟悉 Linux 的用户。
	- **优点：**
		- 开箱即用，不需要额外配置操作系统或依赖。
		- 提供完整功能，包括插件、备份和图形化管理界面。
		- 自动更新操作系统和核心服务。
	- **缺点：**
		- 操作系统不可定制，用户无法安装其他非 Home Assistant 的应用。
	- **类比：** 像一台预装了所有应用的家电，用户只需通电即可使用。

**时间线总结与对比**:

| **安装方式**                      | 诞生时间 | 定位       | 适合用户         | 功能特点                          |
| ----------------------------- | ---- | -------- | ------------ | ----------------------------- |
| **Home Assistant Core**       | 2013 | 基础版本     | 开发者、高级用户     | 最灵活，最小化功能，依赖 Python 环境        |
| **Home Assistant Container**  | 随后   | 容器化轻量版本  | Docker 用户    | 灵活的容器化部署，功能不包括插件和图形化管理        |
| **Home Assistant Supervised** | 随后   | 高级用户综合版本 | 技术爱好者、定制需求用户 | 提供插件和图形化管理界面，但需要维护底层 Linux 系统 |
| **Home Assistant OS**         | 较晚   | 开箱即用完整版本 | 普通用户         | 开箱即用，提供完整功能但底层操作系统不可更改        |

**推荐选择：根据需求**

1. **我喜欢技术折腾，想最大化控制环境：** 选择：Home Assistant Core 或 Container。
2. **我想要完整功能，但也希望保留对 Linux 系统的控制：** 选择：Home Assistant Supervised。
3. **我只想简单地用起来，不想管底层细节：** 选择：Home Assistant OS。

作为普通玩家，选择 OS 就好了，不用太折腾底层，也会更加稳定、省心。

> 安装 **OS 级别** 的 Home Assistant（即 **Home Assistant OS**）意味着要完整安装一个专用操作系统。因此，只有像树莓派这种通过刷写 OS 镜像启动的方式，或者在虚拟机中部署，才能安装并运行 HA OS。
### Step 1. 安装 Home Assistant OS

虽然 Home Assistant 支持许多种方式去安装，但对于*身处国内网络环境*以及*不想深究 HA* 内部的开发及管理，可以直接选择冬瓜 HAOS。  

冬瓜 HAOS 是对官方的 HAOS 一个分支（fork），除了内置了常用的下载 *加速* 和预装了常用集成（Integrations）和 add-ons 外以及些许小工具，与官网毫无差别，特别适合没有良好网络环境的傻瓜用户。从烧录系统镜像到访问 HA 页面一般不会超过 20 分钟。  

详情请访问：[冬瓜 HAOS - Hassbian/瀚思彼岸](https://bbs.hassbian.com/thread-24065-1-1.html)。

*优势如下*：
- 支持国内网络环境
- 内置常用的下载加速
- 预装常用集成（Integrations）和 add-ons
- 附带小工具，操作更便捷
- 从烧录镜像到访问页面仅需 20 分钟

> 选择你的硬件平台（如树莓派 4b），然后选择对应的镜像（系统）进行下载。

*冬瓜 HAOS 下载指向链接*：
- **X86 电脑或虚拟机版本**  
  - [x86 原生版和虚拟机版](https://bbs.hassbian.com/thread-23791-1-1.html)  
  - [PVE 安装教程](https://bbs.hassbian.com/thread-24143-1-1.html)  
  - [群辉 Synology](https://bbs.hassbian.com/thread-24547-1-1.html)  
  - [爱快 iKuai](https://bbs.hassbian.com/thread-24483-1-1.html)  
  - [PC 电脑万能安装冬瓜 HAOS 大法（WINPE 安装法）](https://bbs.hassbian.com/thread-24779-1-1.html)  
- **Amlogic 系列版本**  
  - [X96max+ 系列【方案 S905X3】](https://bbs.hassbian.com/thread-21234-1-1.html)  
  - [魔百盒系列【方案 S905l3a】（cm311-1a, m401a, unt403a）*不再更新，请改用通用版*](https://bbs.hassbian.com/thread-22974-1-1.html)  
  - [魔百盒系列【方案 S905l3a 通用】](https://bbs.hassbian.com/thread-26264-1-1.html)  
  - [魔百盒系列【方案 S905l3 或 l3b 通用】](https://bbs.hassbian.com/thread-26320-1-1.html)  
  - [S905X3 通刷系列【方案 S905X3】](https://bbs.hassbian.com/thread-27255-1-1.html)  
- **树莓派系列版本**  
  - [树莓派 3 代、4 代、5 代](https://bbs.hassbian.com/thread-24197-1-1.html)  
- **Home Assistant**  
  - [Green](https://bbs.hassbian.com/thread-24374-1-1.html)  
- **斐讯系列版本**  
  - [斐讯 N1](https://bbs.hassbian.com/thread-24505-1-1.html)  
  - [斐讯 T1](https://bbs.hassbian.com/thread-24532-1-1.html)  
- **黑豹 X2（PantherX2）**  
  - [黑豹 X2](https://bbs.hassbian.com/thread-24373-1-1.html)  
- **X88pro20 系列**  
  - [X88pro20 系列](https://bbs.hassbian.com/thread-25593-1-1.html)  

### Step 2. 连接设备

当把 HA 系统镜像（软件）烧录（安装）到了你的设备之后，对于初学者来说，可以不用管 HA 的 IP 地址是什么。

当 HA 加载完毕，可以在浏览器输入 `homeassistant.local:8123` 访问 Home Assistant 页面「当然你可以通过移动端设备如手机 App 去帮你自动加入本地 HA 的服务器直接访问： [iOS](https://apps.apple.com/us/app/home-assistant/id1099568401) or [Android](https://play.google.com/store/apps/details?id=io.homeassistant.companion.android) 」。
### Step 3. 添加设备

HA 已经内置了 [3000 多个 Integrations(集成)](https://www.home-assistant.io/integrations/)，里面存在的厂商和协议，你都可以接入；
#### 添加小米家居设备

由于米家生态已经是国内智能家居的大头了，所以我们以添加一个米家设备作为开始。默认的小米集成只支持部分和有限的交互，所以我们最好是去安装一个小米组件：[官方](https://github.com/XiaoMi/ha_xiaomi_home)和[第三方](https://github.com/al-one/hass-xiaomi-miot)。

官方的插件采用了 MQTT 消息订阅的方式，而不是像第三方采用轮询去获取信息，所以官方的组件延迟会低很多，但是第三方 HA 组件发展比较久，有些功能用起来会更方便一些，比如现在（2025-01-14），只有第三方的组件才有小爱音箱的 STT 获取文本。也就是说如果你想用小爱同学去控制你的 DIY 设备或者其它设备，需要借助第三方组件去实现。

说了这么多，你完全可以下载两个组件，用官方组件管理传感器类型的，第三方组件来获取其它类型的设备信息。

## 基本概念 & 术语

对于 HA 的使用，我们需要了解一下 HA 应用中基本的概念，就像学习使用电脑那样知道什么是浏览器的菜单栏、链接等等概念。

HA 使用到的名词概念较多，但核心的有如下几个：[Concepts and terminology - Home Assistant](https://www.home-assistant.io/getting-started/concepts-terminology/)
Add-ons

### 1. 集成 (Integrations)
- Home Assistant 通过“集成”来支持各种品牌和协议的设备或云服务。  
- 常见集成如 Tuya、Aqara、Philips Hue 等，学员可以在“设置 → 设备与服务 → 添加集成”中直接搜索、安装。

### 2. 设备 (Devices)
- 指现实中的智能硬件（如一颗温湿度传感器、一台空调、一把智能门锁等）在 HA 中的映射。  
- 每个“设备”下面可能会包含多个可以独立控制或读取的“实体”。

### 3. 实体 (Entities)
- 更细化的逻辑对象，常见的实体类型包括“传感器 (sensor)”、“开关 (switch)”、“灯 (light)”等等。  
- 如果说“设备”是一个物理对象，那“实体”就是这个设备在 HA 系统中的各项可监测或可操作的子功能。

> 要发现对应的**设备**，必须要有对应的**集成**去管理、发现；对于实质的控制是针对于**实体**来的（但也由编写*集成*组件的人来定义）
### 4. 管理 (Organization)
[Grouping your assets - Home Assistant](https://www.home-assistant.io/docs/organizing)

- **区域 (Area)：** 按房间或区域将设备进行分组，如“客厅”“卧室”“厨房”等；  
- **楼层 (Floor)：** 当房屋有多层时，可以用此来对“区域”做更上层的划分；  
- **标签 (Labels)：** 用于快速检索或给设备/实体打上自定义标签，便于分类管理。

### 5.  加载项、插件 (Add-ons)

在 Home Assistant 中，**Add-ons** 是基于 Supervisor（的一种特殊功能拓展机制，主要用来为 Home Assistant 补充一些辅助服务或工具，而不必在系统外独立部署。常见的 Add-ons 包括：

- **Advanced SSH & Web Terminal** 对于 OS，利用此插件可以方便的进行终端交互，访问 Editor 无法进行的层面；  
- **File Editor** 则给初学者带来最直观的配置文件编辑体验，主要用于基本的配置文件的 YAML 配置文件编辑。
- **Node-RED** 用可视化编程提升自动化复杂度与可玩性；  
- **ESPHome Device Builder** 是 DIY 与硬件改造爱好者的得力助手；  
- **EMQX** 替换官方的 MQTT Broker，便于更加清晰的管理；  
### 6. [自动化 (Automations)](https://www.home-assistant.io/docs/automation)

#### 6.1 基本的自动化 (Basic automations)
- **触发器（Triggers）：** 事件（开关变化、时间调度、传感器数值超限等）  
- **条件（Conditions）：** 对触发条件作出进一步判断（如“只在晚上进行”或“只有在温度高于 30℃ 时执行”）  
- **动作（Actions）：** 要让系统执行的操作，比如“打开灯”、“发送通知”、“切换场景”等。

> 例如：当玄关门锁打开时，若时间在晚上 7 点后，则自动亮起客厅主灯，并播放背景音乐。自动化的“触发—条件—动作”三步曲。

#### 6.2 场景 (Scenes)

在设置场景的时候, 可以以当前你的环境状态作为一个模板，比如，你在看书，那么可以复制当前的家庭情况为“看书”。

- 一次性设置多个设备的目标状态，比如“回家场景”中灯光亮度、窗帘打开程度、音响音量等，全部只需一键切换。  
- 适合营造不同氛围或处理多设备联动，操作起来更省心。

> 场景是一个模板，当进入这个模板，就会按照这个模板去规划所有设备的行为。
#### 6.3 脚本 (Scripts)
- 类似一段可重复调用的“动作集合”，可与自动化逻辑或场景结合使用，减少重复配置。  
- 也可以在脚本内添加延时、条件等，构建更灵活的操作流程。

> 脚本只是执行器，没有任何的条件判断。

## More to Read

- [正是入坑好时节：在米家官方支持之际，再聊新人 Home Assistant 入门](https://sspai.com/post/95117)
- https://smartyhome.io/introduction-to-home-assistant/
- [Home Assistant Tutorial: A Beginner’s Guide to Automation](https://www.influxdata.com/blog/home-assistant-tutorial-beginners-guide-automation-influxdb/) - 主要是介绍了基本的概念和术语
- [Introduction to Home Assistant](https://smartyhome.io/introduction-to-home-assistant/) - 17 年的文章，但值得翻阅一遍
- [Perfect Home Automation](https://www.home-assistant.io/blog/2016/01/19/perfect-home-automation/)
## Reference

- https://www.home-assistant.io/
- [hassbian](https://bbs.hassbian.com/forum-75-1.html)
