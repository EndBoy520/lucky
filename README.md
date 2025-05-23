# Lucky(万吉)
 

 ## 注意：源码公布到1.4.10版本，后续暂无继续开源计划。

 ## 麻烦各位大佬发表lucky相关教程的时候不要加上“开源”神器，开源二字我不配，lucky后续也没开源打算。
        1.开源并不等于安全，闭源并不等于不安全。闭源软件开发也会受到安全人员的审查。无论是开源还是闭源软件，都有可能会受到各种安全人员的审查和研究。安全人员可以使用各种技术手段来检测软件的安全性和漏洞。
        2. 个人观点lucky这种应用类软件更多只是体力活，毫无技术含量，开源的优势在于透明度和社区参与，更多劳动力参与，但也可能导致功能过多、复杂度增加的问题。闭源软件的优势在于我想怎么写就怎么写,即使还未能从lucky中获利，lucky对我也有更深的特殊含义。
        3. 我对lucky的规划还有一大部分未实现，不想被人当免费劳动力使唤，不解释太多，就这样。

 
 ## 如果您是第一次使用Lucky，请务必先访问 https://lucky666.cn ，并仔细阅读相关的文档，以获得必要的信息和答案。在这些文档中，您可以了解到Lucky的基本功能和特性，掌握Lucky的使用方法，以及解决常见的问题和疑惑。
 

