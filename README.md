## FofaMap云查询版 | [FofaMap国庆特别版](https://github.com/asaotomo/FofaMap)

<p align="center">
<a href="https://opensource.org/licenses/MIT"><img src="https://img.shields.io/badge/license-MIT-_red.svg"></a>
<a href="https://github.com/asaotomo/fofamap/issues"><img src="https://img.shields.io/badge/contributions-welcome-brightgreen.svg?style=flat"></a>
<a href="https://github.com/sqlmapproject/sqlmap/actions/workflows/tests.yml"><img src="https://img.shields.io/badge/python-3.x-blue.svg"></a>
</p>

### 0x00 工具简介

FofaMap云查询版是基于C/S架构打造的Fofa数据采集器，仅需配置好一个服务端，即可实现多个客户端同时在线查询，其客户端支持FofaMap国庆版全部功能。

### 0x01 服务端

服务端基于Python3的Flask框架构建，可将其部署在vps上，提供fofa api在线查询功能。

```plain
# 使用说明
1.工具使用Python3开发，请确保您的电脑上已经安装了Python3环境。
2.首次使用请在server目录下打开终端，并使用 python3 -m pip install -r requirements.txt 命令，来安装服务端必要的外部依赖。

服务器端启动命令：
python3 fofamap-server.py

在后台启动fofamap-server：
# 创建一个 screen 终端，fofamap-server
screen -S fofamap-server
# 在这个终端上运行服务端
python3 fofamap-server.py
# 显示已创建的screen终端 
screen -ls  
# 恢复到fofamap-server终端
screen -r fofamap-server
```

![img](https://cdn.nlark.com/yuque/0/2022/png/12839102/1644202822251-419c4cef-1819-4260-b6ff-689ccb779c5f.png)

**服务端配置文件说明：**

```plain
[userinfo]
#注册和登录时填写的email
email = xxxxxxx@qq.com
#会员到个人资料可得到key，为32位的hash值
key = xxxxxxxxxxxxxxxxxxxxxxxxx

[CouldServer]
#fofamap服务端与客户端交互的通信口令，默认为fofamap@2022，为了安全起见建议修改后使用。
key = fofamap@2022
#服务器监听地址，默认为0.0.0.0。
ip = 0.0.0.0
#服务器监听端口，默认为15800。
port = 15800
```

### 0x02 客户端

客户端能够向服务端发送查询语句，获取查询内容，并将其美化输出。提供fofamap国庆版全部功能，仅需配置服务器IP地址和通信口令即可使用。

```plain
使用说明
1.工具使用Python3开发，请确保您的电脑上已经安装了Python3环境。
2.首次使用请在client目录下打开终端，并使用 python3 -m pip install -r requirements.txt 命令，来安装客户端必要的外部依赖。

客户端查询示例：
python3 fofamap.py -q 'ip="8.8.8.8"'

```

![img](https://cdn.nlark.com/yuque/0/2022/png/12839102/1644202838077-3415f8b7-9278-49a7-b1a5-b7ab98fe246f.png)

fofamap具体使用方法请参考：[使用手册](https://github.com/asaotomo/FofaMap/blob/1.1.1/README.md)


**客户端配置文件说明：**

```plain
[CouldServer]
#服务端地址,请将其修改为你的服务端地址
ip = 127.0.0.1
#服务端端口，默认为15800。
port = 15800
#fofamap服务端与客户端交互的通信口令，默认为fofamap@2022，为了安全起见建议修改后使用。
key = fofamap@2022

[size]
#每页查询数量，默认为100条，最大支持10,000条/页
size = 100

[full]
#默认搜索一年内的数据，指定为true即可搜索全部数据，false为一年内数据
full = false

[fields]
#查询内容选项
fields = host,ip,port,protocol,title,domain,country,city,lastupdatetime
#fields可选项：['host', 'title', 'ip', 'domain', 'port', 'country', 'province', 'city', 'country_name', 'header', 'server',
#           'protocol', 'banner', 'cert', 'isp', 'as_number', 'as_organization', 'latitude', 'longitude', 'structinfo',
#           'icp', 'fid', 'cname']

[page]
#查询启始页数，page最小为1
start_page = 1
#查询结束页数
end_page = 2

[logger]
#全局日志开关，开启后会默认输入软件执行日志到fofamap.log文件
logger = on

#不同用户使用fofamap调用fofa api接口查询次数如下：
#企业会员 免费前100,000条/次
#高级会员 免费前10000条/次
#普通会员 免费前100条/次
#注册用户 1F币（最多10,000条）/次
```

------

**本工具仅提供给安全测试人员进行安全自查使用** **用户滥用造成的一切后果与作者无关** **使用者请务必遵守当地法律** **本程序不得用于商业用途，仅限学习交流**

------

**FofaMap云查询版由Hx0战队开发维护**

<img width="318" alt="image" src="https://cdn.nlark.com/yuque/0/2022/png/12839102/1644203339831-1825b745-a60c-4d5e-a404-c4f3619b5ba4.png">

**【知识星球】福利大放送**

<img width="318" alt="image" src="https://user-images.githubusercontent.com/67818638/156556995-f3798cb1-027e-47e6-84ba-b7537d85b158.png">

---

**更新日志 V1.1.3 FofaMap云查询版**

[+] 增加nuclie扫描指定单一扫描模板（templates）的功能。

[+] 增加全局日志功能，用户可自行选择是否开启日志。

[+] 增加Host聚合查询模式，可以根据当前的查询内容，生成聚合信息。

[+] 增加批量Host聚合查询模式，可以批量查询Host聚合信息。

[+] 新增每页查询数量和数据查询范围设置功能，用户可以根据自己的需求选择每页查询的数据数量以及数据查询的范围（1年内 or 全部数据）。

[+] 优化Host聚合查询模式中端口详情的显示格式和内容。

[+] 优化网站图标查询逻辑，增加网站图标识别成功率。

[+] 修复使用-s命令时，输出内容包含非http协议的问题

[+] 优化聚合搜索内容，修复部分搜索结果报错的问题。

[+] 增加统计聚合功能，可根据当前的查询内容，生成全球统计信息，当前可统计每个字段的前5排名。

**更新日志 V1.1.2 FofaMap云查询版**

[+] 增加网站图标查询功能，该功能仅支持高级会员及以上用户使用。

[+] 增加查询结果自动去重功能。

[+] 增加备案查询结果自动去重功能。

[+] 修复当查询字段（fields）只有一个时报错的bug。

[+] 新增异常捕获，当fofa语法输入错误时程序不退出。

