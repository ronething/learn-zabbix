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



