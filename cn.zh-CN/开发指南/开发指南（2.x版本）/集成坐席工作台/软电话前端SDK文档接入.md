软电话前端SDK文档接入 
=================================



通过该文档，您可以实现将坐席工作台嵌入到第三方系统中，直接在您系统中实现单点登录、接打电话等功能，并且您可以通过监听SDK中的方法来实现来电弹屏，下面的工作需要您公司的前端工程师来实施。您可随时关注该文档页面，SDK有更新时会第一时间更新文档页面。

一、前端资源 
---------------------------

**备注：更新前端资源版本以后，一定要在本地环境做全面测试以后再发布线上环境！** 

    <!--sdk样式文件-->
    <link rel="stylesheet" type="text/css" href="//g.alicdn.com/cloudcallcenter/web-workbench-sdk/{version-sdk}/main.min.css">
    <!--sdk js文件-->
    <script type="text/javascript" src="//g.alicdn.com/cloudcallcenter/SIPml/{version-sip}/SIPml-api.js"></script>
    <script type="text/javascript" src="//g.alicdn.com/cloudcallcenter-voip/web-agentbar-sdk/{version-voip}/index.js"></script>
    <script type="text/javascript" src="//g.alicdn.com/cloudcallcenter/web-workbench-sdk/{version-sdk}/workbenchSdk.min.js"></script>
    以上静态资源，将上面的{version-sdk}和{version-sip}替换为对应的版本号，当前最新版本号为：
    version-sip ==> 0.1.9
    version-voip ==> 1.1.5
    version-sdk ==> 1.1.4



开发模式时web-agentbar-sdk推荐引入index.js，会有一些打印提示。目前非压缩版本需要从此地址加载：https://cloudcallcenter-stage.oss-cn-hangzhou.aliyuncs.com/all-public/web-agentbar-sdk-uncompress-build/daily/1.1.5/index.js

开发模式时web-workbench-sdk推荐引入workbenchSdk.js，会有一些打印提示。目前非压缩版本需要从此地址加载：https://cloudcallcenter-stage.oss-cn-hangzhou.aliyuncs.com/all-public/web-workbench-sdk-uncompress-build/daily/1.1.4/workbenchSdk.js

二、初始化SDK 
-----------------------------

接入sdk之前需要做的工作：

1. 必须使用chrome浏览器，版本号为58以上。原因是云呼叫中心的通话是通过webRTC技术实现的，目前chrome浏览器对于webRTC技术的支持是最好的。为了保证您的通话质量及安全性，所以我们做出了这样的要求。

   

2. 软电话SDK所嵌入的自有业务系统必须使用https协议。原因是chrome在47版本之后，禁止http协议获取系统麦克风权限，会造成无法正常通话。

   

3. 如果您是在iframe标签内使用软电话SDK，那么需要为iframe标签增加allow="microphone"属性，来允许iframe标签获取系统麦克风权限。

   




初始化SDK：

window.workbench = new WorkbenchSdk(config)

三、config必选配置 
---------------------------------

1. dom

    挂载元素id



2. instanceId

    创建呼叫中心实例填写的域名， 
     https://ccc.console.aliyun.com/AccV2Instance  
    
    访问地址查看，格式 #/workbencch/XXX(域名)



![域名](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/1010996161/p256076.png)3. regionId

    云呼服务器部署的集群，如果没有特殊说明，为'cn-shanghai'



四、config可选配置 
---------------------------------

1. header

    是否展示头部(小休，下线，手机接听)，默认展示，参数类型：Boolean



2. width

    宽度，默认280，参数类型：Number；



3. height

    高度，默认552，参数类型：Number；（为了保证完整的UI展示，建议高度最低552）；



4. defaultVisible

    默认是否展示面板，默认为true，参数类型：Boolean；



5. offlineImage

    下线展示的静态图片地址，参数类型：String；



6. breakImage

    小休展示的静态图片地址，参数类型：String；



7. afterCallRule

    挂机后进入空闲状态的时间，单位秒，默认15秒，参数类型：Number；
    等待客服手动去从话后处理切换到空闲状态，为"manual"；



8. autoAnswerCall

    有来电时自动接听电话的时长，单位秒，默认为手动接听，参数类型：Number；