<!-- TOC -->
- [Lucky(万吉)](#)
  - [特性](#特性)
  - [一键安装](#一键安装)
  - [OpenwrtIPK包安装](#OpenwrtIPK包安装)
  - [使用](#使用)
  - [Docker中使用](#docker中使用)
  - [后台界面](#后台界面)

  - [开发编译](#开发编译)
  - [更新日志](#更新日志)
  - [使用注意与常见问题](#使用注意与常见问题)

<!-- /TOC -->


## 特性

Lucky最初是作为一个小工具，由开发者为自己的个人使用而开发，用于替代socat，在小米路由AX6000官方系统上实现公网IPv6转内网IPv4的功能。Lucky的设计始终致力于让更多的Linux嵌入式设备运行，以实现或集成个人用户常用功能，降低用户的硬件和软件操作学习成本，同时引导使用者注意网络安全。随着版本更新和网友反馈，Lucky不断迭代改进，拥有更多功能和更好的性能，成为用户值得信赖的工具。

Lucky 的核心程序完全采用 Golang 实现，具有高效、稳定、跨平台等优点。其后台前端则采用 Vue3.2 技术进行开发，具有良好的用户体验和响应速度。此外，Lucky 的管理后台采用前后端分离的架构，第三方开发者也可以自由使用OpenToken轻松调用Lucky的各种功能接口。



## 功能模块

目前已经实现/集成的主要功能模块有
  - 端口转发
  - 动态域名(DDNS)
  - Web服务
  - Stun内网穿透
  - 网络唤醒
  - 计划任务
  - ACME自动证书
  - 网络存储



### 端口转发
  1. 主要用于实现公网 IPv6 转内网 IPv4 的 TCP/UDP 端口转发。
  2. 支持界面化的管理转发规则，用户可以通过 web 后台轻松地进行规则的添加、删除、修改等操作。
  3. 单条转发规则支持设置多个转发端口，这样可以实现多个内网服务端口的转发。
  4. 提供了一键开关和定时开关功能，用户可以根据自己的需求设置转发规则的开启和关闭时间，还可以使用计划任务模块进行定时开关。
  5. 单条规则支持黑白名单安全模式切换，用户可以根据需要选择使用白名单模式或黑名单模式。
  6. 白名单模式可以让没有安全验证的内网服务端口稍微安全一点暴露到公网，提高服务可用性。
  7. 实时记录最新的访问日志，方便用户了解转发情况。
  8. 规则列表日志一目了然，用户可以方便地追踪转发异常，及时进行排查和处理。



### 动态域名(DDNS)
  1. 支持接入多个不同的 DNS 服务商。
  2. 支持全功能自定义回调（Callback），包括设置 BasicAuth，方便接入任意 DNS 服务商。
  3. Webhook 支持自定义 headers。
  4. 内置常用免费 DNS 服务商设置模板（每步、No-IP、Dynv6、Dynu），通过自定义回调进行快速接入，仅需修改相应用户密码或 token 即可一键填充。
  5. 支持 阿里云，百度云，华为云，京东云，腾讯云，火山引擎，帝恩爱斯-DNS.LA,Cloudflare，deSEC,DNSPod.CN，DNSPod.COM，Dynadot，Dynv6，Freemyip ,GoDaddy，Name.com，NameSilo,Porkbun，Vercel等服务商。


### Web服务
  1. 支持反向代理、重定向和 URL 跳转。
  2. 支持 HTTP 基本认证。
  3. 支持 IP 黑白名单模式。
  4. 支持 UserAgent 黑白名单。
  5. 规则日志清晰易懂，便于追踪异常。
  6. 支持一键开关规则和定时开关规则。


### Stun内网穿透
  1. 实现内网穿透，无需公网IPv4地址。
  2. 适合于国内运营商级NAT1宽带网络. 

### 网络唤醒
  1. 支持远程控制唤醒和关机操作
  2. 支持接入第三方物联网平台(点灯科技 巴法云),可通过各大平台的语音助手控制设备唤醒和关机.

### 计划任务
  1. 不依赖 Linux 系统的 Cron，支持 Windows 系统。
  2. 操作简便，可视化编辑。
  3. 可操作控制 Lucky 框架内的其他模块开关。

###  ACME自动证书
  1. 支持 ACME 自动证书的申请和续签。
  2. 支持 阿里云，百度云，华为云，京东云，腾讯云，火山引擎，帝恩爱斯-DNS.LA,Cloudflare，deSEC,DNSPod.CN，DNSPod.COM，Dynadot，Dynv6，Freemyip ,GoDaddy，Name.com，NameSilo,Porkbun，Vercel等服务商.


### 网络存储
  1. 网络存储模块是一个应用范围广泛的模块，它提供了将本地存储、WebDAV和阿里云盘挂载到Lucky内部的各个文件类服务功能。
  2. 通过网络存储模块，你可以将添加的存储挂载到Web服务的文件服务、WebDAV、FTP和FileBrowser模块，实现更加便捷的文件管理和访问。





## 一键安装

- [一键安装详看这里](https://github.com/gdy666/lucky-files)


## OpenwrtIPK包安装

- [Openwrt IPK包](https://github.com/gdy666/luci-app-lucky)


## 使用
    

- 默认后台管理地址 http://<运行设备IP>:16601
  默认登录账号: 666
  默认登录密码: 666

- 常规使用请用 -cd <配置文件夹路径> 指定配置文件夹的方式运行 
    ```bash
    #仅指定配置文件夹路径(如果配置文件夹不存在会自动创建),建议使用绝对路径
    lucky -cd luckyconf

    ```




## Docker中使用

- 不挂载主机目录, 删除容器同时会删除配置

  ```bash
  # host模式, 同时支持IPv4/IPv6, Liunx系统推荐
  docker run -d --name lucky --restart=always --net=host gdy666/lucky
  # 桥接模式, 只支持IPv4, Mac/Windows推荐,windows 不推荐使用docker版本
  docker run -d --name lucky --restart=always -p 16601:16601 gdy666/lucky
  ```

- 在浏览器中打开`http://主机IP:16601`，修改你的配置，成功
- [可选] 挂载主机目录, 删除容器后配置不会丢失。可替换 `/root/luckyconf` 为主机目录, 配置文件夹为lucky

  ```bash
  docker run -d --name lucky --restart=always --net=host -v /root/luckyconf:/goodluck gdy666/lucky
  ```


## 宝塔Docker安装

1.  安装宝塔面板 (9.2.0版本及以上)，前往 [宝塔面板](https://www.bt.cn/new/download.html) 官网，选择正式版的脚本下载安装
2.  安装后登录宝塔面板，在菜单栏中点击 Docker ，首次进入会提示安装 Docker 服务，点击立即安装，按提示完成安装
3.  安装完成后在应用商店中找到 lucky ，点击安装，配置基本选项 即可完成安装









## 后台界面
![规则设置](./previews/relayruleset.png)
![规则列表](./previews/relayrules.png)
![](./previews/whitelistset.png)
![](./previews/whitelist.png)
#### 动态域名服务

![](./previews/ddnslist.png)


![](./previews/iphistroy.png)

![](./previews/webhookhistroy.png)

![](./previews/domainsync.png)

#### Http反向代理
![](./previews/reverseproxy.png)

#### 网络唤醒

![](./previews/wol001.png)

![](./previews/wol002.png)




#开发编译


    ```bash
    go build -v -tags "adminweb nomsgpack" -ldflags="-s -w"
    ```


# 更新日志

    2025-03-24 v2.15.8 
    1.网络唤醒
        优化: 快捷控制页面，新增设备列表信息的实时刷新机制。
        修复: 无法通过反向代理访问快捷控制页面的问题。
    2.端口转发
        修复: 由于自身转发检测不可避免的小概率误报，解决导致转发中断的已知问题。
        新增: 禁用自身转发检测开关（若确保未误用 Lucky 端口转发，可开启此选项以提升转发性能以及避免上述误报现象）。
    3.Coraza
        更新: 内置 OWASP 核心规则集v4.12.0
    4.全局变量
        新增  {DNS_记录类型_记录名} 格式查询 DNS 记录，若存在多个记录，则随机返回一条，例如 {DNS_A_lucky666.cn} 
    5.FileBrowser
        同步： 最新源码
    6.SSL 证书
        新增: 多 Lucky 证书同步功能（暂未开放）
    7.Web 服务
        修复: 跨域支持异常的问题
    8.STUN
        优化UPnP提升对光猫环境的兼容性
    9.IP 过滤
        新增：自动记录 IP 接口 支持 netmask 子网掩码参数（可选），支持网段录入。
    10.其他优化
        自定义可访问内网网段
        通过  配置目录下的 localips 文件 记录，每行一条记录，支持 **单 IP 或网段格式**。
        localips 文件不为空时，默认内置网段将失效。

    2025-02-17 v2.15.7
      1. 端口转发
        进一步优化防止端口转发至自身的机制，避免因错误配置导致循环转发问题。
      2. DDNS
        尝试修复 Cloudflare 接口解析域名时出错的问题。
        优化任务添加/修改检测，禁止添加空域名，并防止将自身域名添加到自定义多级域名后缀列表。
      3. STUN
        更新默认内置 STUN 服务器列表
      4. SSL 证书
        改进非直接公网环境下的 IP 证书匹配处理逻辑。
      5. Web 服务
        新增{ECH} 变量支持，便于查询访问是否通过 ECH（加密客户端你好）方式。
        连接管理底层架构重构，优化性能，提高连接管理效率。
        关闭子规则时，将自动关闭所有相关连接。
        修复 User-Agent 默认过滤未正确处理空字符串的问题。
      6. 其他
        修复已知 bug，提升系统稳定性。

    2024-12-01 v2.14.0
      1. 网络唤醒
          修复了一个 bug，该 bug 导致在服务端手动添加设备记录时，客户端首次使用时连接失败。
      2. IP地址库
          新增对纯真新版地址库（czdb 格式）的支持。请自行通过纯真官网获取。
      3. 点灯物联
          优化核心代码，修复小爱同学语音控制回复异常的问题。
      4. DDNS
        4.1 腾讯云接口不再限制最小 TTL 为 600。
        4.2 修复了 Dynadot 更新主域名失败的问题。
      5. SSL
        ACME 证书 同一组域名可同时使用 Let's Encrypt、ZeroSSL 和 FreeSSL 等多个机构颁发的证书，Lucky 将自动调用有效期最长的证书。
      6. 计划任务 点灯组件绑定数量限制放宽到10个
      7. 增加隐私防护策略，防止fofa根据固定图标hash值搜索出lucky后台
      8. 增加安全入口设置检查和默认账号密码检查机制，不通过检查无法使用每个功能模块，可在设置页面禁用检查。登陆连续错误最大次数减少到30次 从2.14.0版本开始，在默认配置中，外网访问开关处于关闭状态。然而，在 lucky_base.lkcf 配置初始化后的十分钟内，系统允许外网访问。如果在这十分钟内执行了配置保存操作，则外网访问开关的设置将优先生效。如果错过了这个时间，您需要通过删除 lucky_base.lkcf 配置文件并重启 Lucky 进程的方式，使 lucky_base.lkcf 配置再次初始化。 如果未设置安全入口或未修改默认账号密码，将无法使用所有功能模块。如果您了解相关风险并确实不想进行设置，请在设置面板中启用禁用安全入口设置检查和禁用默认账号密码检查开关（此两个选项会闪烁提示）。
      9. 其他优化
  

   [更多日志请查看](https://lucky666.cn/docs/category/%E6%9B%B4%E6%96%B0%E6%97%A5%E5%BF%97)

















。



