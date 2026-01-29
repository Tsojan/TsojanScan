# TsojanScan
一个集成的BurpSuite漏洞探测插件

## First
  本着市面上各大漏洞探测插件的功能比较单一，因此与[TsojanSecTeam](https://github.com/Tsojan)成员决定在已有框架的基础上修改并增加常用的漏洞探测POC，它会以最少的数据包请求来准确检测各漏洞存在与否，你只需要这一个足矣。


### Usage
#### 1、加载插件
<img src="https://user-images.githubusercontent.com/48227194/208301053-4d7e0e15-aab5-4888-b77a-b295593c23c5.png" width="85%" height="85%"/>
</br>

#### 2、功能介绍
#### （1）面板
<img src="https://user-images.githubusercontent.com/48227194/208301144-5f383e49-f205-4c6f-8a49-9d43e93be417.png" width="40%" height="40%"/>
</br>
自定义黑名单，插件不扫描黑名单的url列表，进行Reg匹配优先级第一。
</br>
<img src="https://user-images.githubusercontent.com/48227194/208301777-9b2cfbd9-32b6-4d49-8bfa-ac656f6c11e3.png" width="40%" height="40%"/>
</br>

#### （2）主动探测
<img src="https://user-images.githubusercontent.com/48227194/208303314-18d5a4f1-d132-48bf-8b08-d6e3c456a9c1.png" width="80%" height="80%"/>
</br>

比如探测非根目录/，目录下面需要加/
</br>
<img src="https://user-images.githubusercontent.com/48227194/208301191-c8f25270-e759-40b3-8dde-79416d9968d9.png" width="80%" height="80%"/>

#### 3、fastjson >=1.2.80探测
#### （1）本地环境
<img src="https://user-images.githubusercontent.com/48227194/208301213-5f69c155-55c8-4ea0-a71c-5be220d77624.png" width="80%" height="80%"/>

#### （2）预查询DNSlog接口
<img src="https://user-images.githubusercontent.com/48227194/208301223-d3fe3c7a-7d5a-43fe-badf-7b790b1fe042.png" width="80%" height="80%"/>
<img src="https://user-images.githubusercontent.com/48227194/208301234-9ecee57e-99f2-429e-bc72-e3755e031a22.png" width="80%" height="80%"/>

#### （3）扫描
<img src="https://user-images.githubusercontent.com/48227194/208301251-42f96fad-7843-4b14-a4ab-d25582997a80.png" width="80%" height="80%"/>

#### （4）判断准确版本
1.2.80版本探测如果收到了两个dns请求，则证明使用了1.2.83版本，如果收到了一个 dns 请求，则证明使用了1.2.80版本。
</br>
<img src="https://user-images.githubusercontent.com/48227194/208301276-9236ec7b-35eb-41df-b638-05691dea17b6.png" width="80%" height="80%"/>
<img src="https://user-images.githubusercontent.com/48227194/208301279-5bf185c5-63da-4f05-9753-865c14ffa0d0.png" width="80%" height="80%"/>
</br>

#### 4、DNSLog查询漏报
<img src="https://user-images.githubusercontent.com/48227194/208301292-e9b68adb-8f36-44bf-bb3d-d0988377bad7.png" width="80%" height="80%"/>
<img src="https://user-images.githubusercontent.com/48227194/208301296-6fb56dd9-c822-4d81-b3ef-71d85ae6f1c0.png" width="80%" height="80%"/>
<img src="https://user-images.githubusercontent.com/48227194/208301300-7d09985a-e69d-4d19-8022-e2179061632b.png" width="80%" height="80%"/>

<img src="https://user-images.githubusercontent.com/48227194/208301308-3a2eab8a-c022-4a45-a0f9-20a5240e7ab2.png" width="80%" height="80%"/>

注意⚠️：扫描结束后才会在BurpSuite的Target、Dashboard模块显示高危漏洞，进程扫描中无法进行同步，但可以在插件中查看（涉及到DoPassive方法问题）。

<img src="https://user-images.githubusercontent.com/48227194/208301319-4371383e-122c-4608-8dd2-781bfe6905f6.png" width="80%" height="80%"/>
</br>

### Update

#### 更新说明 - v2.0.0-Beta2

- 新增vulPanel表格添加右键选项，可以删除，清理所有数据并导出数据为csv和html
- 新增几个DNSlog服务商（Eyes,requestrepo,DigPM，当前默认Eyes，推荐优先使用Eyes
- 修复fastjson主动和被动扫描不工作
- 修复上一个beta版本扫描带有X-Tsojan-Scanner: true请求头指纹
- 继续优化相关漏洞检测逻辑。

#### 更新说明 - v2.0.0-Beta1

- 重构 TsojanScan 插件框架代码 适配2026年 BurpSuite 新版 MontoyaApi api；
- 重构 TsojanScan 模块框架，优化 UI 框架；
- 新增 Scanning Status 模块，增加BurpAPI、OkHttp引擎驱动，性能爆炸；
- 新增 Burp Collaborator官方 DNSlog平台；
- 使用 JDK 21 版本编译；
- 优化相关漏洞检测逻辑。

#### 更新说明 - v1.4.6

1. 新增XyzDnsLog平台，删除不可用的DnsLog，由于国内政策问题，建议使用Ceye dnslog平台;
2. 修复适配Burp Suite Pro 2024年度版本报错问题;
3. 优化发包代码逻辑，更新插件稳定性。

#### 更新说明 - v1.4.5

1. 增加nacos漏洞被动扫描，CVE-2021-29441 & QVD-2023-6271 ;
2. 增加jpath主动模块化扫描，集合SpringBoot Env、Druid、Swagger 相关无害化POC;
3. 更新dnslog平台，删除不可用的dnslog，默认设置Ceye dnslog平台;
4. 修复新版本BurpSuite版本报错问题 #23 ;
5. 修复删除测试垃圾代码，优化插件稳定性。

### Tips
#### 由于工作原因，更新会比较慢，各位师傅提的issues，都会一条条仔细回复，新功能上线前团队内部会进行大量本地、实战项目测试所以周期较长，请各位师傅谅解。。ORZ


#### 更新说明 - v1.4.4

1. 优化代码结构；

2. 修复weblogic弱口令误报bug；

3. 增加otf后缀不扫描规则；

4. 删除asix/happaxis.jsp扫描规则；

5. 增加sql语法错误的页面回显扫描模块，只显示sql错误显示（参数后面增加单引号、双引号、反斜线，去查看有没有SQL错误语句）





#### 更新说明 - v1.4.3

1. 修复首次加载插件占用过多资源的问题造成假死进程状态。

2. 增加dnslog：DNSlog平台Xssx1，首次加载插件使用Ceye，后续启动则默认使用上次应用的dnslog，若网络环境较好，推荐使用Xssx1、Microsoftz方式。

3. 增加主动/被动 Ueditor .net 文件上传扫描模块。



#### 更新说明 - v1.4.2

1.增加Ceye dnslog平台，默认加载为Microsoftz，需要手动加载Ceye后，下次再打开将自动加载上次Apply应用的dnslog。

2.优化添加配置设置不显示插件的bug。

<img src="https://user-images.githubusercontent.com/48227194/219374135-69de3b1f-1721-44b4-a6e9-fd85d87baf1c.png"  width="80%" height="80%"/>


<img src="https://user-images.githubusercontent.com/48227194/219374032-1520df53-e171-4e8f-81f9-a527267fa727.png"  width="80%" height="80%"/>


#### 更新说明 - v1.4.1

1. 修复dnslog平台，更换api接口。
2. 版本号未修改，下次更新上传。

#### 更新说明 - v1.4

1. 增加 laravel 漏洞扫描、增加 laravel 主动扫描。
2. Issue 首字母大写（强迫症福音）。
3. 增加自定义每个请求之间延时的功能。
4. 增加SQL注入扫描、增加SQL注入主动扫描（MySQL报错，时间盲注SQL全系列）。
5. 修复Text4shell某些头部不扫描的问题。
6. 修复主动扫描时已存在的漏洞不会重复添加的问题。
7. 修复dnslog平台，更换api接口为dnslog.rest。


#### 更新说明 - v1.3

1. 增加thinkphp多语言rce漏洞扫描。
2. 优化thinkphp多语言rce探测数据包，减少发包数量。


#### 更新说明 - v1.2

1. 增加Fastjson参数扫描，并增加Fastjson主动扫描。
2. 修改引入的fastjson库版本为1.2.83，防止被反制。
3. 删除自己添加的bp api，改为maven库导入模式。
4. 增加axis服务接口扫描。


#### 更新说明 - v1.1

1. 增加Domain黑名单设置，可手动添加域名让插件对该域名进行判断是否为黑名单，从而不对其进行漏洞探测，来减少多余的探测进程影响渗透过程。。
2. 黑名单模式添加方式：google.com或者google，127.0.0.1或者127.0.0.1:8080；之前的扫描进程不会中断，下一个域名或者ip开始进行判断。
3. Reset表示恢复默认黑名单状态，也就是当前初始化状态。
4. apply表示当你启用BlackList功能时，需要apply加载。


#### 更新说明 - v1.0

1. 增加druid未授权扫描。
2. 修复log4j只扫描 已有头部与容易出现问题头部取交集 的问题。
3. 修复SpringBoot Env、swagger、druid在同一文件中导致的发现druid则不再探测其他漏洞的问题。
4. 修改dnslog请求次数，改为仅在插件开启时请求一次，方便查询dnslog结果。
5. 不扫描dnslog平台（某个家伙Yyy连dnslog都自己扫了）。
6. 增加了spring cloud gateway扫描，但没加漏洞检测。
7. 修复了spring cloud SPEL漏洞不报的问题，增加/functionRouter接口扫描。
8. 修复只取host不取port导致同一域名不同端口会跳过扫描的问题。
9. 修复fastjson扫描无法通过dnslog获取结果的问题。
10. 修复匹配URL后缀时使用包含的方式，改为以xx后缀结尾。
11. 修改log4j和text4shell为不扫描.asp/.php/.aspx等后缀。
12. 增加ThinkPHP主动自定义目录扫描
  ○ 比如：想扫描/Think5/目录的话，Repeater请使用GET /Think5/ HTTP/1.1；
  ○ 缺点：如果想主动扫描根目录或public目录的话，Repeater请使用根目录GET / HTTP/1.1。
13. 修改结果窗口的请求和响应分割线，将其保持在中间的位置。
14. 增加Weblogic主动扫描（这个也有类似ThinkPHP的自定义目录扫描）。


#### 更新说明 - v0.1

1. 修改dnslog部分，将ceye删除，创建了testmail.buzz（已修复）。
2. 增加Text4shell漏洞探测。
3. 增加springboot信息泄露扫描记录，防止扫描重复路径。
4. 增加配置窗口，替代config.json文件。


### ToDo

- [x] 增加swagger-resource的扫描与匹配规则。
- [x] 修复路径中包含.js即跳过扫描的问题。
- [x] 增加druid的扫描配置。
- [x] 增加springboot扫描绕过部分（后跟.json后缀、增加/绕过方式）。
- [x] 增加log4j扫描的头部字段。
- [x] 增加spring漏洞扫描（core没加）。
- [x] 增加log4j的404路径扫描，未测试，没找到测试环境。
- [x] 增加fastjson扫描规则。
- [x] 增加ThinkPHP Scan。
- [x] 修改sql注入扫描 - 后续慢慢来，工程量太大。
- [x] 增加weblogic检测poc。
- [x] 删除Level Make功能。
- [x] 修改scannedURL，改为每个POC都有自己的scannedURL并单独检测。
- [x] 增加fastjson检测（参数中的）。
- [ ] 增加shiro扫描key - 比较占用时间，决定不加。
- [ ] 增加log4j、Text4shell、fastjson的延迟检测 - 决定不加，手动探测吧。
- [x] 修改bp的interface，改为2022的interface，目前issue无法同步到dashboard那里。
- [x] 设置ThinkPHP扫描每个目标仅扫一次。
- [x] 设置weblogic扫描每个目标仅扫描一次。

</br>

### Thanks

部分代码参考来源：

https://github.com/pmiaowu/BurpShiroPassiveScan

https://github.com/pmiaowu/BurpFastJsonScan

https://github.com/l1ubai/GyScan

https://github.com/whwlsfb/Log4j2Scan

### END

 欢迎各位师傅提Issue。。。