**\*\*\*\*\*\*以下参数是前端请求服务端接口的API地址及请求参数** **配置** **：\*\*\*\*\*\*** 

**请求路径为：** ${ajaxOrigin}${ajaxPath}?${ajaxApiParamName}=${apiName}\&product=CloudCallCenter\&version=2020-07-01\&region=${regionId}

9. ajaxOrigin

    请求源，默认请求当前源（location.origin），参数类型：String；



10. ajaxPath

    请求路径，默认为"/data/api.json"



11. withCredentials

    表示跨域请求时是否需要使用凭证,是否允许携带cookie,参数类型：Boolean



12. ajaxApiParamName

    ajaxType为param时指定区分action的名称，默认action，参数类型：String；



13. ajaxMethod

    请求方式，post|get 默认post，参数类型：String；



14. ajaxOtherParams

    其他自定义参数和request同一层级，参数类型：Object；



15. ajaxHeaders

    请求的header，参数类型：Object；



**\*\*\*\*\*\*请求接口的参数配置结束\*\*\*\*\*\*** 

16. exportErrorOfApi

    Toast提示接口的错误信息、ApiName、ErrorCode、RequestId，当接口出现错误的，提供错误信息，
    便于后端排查问题。默认是false，可根据需要是否Toast错误消息。



17. moreActionList

    在头部的功能模块的按钮列表，值可为["break", "offline", "adjustVolume"]，
    分别对应[小休，下线，调节音量]，用户可根据需求选择配置项，参数类型：Array



18. useLocalStorageToCall

    是否允许使用多标签页外呼，默认为false，参数类型：Boolean；详细介绍请参考第9条说明。



**\*\*\*\*\*\*以下是钩子函数：某些事件触发时的回调函数，类型均为function\*\*\*\*\*\*** 

19. onInit()

    SDK对象实例化完成时触发



20. onRegister(config)

    sip服务注册成功时触发



21. onLogIn()

    签入、上线时触发



22. onBreak()

    小休时触发



23. onReady()

    空闲时触发



24. onCallComing(callDetail)

    来电时触发，可以在该函数内获取到一个对象callDetail，callDetail参数信息含义如下：
    
    caller：主叫号码
    callee：被叫号码
    callType：呼叫类型
    jobId：当前通话的ID
    callContext：当前通话的详细信息
    
    注意：为了提高接通率，当有来电振铃30s后未接听，会自动将当前坐席置为小休状态。
    电话自动流转回转人工队列，分配给其他空闲坐席。



25.onBeforeCallDialing(payload)

    调用call方法前触发，如果配置这样一个钩子函数一定要执行callback方法，否则电话不会被拨打出去。
    
    payload返回数据的参数含义如下：
    callee：被叫号码
    userId：用户的userId
    callback：满足条件以后的调用，可传入完参数callee：被叫前缀+被叫号码，不传为面板或call方法传入的被叫号码



26. onCallDialing(callDetail)

    去电、拨号振铃时触发，可以在该函数内获取到一个对象callDetail，callDetail参数信息含义如下：
    caller：主叫号码
    callee：被叫号码
    callType：呼叫类型
    jobId：当前通话的ID
    callContext：当前通话的详细信息



27. onHangUp(type)

    挂机时触发
    参数type值为ringing代表呼入未接时挂机
    参数type值为dialing代表呼出未接时挂机
    参数type值为inbound代表呼入通话，通话中挂断
    参数type值为outbound代表呼出通话，通话中挂断



28. onBeforeCallHangup(payload)

    调用hangUp方法前触发，如果配置这样一个钩子函数一定要执行callback方法，否则电话不会被挂断。
    
    payload返回的参数含义如下：
    callback：回调方法
    jobId：当前通话ID
    channelId：这个坐席通话的channel id
    userId: loginInfo.userId 



29. onCallEstablish(callDetail)

    通话建立连接时触发，可以在该函数内获取到一个对象callDetail，callDetail参数信息含义如下：
    
    callContext：当前通话的详细信息



30. onCallRelease(callDetail)

    通话结束时触发，可以在该函数内获取到一个对象callDetail，callDetail参数信息含义如下：
    
    callContext：当前通话的详细信息



