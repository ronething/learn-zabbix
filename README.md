# 学习 zabbix4.0

⚠️ [中文文档地址](https://www.zabbix.com/documentation/4.0/zh/manual) 不过翻译滞后了，更新的比较慢 [英文文档地址](https://www.zabbix.com/documentation/4.0/manual)比较好点

## 简介

### [手册目录结构](https://www.zabbix.com/documentation/4.0/zh/manual/introduction/manual_structure)

### Zabbix 介绍

- Zabbix 是一个企业级分布式开源监控解决方案。

- Zabbix 软件能够监控众多网络参数和服务器的健康度、完整性。Zabbix 使用灵活的告警机制，允许用户为几乎任何事件配置基于邮件的告警。这样用户可以快速响应服务器问题。Zabbix 基于存储的数据提供出色的报表和数据可视化功能。

- Zabbix 支持主动轮询和被动捕获。所有的 Zabbix 报告、统计信息和配置参数都可以通过基于 Web 的前端页面进行访问。基于 Web 的前端页面确保您的网络状态和服务器健康状况等可以从任何地方访问。

### [Zabbix 功能](https://www.zabbix.com/documentation/4.0/zh/manual/introduction/features)

-   数据采集
-   灵活的阈值定义
-   高度可配置化的告警
-   实时图形
-   Web 监控功能
-   丰富的可视化选项
-   历史数据存储
-   配置简单
-   套用模板
-   网络发现
-   快捷的 Web 界面
-   Zabbix API
-   权限管理系统
-   权限管理系统
-   功能强大且易于扩展的 Zabbix Agent
-   二进制守护进程
-   适应更复杂的环境

### [Zabbix 概述](https://www.zabbix.com/documentation/4.0/zh/manual/introduction/overview)

> Zabbix 由几个主要的功能组件组成:

-   Server
-   数据库
-   Web 界面
-   Proxy
    -   Zabbix proxy 可以替 Zabbix server 收集性能和可用性数据。Zabbix proxy 是 Zabbix 环境部署的可选部分；然而，它对于单个 Zabbix server 负载的分担是非常有益的。
-   Agent
-   数据流(感觉类似于flow 有触发条件之类的)


### [Zabbix 4.0.0 新特征](https://www.zabbix.com/documentation/4.0/manual/introduction/whatsnew400)

-   改进的仪表板
-   添加了另一个默认仪表板，专注于显示Zabbix服务器性能：Zabbix服务器运行状况 默认情况下， 此仪表板仅与Zabbix管理员组共享。
-   立即检索指标 ⚠️ 检查新值时，不会更新配置缓存，因此这些值不会反映项目/发现规则配置的最新更改。因此，也无法检查刚刚创建的项目/规则的新值。
-   新的HTTP项类型
    -   引入了新的HTTP项类型，允许使用HTTP / HTTPS协议进行数据轮询。
-   新模板
    -   新模板可用于监控某些IBM，Dell，HP，Cisco UCS和Supermicro Aten硬件
-   Item prototypes can depend on regular items
-   Low-level discovery macros in item preprocessing
-   Substring extraction of low-level discovery macro value
-   触发级别的主机维护
-   使用webserver进行单点登录
-   更灵活的活动代理自动注册
-   支持MySQL 8.0
-   Elasticsearch的基于日期的索引设置
-   更安全的代理连接
-   可以更改问题严重性
-   处理问题
-   新的图形小部件
-   时间选择器重新设计
-   前端页面的Kiosk模式
-   紧凑的问题视图
-   监控→已删除触发器
    -   在监视 → 问题成为需要查看当前问题的首选部分时，已决定从“监视”菜单中删除“ 触发器”部分。
-   Inventory macro support in event tags
-   灵活地防止单位转换
    -   In the new version, any unit can be prevented from being converted by using a ! prefix, for example !B
        ```
        1024 !B -> 1024 B
        1024 B -> 1 KB
        61 !s -> 61 s
        61 s -> 1m 1s
        0 !uptime -> 0 uptime
        0 uptime -> 00:00:00
        0 !! -> 0 !
        0 ! -> 0
        ```
-   一个用户媒体中的多封电子邮件
-   Real-time export of events, values, trends
-   基于标签的权限
-   服务器代理通信的压缩
    -   压缩可降低带宽要求并提高数据传输速度。[Zlib](https://zlib.net/) library is required for compression support.
-   Improved database down messages
-   Use of "not" keyword
    
    ![](https://i.loli.net/2019/01/06/5c31941fd1171.png)
-   Items
    -   New items
    -   Updated items
    -   JMX monitoring
    -   External script argument wrapping
    -   Searching IPMI sensor by full name
-   触发器
    -   时间触发器由历史同步器处理
    -   Miscellaneous
-   前端
    -   必填字段标记
    -   键盘导航
    -   日期选择器重新设计
    -   颜色选择器重新设计
        
        颜色选择器经过重新设计，提供更大的颜色选择
    -   弹出窗口由叠加对话框替换
-   过滤
    -   通过标签过滤更灵活的问题
    -   主机列表
    -   物品清单
-   触发器配置列表中显示的触发值
-   Renamed operators
-   Renamed widgets, screen elements and reports
-   Multiple item support in plain text widget
-   事件状态颜色调整
-   “主机质量更新”表单中的更改
-   “用户媒体”表单中的更改
-   Twin boxes replaced with auto-select
-   改进的小部件配置
-   小部件中的图形视觉改进
-   前端顶部栏菜单改进
-   无障碍
-   高对比度主题
-   守护进程
-   API improvements
    
    From now on [user.checkAuthentication](https://www.zabbix.com/documentation/4.0/manual/api/reference/user/user.checkauthentication) method contains additional parameter “extend”.

## [定义](https://www.zabbix.com/documentation/4.0/manual/definitions)

-   主机（host）
    
    你想要监控的联网设备，有IP/DNS。

-   主机组（host group)
    
    主机的逻辑组；可能包含主机和模板。一个主机组里的主机和模板之间并没有任何直接的关联。通常在给不同用户组的主机分配权限时候使用主机组。

-   监控项（item）

    你想要接收的主机的特定数据，一个度量/指标数据。

-   值预处理（value preprocessing）

    转化/预处理接收到的指标数据 存入数据库之前。

-   触发器（trigger）

    一个被用于定义问题阈值和“评估”监控项接收到的数据的逻辑表达式。
    
    当接收到的数据高于阈值时，触发器从“OK”变成“Problem”状态。当接收到的数据低于阈值时，触发器保留/返回“OK”的状态。

-   事件（event）

    一次发生的需要注意的事情，例如触发器状态改变、发现/监控代理自动注册

-   事件标签（event tag）

    提前设置的事件标记可以被用于事件关联，权限细化设置等。

-   事件关联（event correlation）

    自动灵活的、精确的关联问题和解决方案

    比如说，你可以定义触发器A告警的异常可以由触发器B解决，触发器B可能采用完全不同的数据采集方式。

-   异常（problems）

    一个处在“异常”状态的触发器

-   异常更新（problem update）

    Zabbix提供的问题管理选项，例如添加评论、确认异常、改变问题级别或者手动关闭等。

-   动作（action）

    预先定义的应对事件的操作

    一个动作由操作(例如发出通知)和条件(什么时间进行操作)组成

-   升级（escalation）

    一个在动作内执行操作的自定义方式; 发送通知/执行远程命令的顺序安排。

-   媒介（media）
    
    发送告警通知的方式；传送途径

-   通知（notification）

    关于事件的信心，将通过选设定的媒介途径发送给用户。

-   远程命令（remote command）

    一个预定义好的，满足特定条件的情况下，可以在被监控主机上自动执行的命令。

-   模版（template）

    一组可以被应用到一个或多个主机上的实体（监控项，触发器，图形，聚合图形，应用，LLD，Web场景）的集合

    模版的应用使得主机上的监控任务部署快捷方便；也可以使监控任务的批量修改更加简单。模版是直接关联到每台单独的主机上。

-   应用（application）

    一组监控项组成的逻辑分组

-   Web场景（web scenario）

    检查网站可浏览性的一个或多个HTTP请求

-   前端（frontend)

    Zabbix提供的web界面

-   Zabbix API

    Zabbix API允许用户使用JSON RPC协议来创建、更新和获取Zabbix对象（如主机、监控项、图形和其他）信息或者执行任何其他的自定义的任务

-   Zabbix server

    Zabbix监控的核心程序，主要功能是与Zabbix proxies和Agents进行交互、触发器计算、发送告警通知；并将数据集中保存等

-   Zabbix agent

    部署在监控对象上的，能够主动监控本地资源和应用的程序

-   Zabbix proxy

    一个帮助Zabbix Server收集数据，分担Zabbix Server的负载的程序

-   加密（encryption）

    支持Zabbix组建之间的加密通讯(server, proxy, agent, zabbix_sender 和 zabbix_get 程序) 使用TLS（Transport Layer Security ）协议。

## [Zabbix processes](https://www.zabbix.com/documentation/4.0/manual/concepts)

### [Server](https://www.zabbix.com/documentation/4.0/manual/concepts/server)