31. onErrorNotify(error)

    当有一些错误信息的时候触发，可以获取error信息，error参数含义如下：
    
    errorCode: 错误code,
    errorMsg: response错误信息,
    errorMsgTip: 我们定义的中文错误信息,
    requestId: 请求ID
    
    当处于开发阶段时建议在该钩子函数中打印参数表以获取错误信息



32. onStatusChange(codeDetail)

    任何状态改变都会触发该函数，可在该函数内监听当前状态值的变化过程，状态code的含义请参考本文档第八条状态对照表。
    可以获取到codeDetail参数，codeDetail参数含义如下：
    
    code: 当前状态码
    lastCode： 上次状态码
    context：上下文信息



33. sideNavList

    支持面板左侧导航显示自定义，默认是显示全部，配置以后显示自定义的导航，
    配置项：["呼入", "呼出","通话记录", "转接", "会议", "监听", "我的工作", "设备检测"]。



34. disableSaveStats

    默认为false（不关闭收集通话录音数据），参数类型：Boolean。
    收集坐席侧通话录音数据，方便出现问题时进行语音排查和网络分析。
    强烈不建议关掉，当出现问题时不方便工程师排查。



35. reducePanel

    sdk面板最小化Icon展示，默认为true，如果不需要该功能，可设置为false，参数类型：Boolean。



36. isEnableSwitchAdapter

    为提高坐席语音通话质量，新增多个接入点语音专线，默认为true。
    如果坐席需要直连云呼服务器，可设置为false，参数类型：Boolean。



37.customizedNotification

    支持集成客户自主定制来电桌面提醒，默认显示呼叫中心配置的桌面来电提醒，默认为false。
    传值为true时不展示，参数类型：Boolean。



38. apiAxiosFunc

    支持客户自己写请求接口的方法，最终返回结果为一个promise对象且返回的数据格式要和云呼叫中心公有云数据接口返回格式一致
    
    apiAxiosFunc: (apiName, params) => {
       console.log(apiName, params);
       let promise = axios({
          method: 'post',
          url:`/aliyun/ccc/api?action=${apiName}`,
          headers: {
             'Content-Type': 'application/x-www-form-urlencoded',
          },
          data: Qs.stringify({ request: JSON.stringify(params)}),
        });
        return promise;
    }



以下是配置示例：

    window.workbench = new window.WorkbenchSdk({
       dom: "workbench-container",
       regionId: 'cn-shanghai',
       width: "320px",
       height: "552px",
       instanceId: "XXX",
       ajaxPath: "/aliyun/ccc/api",
       ajaxMethod: "post";,
       afterCallRule: 15, // 挂机后的话后处理时间
       header: true,
       autoAnswerCall: 8, // 有来电振铃响8s后自动接听
       useOpenApiSdk: false,
       exportErrorOfApi: true,
       onInit: function () {
         // window.workbench.register() // 想实现自动上线在此注册
       },
       onErrorNotify: function (error) {
         console.warn(error)
       },
       onCallComing: function (callDetail) {
         console.log(callDetail);
       },
       onCallDialing: function (callDetail) {
         console.log(callDetail);
       },
       onStatusChange: function (codeDetail) {
         console.log(codeDetail);
       },
       onCallEstablish: function (callDetail) {
         console.log("这里是通话建立时触发的回调函数", callDetail)
       },
       onCallRelease: function (callDetail) {
         console.log("这里是通话结束时触发的回调函数", callDetail)
       },
       onHangUp: function (type) {
         console.log("这里是onHangUp事件，type =" + type)
       }
     })



五、SDK方法 
----------------------------

以下调用方式为：window.workbench.方法名(传参);

***注意：初始化SDK时定义的全局变量名称是否与文档定义的一致。*** 

1. isAvailBroswer()

    此方法用来检测当前浏览器是否支持使用软电话的，若浏览器不兼容软电话，会弹出一个提示框并维持3s，
    并在钩子函数onErrorNotify中可得到错误信息提示；若支持则无弹框提示，onErrorNotify中也无错误信息。



2. checkNetwork()

    此方法用来检测当前网络连接是否能连接到软电话的服务，检测是否被本地的防火墙拦截。



3. changeVisible(visible)

    显示或隐藏软电话面板，参数visible类型为Boolean



4.reRender()

    重新进行sdk的挂载，主要场景为在通话过程中或上线状态下切换到其他页面以后再回到坐席工作台界面，
    主要适用于SPA应用。



5. register(loginSkillGroupArray, accessPoint)

    首次签入，包含了sip服务注册+签入+置空闲，页面加载完毕，首次签入需调用该方法，
    调用完成后坐席进入空闲状态（需要在onInit钩子方法执行之后才可以调用）
    
    loginSkillGroupArray为数组，从接口ListSkillGroupsOfUser得到坐席的技能组列表信息
    {
        skillGroupId: xxx,
        skillGroupName: xxx,
        skillLevel: xxx
    }
    
    accessPoint为从接口GetTurnServerList获取的数组对象的region，必须和接口region保持一致，
    否则不能切换成功，自动传'default'，sdk内部实现选择最近的接入点。



6. logIn(loginSkillGroupArray)

    签入（处于签出状态可调用，状态为1），调用该方法实现上线操作
    loginSkillGroupArray数据格式跟register方法传loginSkillGroupArray的格式一致



7. logOut()

    签出，调用该方法实现下线操作



8. ready()

    置空闲、通过该方法可变为空闲状态，空闲状态后可接听、拨打电话。



9. applyForBreak(breakReason)

    申请小休，设置后来电将不会转到当前坐席，会转到其他空闲的坐席人员。
    这里参数方便统计不同的小休类型：
    breakReason：默认是'default'，可自定义小休原因



10. hangUp()

    挂断，通过该方法可结束通话



11. answer()

    接听电话，通过该方法可接听来电，建立通话连接。



12. getStatusCode()

    获取坐席当前状态码，code是当前状态 lastCode是上一次的状态



13. call(callee, caller)

    拨打电话
    
    callee：被叫号码，必传，数据类型是String
    caller：主叫号码，可以指定主叫号码；
               也可以不传，或者传''或者'auto'，根据外呼的号码的归属地选择与其同一归属地的主叫号码，
               若没有同一归属地的就随机在坐席绑定的外呼号码列表中随意选择一个；



14. sendDtmf(number)

    DTMF按键交互，发送dtmf; number可为0~9，*或#



15. callHold()

    通话保持，通过该方法可使通话进行保持，客户端听到的是一段音乐，坐席端说话客户端无法听到。



16. callRetrieve()

    通话取回，通过该方法结束通话保持的状态，重新建立客户端和坐席端的通话



17. muteAgent

    通话中静音



18. umMuteAgent

    取消通话中静音



19. changeVolumeInCall

    改变通话中的音量，参数volumeInCall值为[0, 1]的小数。



20. monitor(userId)

    监听方法，userId为坐席的ID



21. thirdCallTransfer(callee, caller)

    通话过程中直接转接，A和B通话，将通话直接交给C
    
    转接给坐席
    callee：坐席分机号
    caller: ''
    
    转接给外部电话
    callee：手机号
    caller：'auto'



22. initiateAttendedTransfer(callee, caller)

    通话过程中咨询转接，A和B通话，咨询C，咨询过程中A等待
    
    转接给坐席
    callee：坐席分机号
    caller: ''
    
    转接给外部电话
    callee：手机号
    caller：'auto'



23. thirdCallRetrieve

    三方通话取回，回到原来的通话，A和B通话，咨询C，咨询完成回到A和B通话



24. thirdCallTransferFinished

    三方咨询通话过程中转移通话，A和B通话，咨询C，咨询完成回到A和B通话，实现A和C通话



25.testTurnServers(args)

    测试云呼坐席接入点的时间。args的参数形式为：
    
    accessPoint: 可以只测某个接入点的值。不传为测试当前所有接入点
    currentFrequence： 测试几次。不传为1次，参数类型为Number
    callback: (res) => { 在这里得到接入点结果 }



26.switchAccessPoint(accessPoint)

    切换坐席接入点，accessPoint为从接口GetTurnServerList获取的turnServerListConfig数组对象的region，
    必须和接口region保持一致，否则不能切换成功，自动传'default'



六、服务端准备工作 
------------------------------

因为软电话SDK是嵌入到了您的自有业务系统中，在软电话SDK的使用过程中，会发起多个请求到自有业务系统的服务端，请求的调用地址可以通过四、config可选配置中的ajax相关配置来设置。需要将软电话SDK发出的请求经过您的服务端转发到云呼叫中心的服务端（也就是调用云呼叫中心的openAPI），然后将返回结果透传回软电话SDK中即可。详细步骤如下：

* 可以通过AK/SK方式请求接口，或通过oauth2方式请求接口

  

* 转发sdk发的请求到云呼叫中心服务端，根据 [API简介说明](https://help.aliyun.com/document_detail/85054.htm)调用对应openAPI，将返回结果透传回软电话SDK即可，软电话SDK所需的返回结果必须是JSON数据格式。

  

* 坐席，技能组等需要在阿里云云呼叫中心控制台进行配置，否则无法正常工作；

  




|      类型      |             接口              |        描述         |
|--------------|-----------------------------|-------------------|
| **业务接口**     | GetLoginDetails             | 获取坐席的信息           |
| **业务接口**     | ListSkillLevelsOfUser       | 坐席的技能组信息          |
| **业务接口**     | ListOutboundNumbersOfUser   | 坐席的外呼号码           |
| **业务接口**     | ListConfigItems             | 坐席工作台配置信息         |
| **业务接口**     | GetTurnServerList           | 获取云呼提供的turn服务接入点  |
| **业务接口**     | ListPrivilegesOfUser        | 坐席的权限列表           |
| **业务接口**     | GetTurnCredentials          | Turn服务的账号密码       |
| **业务接口**     | ListDevices                 | 登录的设备信息           |
| **业务接口**     | AddAgentDevice              | 保存设备信息            |
| **业务接口**     | PickOutboundNumbers         | 自动选择外呼号码          |
| **业务接口**     | GetNumberLocation           | 查询号码归属地           |
| **业务接口**     | ListRealtimeAgentStates     | 查询当前坐席的状态列表（转接功能） |
| **业务接口**     | ListAgentStates             | 查询当前的坐席列表（监听功能）   |
| **业务接口**     | ResetAgentState             | 重置坐席状态            |
| **业务接口**     | ListRecentCallDetailRecords | 查询通话记录            |
| **业务接口**     | ListSkillGroups             | 获取技能组，只有admin有权限  |
| **业务接口**     | ListBriefSkillGroups        | 转接的技能组列表          |
| **业务接口**     | ListHistoricalAgentReport   | 获取坐席我的工作数据        |
| **业务接口**     | SaveTerminalLog             | 给服务端上报错误日志        |
| **话务操作相关接口** | SignOutGroup                | 退出                |
| **话务操作相关接口** | TakeBreak                   | 小休                |
| **话务操作相关接口** | ReadyForService             | 置空闲               |
| **话务操作相关接口** | MakeCall                    | 拨打电话              |
| **话务操作相关接口** | AnswerCall                  | 接听电话              |
| **话务操作相关接口** | ReleaseCall                 | 挂电话               |
| **话务操作相关接口** | HoldCall                    | 通话保持              |
| **话务操作相关接口** | RetrieveCall                | 通话取回              |
| **话务操作相关接口** | BlindTransfer               | 直接转接              |
| **话务操作相关接口** | InitiateAttendedTransfer    | 发起咨询转接            |
| **话务操作相关接口** | CompleteAttendedTransfer    | 咨询转接转移通话          |
| **话务操作相关接口** | CancelAttendedTransfer      | 取消转接              |
| **话务操作相关接口** | SendDtmfSignaling           | 发送DTMF按键          |
| **话务操作相关接口** | MonitorCall                 | 发起监听              |
| **话务操作相关接口** | BargeInCall                 | 监听状态下强插           |
| **话务操作相关接口** | InterceptCall               | 监听状态下强拆           |
| **话务操作相关接口** | Coach                       | 监听状态下辅导           |
| **话务操作相关接口** | MuteCall                    | 静音                |
| **话务操作相关接口** | UnmuteCall                  | 取消静音              |
| **话务操作相关接口** | LaunchSurvey                | 发送语音满意度           |



七、开发错误、操作逻辑错误 
----------------------------------

SDK会抛出两种类型的错误：开发错误、操作逻辑错误。建议您在开发时配置onErrorNotify钩子并打印参数，方便排查问题并将相关错误抛出给客户，方便问题排查。

1. 开发错误：简单的说就是可以通过修改您的代码来修复的错误，是稳定重现的，这一类型的错误常见的有配置参数类型出错、调用sdk方法未按照状态约束表进行。比如配置项onInit要求是一个方法，但是却传入了一个字符串，那么sdk会直接执行如下代码，遇到这样的错误js执行被打断，必须要根据错误提示先进行修复

   

2. 操作逻辑错误：这一类错误是用户使用呼叫中心过程中一些操作不当造成的错误，不一定是稳定重现的，这一类型的错误常见的有未允许浏览器对本域名开启声卡权限、账号在别处登录、客服不在任何技能组中、呼叫中心网络错误等。这类错误sdk会调用onErrorNotify方法通知外部系统，钩子函数onErrorNotify中的所有情况：

   




    9001：出现此错误码，当前状态不能操作该api
    6001：AgentNotRegistered
    6002：AgentNotLogin
    6003：SkillIdNotExist
    6004：AgentIdNotExist
    6005：CurrentStatesNotAllowedChanged
    6006：CurrentStateIsBusy
    6007：CallExisted
    6008：CallNotExisted
    6009：AgentOffline
    8001：GetUserMediaFailed
    8002：'check Audio Device Failed'
    8003：'call already exist'
    8004：'api interception agent req by status'
    8005：'user request is handling'
    8020：OtherUsingInCall
    8021：OnKillSelf
    8022：OnReload
    8023：GetConfigError
    CallerIsNull： 主叫号码为空
    NoAvailableCallersWithRedialing：当前主叫号码不管用
    NoAvailableCallee：不可用被叫
    AllAvailableCallersHaveBeenCalled： 当前没有可外呼的号码
    accessPointNull：接入点为空
    testTurnError：接入点连接失败，切换到直接连接方式
    protocolError：访问的网址协议必须为https
    browserError：浏览器需要是chrome



八、状态对照表及状态说明 
---------------------------------



| 状态码 |  描述  |        操作        |
|-----|------|------------------|
| -1  | 未注册  | 当前状态只能操作register |
| 0   | 注册中  |                  |
| 1   | 离线   | 上线               |
| 2   | 小休   | 置空闲，下线           |
| 3   | 空闲   | 下线、外呼、接听，发起监听，会议 |
| 5   | 话后处理 | 置空闲              |
| 6   | 振铃   | 接听               |
| 8   | 拨号   | 挂断               |
| 9   | 呼入通话 | 挂断               |
| 10  | 呼出通话 | 挂断               |
| 11  | 内部通话 | 结束通话             |
| 12  | 通话保持 | 取消通话保持           |
| 16  | 发起三方 | 通话取回、取消三方通话      |
| 17  | 咨询通话 | 取消咨询通话、咨询通话转移    |
| 20  | 被动求助 | 挂断               |
| 21  | 监听   | 挂断               |



九、对比1.0sdk文档的更新 
------------------------------------

**一、前端资源地址有变化** 

**二、config必选配置项** 

* instanceId数据来源有变化，为呼叫中心填写的唯一域名

  

* 新增regionId配置，删除useOpenApiSdk参数

  




**三、config可选配置** 

* 前端请求资源的路径配置为${ajaxOrigin}${ajaxPath}${ajaxApiParamName}=${apiName}\&product=CloudCallCenter\&version=2020-07-01\&region=${regionId}

  

* 回调函数onCallComing、onBeforeCallDialing、onCallDialing、onBeforeCallHangup、onCallEstablish、onErrorNotify、onStatusChange返回的参数都统一为对象格式，具体见文档说明

  

* 删除enableRecord配置项

  




**四、SDK方法** 

* 离线坐席手机功能放到了坐席管理，通过后端接口修改坐席工作模式，不在前端SDK中提供了

  




**五、服务端准备工作，新增了话务相关的接口，详见上方文档说明** 

**六、错误的code码** 

* 减少了双登相关的错误码、2.0如果发现有坐席登录，第二次登录会被拦截

  




**七、状态说明** 

* 小休状态错误码变成了2

  



