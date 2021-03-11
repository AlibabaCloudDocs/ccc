软电话SDK前端接入 
===============================



#### 软电话SDK前端接入 {#h4--sdk-}

**通过该文档，您可以实现将坐席工作台嵌入到第三方系统中，直接在您系统中实现单点登录、接打电话等功能，并且您可以通过监听SDK中的方法来实现来电弹屏，下面的工作需要您公司的前端工程师来实施。** 

![坐席工作台](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/2639562061/p173056.png)

一、引入sdk静态资源 {#h2--sdk-1}
------------------------

#### 备注：更新前端资源版本以后，一定要在本地环境做全面测试以后再发布线上环境！请查看文档「十三、changelog」，根据自己的需求更新。 {#h4--changelog-}

    <!--sdk样式文件-->
    <link rel="stylesheet" type="text/css" href="https://g.alicdn.com/acca/workbench-sdk/{version-sdk}/main.min.css">
    <!--sdk js文件-->
    <script type="text/javascript" src="//g.alicdn.com/cloudcallcenter/SIPml/{version-sip}/SIPml-api.js"></script>
    <script type="text/javascript" src="//g.alicdn.com/cloudcallcenter-voip/agentbar-sdk/{version-voip}/index.js"></script>
    <script type="text/javascript" src="https://g.alicdn.com/acca/workbench-sdk/{version-sdk}/workbenchSdk.min.js"></script>
    以上静态资源，将上面的{version-sdk}和{version-sip}替换为对应的版本号，当前最新版本号为：
    version-sip ==> 0.1.8
    version-voip ==> 2.8.3
    version-sdk ==> 1.1.0



**您可随时关注该文档页面，SDK有更新时会第一时间更新文档页面。** 开发模式时workbench-sdk推荐引入workbenchSdk.js，会有一些打印提示。目前非压缩版本需要从此地址加载：[https://cloudcallcenter-stage.oss-cn-hangzhou.aliyuncs.com/all-public/workbench-sdk-uncompress-build/daily/1.1.0/workbenchSdk.js](https://cloudcallcenter-stage.oss-cn-hangzhou.aliyuncs.com/all-public/workbench-sdk-uncompress-build/daily/1.0.6/workbenchSdk.js)

二、初始化sdk {#h2--sdk2}
--------------------

#### 初始化前必要的准备工作 {#h4-u521Du59CBu5316u524Du5FC5u8981u7684u51C6u5907u5DE5u4F5C}

1. 必须使用`chrome浏览器`，版本号为58以上。原因是云呼叫中心的通话是通过webRTC技术实现的，目前chrome浏览器对于webRTC技术的支持是最好的。为了保证您的通话质量及安全性，所以我们做出了这样的要求。

   

2. 软电话SDK所嵌入的自有业务系统必须使用`https协议`。原因是chrome在47版本之后，禁止http协议获取系统麦克风权限，会造成无法正常通话。

   

3. 如果您是在`iframe标签`内使用软电话SDK，那么需要为iframe标签增加`allow="microphone"`属性，来允许iframe标签获取系统麦克风权限。

   




### 初始化SDK {#h3--sdk}

    window.workbench = new WorkbenchSdk(config)



三、config必选配置 {#h2--config-3}
----------------------------

#### 1. dom {#h4-1-dom}

挂载元素id

#### 2. instanceId {#h4-2-instanceid}

实例Id 使用主账号登录https://ccc.console.aliyun.com/AccInstance, 点击每条实例后面的实例id复制过来即可。

#### 3. useOpenApiSdk {#h4-3-useopenapisdk}

是否使用了openApiSdk，参数类型：Boolean。因为我们产品使用过程中所有接口都需要经过我们的POP接口平台，而POP接口平台对于接口的入参有一定规则（比如1.入参的key值需要大写；2.不支持数组格式，只接收arryKey.1,arryKey.2这种格式），对于接口返回结果的key首字母全部是大写，并且数组外面多包了一层，而这并不是workbenchSdk所需要的，所以用户需要再将格式转换。为了减少用户集成过程中的成本，我们workbenchSdk内部根据该配置项进行了转换。useOpenApiSdk的配置规则如下：

* 如果您引入的是workbenchSdk0.2.9及以后版本，并且后端语言使用了阿里云[openapi-sdk](https://help.aliyun.com/document_detail/85054.html)的用户该值传true，未使用的该值传false

  

* [Java版本的demo](https://cloudcallcenter-stage.oss-cn-hangzhou.aliyuncs.com/all-public/ccc-crm-demo-java.zip)中未使用[openapi-sdk](https://help.aliyun.com/document_detail/85054.html)，所以您如果使用了我们提供的[Java版本的demo](https://cloudcallcenter-stage.oss-cn-hangzhou.aliyuncs.com/all-public/ccc-crm-demo-java.zip)，该值传false

  

* [PHP版本的demo](https://cloudcallcenter-stage.oss-cn-hangzhou.aliyuncs.com/all-public/ccc-crm-demo-php.zip)使用了[openapi-sdk](https://help.aliyun.com/document_detail/85054.html)，所以您如果使用了我们提供的PHP版本的demo，该值传true，并且因为workbenchSdk0.2.9及以后版本对于每个接口的入参和返回结果都做了转化，以前的老用户需要将之前处理接口入参和处理接口返回的逻辑去掉。

  

* [基于 URL 发起 HTTP/HTTPS GET 请求](https://help.aliyun.com/document_detail/85148.html?spm=a2c4g.11186623.2.4.v1BKUn)，该值传false，

  




四、config可选配置 {#h2--config-4}
----------------------------

#### 1. header {#h4-1-header}

是否展示头部(小休，下线，手机接听），默认展示，参数类型：Boolean

#### 2. width {#h4-2-width}

宽度，默认280，参数类型：Number；

#### 3. height {#h4-3-height}

高度，默认552，参数类型：Number；（为了保证完整的UI展示，建议高度最低552）；

#### 4. defaultVisible {#h4-4-defaultvisible}

默认是否展示面板，默认为true，参数类型：Boolean；

#### 5. offlineImage {#h4-5-offlineimage}

下线展示的静态图片地址，参数类型：String；

#### 6. breakImage {#h4-6-breakimage}

小休展示的静态图片地址，参数类型：String；

#### 7. afterCallRule {#h4-7-aftercallrule}

挂机后进入空闲状态的时间，单位秒，默认15秒，参数类型：Number；如果不想自动切换进入空闲状态，而是等待客服手动去从话后处理切换到空闲状态，那么这个值必须为"manual"；

#### 8. autoAnswerCall {#h4-8-autoanswercall}

有来电时自动接听电话的时长，单位秒，默认为手动接听，参数类型：Number；

#### 9. enableRecord {#h4-9-enablerecord}

是否开启坐席侧录音，默认为不开启，值为false，参数类型：Boolean；

#### 10. ajaxType {#h4-10-ajaxtype}

请求路径形式,值为："param" 或 "path";，默认为"param";。

    为"param"请求路径为 ajaxOrigin/ajaxPath?ajaxApiParamName=apiName；
    为"path"请求路径为 ajaxOrigin/ajaxPath/module/action 



#### 11. ajaxOrigin {#h4-11-ajaxorigin}

请求源，默认请求当前源（location.origin），参数类型：String；

#### 12. ajaxPath {#h4-12-ajaxpath}

请求路径，默认为"/data/api.json"

#### 13. withCredentials {#h4-13-withcredentials}

表示跨域请求时是否需要使用凭证,是否允许携带cookie,参数类型：Boolean

#### 14. ajaxApiParamName {#h4-14-ajaxapiparamname}

ajaxType为param时指定区分action的名称，默认action，参数类型：String；

#### 15. ajaxMethod {#h4-15-ajaxmethod}

请求方式，post\|get 默认post，参数类型：String；

#### 16. ajaxOtherParams {#h4-16-ajaxotherparams}

其他自定义参数和request同一层级，参数类型：Object；

#### 17. ajaxHeaders {#h4-17-ajaxheaders}

请求的header，参数类型：Object；

#### 18. exportErrorOfApi {#h4-18-exporterrorofapi}

Toast提示接口的错误信息、ApiName、ErrorCode、RequestId，出现接口错误的时候，提供这些信息给我们，便于后端很快的排查出问题。默认是false，可根据需要是否展示Toast消息提示。

#### 19. moreActionList {#h4-19-moreactionlist}

在头部的功能模块的按钮列表，值可为\["onlyCall", "mobilePhoneAnswer", "break", "offline", "adjustVolume"\]，分别对应\[仅外呼，手机接听，小休，下线，调节音量\]，用户可根据需求选择配置项，参数类型：Array

#### 20. useLocalStorageToCall {#h4-20-uselocalstoragetocall}

是否允许使用多标签页外呼，默认为false，参数类型：Boolean；详细介绍请参考第9条说明。

### 以下是钩子函数：某些事件触发时的回调函数，类型均为function {#h3--function}

#### 21. onInit() {#h4-21-oninit-}

SDK对象实例化完成时触发

#### 22. onRegister(config) {#h4-22-onregister-config-}

sip服务注册成功时触发

    config: 呼叫中心配置项



#### 23. onCallComing(connid,caller,callee,contactId,skillgroupId) {#h4-23-oncallcoming-connid-caller-callee-contactid-skillgroupid-}

来电时触发，用户可以在该函数内获取参数信息，参数含义如下：

    connid: 话务Id
    caller: 主叫号码
    callee: 被叫号码
    contactId: 通话ID，通话记录查询需要的字段
    skillgroupId:技能组id



注意：为了提高接通率，当有来电振铃30s后未接听，会自动将当前坐席置为小休状态。电话自动流转回技能组队列，分配给其他空闲坐席。

#### 24. onCallDialing(connid, caller, callee, contactId) {#h4-24-oncalldialing-connid-caller-callee-contactid-}

去电、拨号振铃时触发，用户可以在该函数内获取参数信息，参数含义如下：

    connid: 话务Id
    caller: 主叫号码
    callee: 被叫号码
    contactId: 通话ID，通话记录查询需要的字段



#### 25.onBeforeCallDialing(payload) {#h4-25-onbeforecalldialing-payload-}

调用call方法前触发，如果没有配置这样一个钩子函数则不会触发。payload返回数据的参数含义如下：

        callee（被叫号码）
        userName（用户的ramId）
        callback（满足条件以后的调用，可传入完参数callee：被叫前缀+被叫号码，不传为面板或call方法传入的被叫号码）



#### 26. onCallEstablish(connid, caller, privateData) {#h4-26-oncallestablish-connid-caller-privatedata-}

通话建立连接时触发，用户可以在该函数内获取参数信息，参数含义如下：

    connid: 话务Id
    caller: 主叫号码
    privateData: 通话中的相关信息，类型为对象，其中包含：
        acid: 通话Id，通话记录查询需要的字段
        adacc：当前通话坐席信息
        dnis：被叫号码
        data: 随路数据。如果此电话为呼入，且ivr流程中设置了随路数据参数，则这个字段有相应的值
        skillgroupname : 所接入技能组id



#### 27. onCallRelease(connid, caller, privateData) {#h4-27-oncallrelease-connid-caller-privatedata-}

通话结束时触发，用户可以在该函数内获取参数信息，参数含义同onCallEstablish

#### 28. onErrorNotify(error) {#h4-28-onerrornotify-error-}

当有一些错误信息的时候触发，可以获取error信息，error参数含义如下：

    error = { 
        errorApi：错误API,
        errorCode: 错误code, 
        errorMsg: response错误信息, 
        errorMsgTip: 我们定义的中文错误信息,
        requestId: 请求ID;
    }



当处于开发阶段时建议在该钩子函数中打印参数表以获取错误信息。

#### 29. onLogOut() {#h4-29-onlogout-}

签出、下线时触发

#### 30. onLogIn() {#h4-30-onlogin-}

签入、上线时触发

#### 31. onBreak() {#h4-31-onbreak-}

小休时触发

#### 32. onReady(type) {#h4-32-onready-type-}

空闲时触发，如果设置了离线坐席，type类型为'offline'

#### 33. onHangUp(type) {#h4-33-onhangup-type-}

挂机时触发

* 参数type值为ringing代表呼入未接时挂机

  

* 参数type值为dialing代表呼出未接时挂机

  

* 参数type值为inbound代表呼入通话，通话中挂断

  

* 参数type值为outbound代表呼出通话，通话中挂断

  




#### 34. onStatusChange(code, lastCode, context) {#h4-34-onstatuschange-code-lastcode-context-}

任何状态改变都会触发该函数，用户可在该函数内监听当前状态值的变化过程，状态code的含义请参考本文档第8条状态对照表。

    code: 当前状态码
    lastCode： 上次状态码
    context：包含话务Id：connid



#### 35. sideNavList {#h4-35-sidenavlist}

支持面板左侧导航显示自定义，默认是显示全部，配置以后显示自定义的导航，配置项：\["呼入", "呼出","通话记录", "转接", "会议", "监听", "我的工作", "设备检测"\]。

#### 36. enableRecord {#h4-36-enablerecord}

是否允许坐席侧通话录音，默认为false（关闭），参数类型：Boolean。

#### 37. disableSaveStats {#h4-37-disablesavestats}

收集坐席侧通话录音数据，方便出现问题时进行语音排查和网络分析。强烈不建议关掉，当出现问题时不方便工程师排查。默认为false（不关闭收集通话录音数据），参数类型：Boolean。

#### 38. reducePanel {#h4-38-reducepanel}

sdk面板最小化Icon展示，默认为true，如果不需要该功能，可设置为false，参数类型：Boolean。

#### 39. isEnableSwitchAdapter {#h4-39-isenableswitchadapter}

为提高坐席语音通话质量，新增多个接入点语音专线，默认为true。如果坐席需要直连云呼服务器，可设置为false，参数类型：Boolean。

#### 40.customizedNotification {#h4-40-customizednotification}

支持集成客户自主定制来电桌面提醒，默认显示呼叫中心配置的桌面来电提醒，默认为false，传值为true时不展示，参数类型：Boolean。

#### 41.apiAxiosFunc {#h4-41-apiaxiosfunc}

支持客户自己写请求接口的方法，最终返回结果为一个promise对象且返回要和[云呼叫中心公有云数据接口返回格式](https://help.aliyun.com/document_detail/85150.html?spm=a2c4g.11186623.6.620.4b453709mk03zQ)一致，返回的数据对象key为小写。

    apiAxiosFunc: (apiName, params) => {
        console.log(apiName, params);
        let promise = axios({
            method: 'post',
            url: `/aliyun/ccc/api?action=${apiName}`,
            headers: {
            'Content-Type': 'application/x-www-form-urlencoded',
            },
            data: Qs.stringify({ request: JSON.stringify(params)}),
        });
        return promise;
    }



### 以下是配置示例： {#h3--}

    ```
    window.workbench = new window.WorkbenchSdk({
        dom: "workbench-container",
        width: "320px",
        height: "550px",
        instanceId: "18b4f6bd-12f7-4ab6-91d1-bf43b854f35c",
        ajaxPath: "/aliyun/ccc/api",
        ajaxMethod:"post";,
        afterCallRule: 15,  // 挂机后的话后处理时间
        header: true,
        autoAnswerCall: 8,  // 有来电振铃响8s后自动接听
        useOpenApiSdk: false,
        exportErrorOfApi: true,
        moreActionList: ["mobilePhoneAnswer", "break", "offline"],
        onInit: function () {
          // win.workbench.register() // 想实现自动上线在此注册
        },
        onBeforeCallDialing: function (payload) {
           console.log('onBeforeCallDialing----->', payload)
           if(payload.callee 满足某个条件) {
               // 执行callback调用 拨打电话
               payload.callback();
           }
        },
        onErrorNotify: function (error) {
          console.warn(error)
        },
        onCallComing: function (connid,caller,callee,contactId,skillgroupId) {
          console.log(connid,caller,callee,contactId,skillgroupId);
        },
        onCallDialing: function (connid,caller,callee,contactId) {
          console.log(connid,caller,callee,contactId);
        },
        onStatusChange: function (code, lastCode, context) {
          console.log(code, lastCode, context);
        },
        onCallEstablish: function (connid, caller, privateData) {
          console.log("这里是通话建立时触发的回调函数", connid, caller, privateData)
        },
        onCallRelease: function (connid, caller, privateData) {
          console.log("这里是通话结束时触发的回调函数", connid, caller, privateData)
        },
        onHangUp: function (type) {
          console.log("这里是onHangUp事件，type =" + type)
        }
      })
    
    
    ```



五、sdk方法 {#h2--sdk-5}
--------------------

    以下调用方式为：window.workbench.方法名(传参);



注意：初始化SDK时定义的全局变量名称是否与文档定义的一致。

#### 0. changeVisible(true/false) {#h4-0-changevisible-true-false-}

显示或隐藏软电话面板

#### 1.reRender() {#h4-1-rerender-}

重新进行sdk的挂载，主要场景为在通话过程中或上线状态下切换到其他页面以后再回到坐席工作台界面，主要适用于SPA应用。

#### 2. register(loginSkillGroupArray, accessPoint) {#h4-2-register-loginskillgrouparray-accesspoint-}

首次签入，包含了sip服务注册+签入+置空闲，页面加载完毕，首次签入需调用该方法，调用完成后坐席进入空闲状态（需要在onInit钩子方法执行之后才可以调用）

    1.loginSkillGroupArray为数组，数据格式为[{单个签入的技能组信息},...]，从接口ListSkillGroupsOfUser得到坐席的技能组列表信息，然后做一下数据转化，单个签入技能组信息格式为
    {
        groupName: skillGroup.skill.skillGroupId,
        groupLevel: skillGroup.level,
        skillGroupName: skillGroup.skill.skillGroupName
    }
    2.accessPoint为从接口GetTurnServerList获取的turnServerListConfig数组对象的region，必须和接口region保持一致，否则不能切换成功，自动传'default'。



#### 3. logIn(skillGroupsList) {#h4-3-login-skillgroupslist-}

签入（处于签出状态可调用，状态为1），调用该方法实现上线操作，如：workbench.logIn(skillGroupsList)skillGroupsList数据格式跟register方法传loginSkillGroupArray的格式一样

#### 4. logOut() {#h4-4-logout-}

签出，调用该方法实现下线操作,如：workbench.logOut()

#### 5. ready() {#h4-5-ready-}

置空闲、通过该方法可变为空闲状态，空闲状态后可接听、拨打电话。

#### 6. applyForBreak(breakId, breakName) {#h4-6-applyforbreak-breakid-breakname-}

申请小休，设置后来电将不会转到当前坐席，会转到其他空闲的坐席人员。这里参数方便统计不同的小休类型：

* breakId小休ID取值范围为1-5的任意值

  

* breakName小休名，例如'开会'、'午休'、'临时有事'

  




#### 7. hangUp() {#h4-7-hangup-}

挂断，通过该方法可结束通话

#### 8. answer() {#h4-8-answer-}

接听电话，通过该方法可接听来电，建立通话连接。

#### 9. getStatus() {#h4-9-getstatus-}

获取当前状态描述，具体参考七

#### 10. getStatusCode() {#h4-10-getstatuscode-}

返回对象, 有两个属性: code是当前状态 lastCode是上一次的状态，具体参考七

#### 11. call(callee, caller, publicKey, useVirNumCall) {#h4-11-call-callee-caller-publickey-usevirnumcall-}

打电话，各参数含义如下:

    callee为被叫号码不可空，必传，加密时传加密后的密文，不加密时传真实被叫号码。
    caller为主叫号码，可以指定主叫号码，也可以不传，或者传''。不传时使用面板里选择的主叫号码或技能组所绑定外呼号码的第一个,为'auto'时，根据外呼的号码的归属地选择与与其同一归属地的主叫号码，若没有同一归属地的就随机在技能组里选择一个主叫号码。
    publicKey为公钥，对被叫号码进行加密时该值必传，非加密情况不传或传空值。使用加密方式外呼时,需要调用加密接口将号码进行加密，得到加密后的被叫号码和公钥后直接调用该call方法：call(密文, 主叫号码, 公钥)。
    useVirNumCall为Boolean类型，传true表示只要caller配置了虚拟号码都会使用虚拟号码进行外呼，不传或传false,如果您使用呼叫中心的面板进行操作，会根据坐席是否选择使用外呼号码进行呼叫，如果勾选了则将使用虚拟号码进行外呼否则直接用呼叫中心的号码进行呼叫。



#### 12. sendDtmf(number) {#h4-12-senddtmf-number-}

二次拨号，发送dtmf; number可为0\~9，\*或#

#### 13. callHold() {#h4-13-callhold-}

通话保持，通过该方法可使通话进行保持，客户端听到的是一段音乐，坐席端说话客户端无法听到。

#### 14. callRetrieve() {#h4-14-callretrieve-}

通话取回，通过该方法结束通话保持的状态，重新建立客户端和坐席端的通话

#### 15. offline(mobileNumber, caller) {#h4-15-offline-mobilenumber-caller-}

离线坐席,对应着面板中的"手机接听";设置离线坐席以后，坐席状态为空闲状态（3）

    mobileNumber: 离线坐席的手机号码
    caller: 外呼号码（可不填，不填由系统指定）



调用该方法后，客户打电话到呼叫中心，呼叫中心会主动外呼mobileNumber，并将客户的电话与mobileNumber电话建立连接，实现手机接听客户的电话。

#### 16. online() {#h4-16-online-}

结束手机接听状态，变为使用坐席PC端接听

#### 17. transferStatisfic() {#h4-17-transferstatisfic-}

发送语音满意度，需要在云呼叫中心平台设置开启语音满意度调研功能，调用后将自动挂机，让客户进行满意度评分

#### 18. downloadRecord(contactId, onlyPlay) {#h4-18-downloadrecord-contactid-onlyplay-}

播放和下载录音，详情可查看本文档第十一条

    contactId: 话务ID(录音ID)(参数类型：String)
    onlyPlay: 是否仅播放（参数类型：Boolean）



#### 19. isAvailBroswer() {#h4-19-isavailbroswer-}

此方法用来检测当前浏览器是否兼容软电话的功能，执行此方法后若浏览器不兼容软电话，会弹出一个提示框并维持3s，并在钩子函数onErrorNotify中可得到错误信息提示；若兼容则无弹框提示，onErrorNotify中也无错误信息。

#### 20. checkNetwork() {#h4-20-checknetwork-}

此方法用来检测当前网络连接是否能连接到软电话的服务，检测是否被本地的防火墙拦截。

#### 21. launchShortMessageAppraise() {#h4-21-launchshortmessageappraise-}

发送短信满意度，调用此方法需要开通[短信服务](https://help.aliyun.com/document_detail/86878.html?spm=5176.10725720.0.0.7bb35137hp8pH9)，并在云呼叫中心平台设置开启短信满意度调研功能，调用后会给用户发送满意度短信。

#### 22. launchShortMessageMissedCall() {#h4-22-launchshortmessagemissedcall-}

发送漏话提醒短信，使用前需要先进行相关设置，参考文档：[短信配置列表](~~89702~~)[漏话短信](~~89703~~)；

#### 23. thirdCallTransfer(callee, caller, useVirNumCall, accSkillGroupName) {#h4-23-thirdcalltransfer-callee-caller-usevirnumcall-accskillgroupname-}

直接转接。A呼叫B，B直接将电话转接到C。其中，C可以是一个指定坐席，也可以是一个技能组。参数如下：

* 转坐席

        callee为坐席的分机号
        caller为转接的主叫号码，传''
        useVirNumCall为是否使用虚拟号码

  

* 转外部电话

        callee为转外部电话的号码
        caller为转接的主叫号码，可不传；也可传'auto'，将会通过被叫callee的归属地调用pickGlobalOutboundNumbers接口获取号码
        useVirNumCall为是否使用虚拟号码

  

* 技能组

        callee为转技能组ivr的路由点
        caller为''
        useVirNumCall为是否使用虚拟号码
        accSkillGroupName为所要转接技能组名称

  

  具体使用说明请参考[坐席将电话转接给技能组](https://help.aliyun.com/knowledge_detail/135274.html)。

  #### 24. conferenceInit(callee,caller) {#h4-24-conferenceinit-callee-caller-}

  咨询转接。A呼叫B，B发起呼叫C。 A被hold，BC通话，先咨询是否将电话转接。参数如下：
  

* 转坐席

        callee为坐席的分机号
        caller为转接的主叫号码，传''

  

* 转外部电话

        callee为转外部电话的号码
        caller为转接的主叫号码，可不传；也可传'auto'，将会通过被叫callee的归属地调用pickGlobalOutboundNumbers接口获取号码

  

  坐席状态变化过程：当发起conferenceInit后，坐席状态会从9（呼入通话）或者10（呼出通话）变成12（通话保持），再立刻到16（发起三方）。当C接听后，坐席状态会到17（咨询通话）。如果在此过程中，A挂机了，坐席状态就会变成普通的呼出场景，即如果A在C接听前挂机，B的状态将会从16到8（拨号）变到10（呼出通话）；如果A在C接听后挂机，B的状态会从17到10。
  




#### 25. thirdCallTransferFinished() {#h4-25-thirdcalltransferfinished-}

咨询转接后，将电话转接出去。A呼叫B，B发起呼叫C，BC通话之后，B操作将电话转移，AC通话。此处是B将电话转移的方法。

#### 26. thirdCallRetrieve() {#h4-26-thirdcallretrieve-}

咨询转接后，取消转接。A呼叫B，B发起呼叫C；BC未通之前，B操作取回，AB恢复通话。

#### 27. 会议相关接口 {#h4-27-}

坐席A可以在两种情况下发起会议：空闲状态下拉B和C发起会议；A与B在通话中，A添加C发起会议。下面分情况介绍：

* A在空闲状态下拉B和C发起会议

        A先与B建立通话：如果B是空闲坐席，则调用agentToAgent(B.分机号） ;如果B是外部电话，则调用call(B.电话) 建立A与B的通话。
        通过A的状态变化（状态由8到10，或者由8到11），发起到C的通话：如果C是空闲坐席， A调用conferenceInit(C.分机号, '') ；如果B为非空闲坐席或者是外部电话，A调用conferenceInit(B.电话) 建立A与C的通话。
        当A当状态为17时，则调用conferenceFinished()最终建立会议。

  

* A在与B通话状态下拉C发起会议

        如果C是空闲坐席， A调用conferenceInit(C.分机号, '') ；如果B为非空闲坐席或者是外部电话，A调用conferenceInit(B.电话) 建立A与C的通话。
        当A当状态为17时，则调用conferenceFinished()最终建立会议。

  




#### 28. thirdCallHangupThird(callee) {#h4-28-thirdcallhangupthird-callee-}

三方会议中挂断第三方通话, 会议第三方是坐席callee传入坐席的分机号，第三方是外部电话callee传入电话号码

#### 29. applyForCallOnly(isCallOnly) {#h4-29-applyforcallonly-iscallonly-}

设置坐席是否只进行外呼。有些场景，坐席希望只外呼，不接听来电，可以用此方法来设置坐席仅外呼。参数isCallOnly为boolean。isCallOnly设置为true设置为仅外呼，isCallOnly不传或传false恢复接听来电。

#### 30. changeVolumeInCall(volumeInCall) {#h4-30-changevolumeincall-volumeincall-}

改变通话中坐席耳机音量。参数volumeInCall为值为\[0, 1\]的小数。

#### 31. toggleMuteInCall() {#h4-31-togglemuteincall-}

通话中静音，通话过程中，客户不会听到坐席侧的声音。

#### 32.monitor(monitordn) {#h4-32-monitor-monitordn-}

监听功能；monitordn为被监听者的分机号

#### 33.testTurnServers(args) {#h4-33-testturnservers-args-}

测试云呼坐席接入点的时间。args的参数形式为：

    accessPoint: 可以只测某个接入点的值。不传为测试当前所有接入点
    currentFrequence： 测试几次。不传为1次，int值
    callback: 回调函数



#### 34.switchAccessPoint(accessPoint) {#h4-34-switchaccesspoint-accesspoint-}

切换坐席接入点，accessPoint为从接口[GetTurnServerList](~~131791~~)获取的turnServerListConfig数组对象的region，必须和接口region保持一致，否则不能切换成功，自动传'default'

#### 35.resetUserStatus(callback) {#h4-35-resetuserstatus-callback-}

当坐席状态出现异常以后，重置坐席状态，callback为成功以后的回调。此方法调用了新接口ResetUserStatus

六、服务端准备工作 {#h2--6}
------------------

因为软电话SDK是嵌入到了您的自有业务系统中，在软电话SDK的使用过程中，会发起多个请求到自有业务系统的服务端，请求的调用地址可以通过第4项中的ajax相关配置来设置。需要将软电话SDK发出的请求经过您的服务端转发到云呼叫中心的服务端（也就是调用云呼叫中心的openAPI），然后将返回结果透传回软电话SDK中即可。详细步骤如下：

* 参考 [OAuth2单点登录](~~63062~~)文档，获取到access_token；

  

* 转发sdk发的请求到云呼叫中心服务端，根据 [API简介说明](~~85054~~)调用对应openAPI，将返回结果透传回软电话SDK即可，软电话SDK所需的返回结果必须是JSON数据格式。

  

* 坐席，技能组等需要在阿里云云呼叫中心控制台进行配置，否则无法正常工作；

  




#### SDK工作台需要使用的接口 {#h4-sdk-}



|                     接口                     |                          描述                           |
|--------------------------------------------|-------------------------------------------------------|
| [ListOutboundPhoneNumberOfUser](~~92453~~) | 获取坐席外呼号码                                              |
| [ListSkillGroupsOfUser](~~63045~~)         | 获取坐席所归属的技能组列表。                                        |
| [ListRecentCallRecords](~~88589~~)         | 获取坐席的通话记录                                             |
| [ListConfig](~~70128~~)                    | 获取工作方式配置                                              |
| [GetServiceExtensions](~~63028~~)          | 获取服务号码，比如发送语音满意度时所需的分机号码（实际是满意度调查IVR的路由点），或者是其他技能组号码。 |
| [LaunchAppraise](~~71562~~)                | 点击软电话SDK中的发送语音满意度按钮时调用，记录坐席发送了满意度，用来统计满意度发送率          |
| [GetSmsConfig](~~89914~~)                  | 获取短信满意度                                               |
| [RequestLoginInfo](~~63030~~)              | 获取坐席登录的信息                                             |
| [RefreshToken](~~63029~~)                  | 刷新坐席工作台的token，用来保持坐席工作台有效的登录状态。                       |
| [PickGlobalOutboundNumbers](~~70126~~)     | 根据被叫归属地自动选择外呼号码                                       |
| [GetNumberRegionInfo](~~70127~~)           | 获取号码的归属地                                              |
| [ListRealTimeAgent](~~70131~~)             | 获取坐席实时数据                                              |
| [ListAgentStates](~~90007~~)               | 获取坐席状态                                                |
| [ListRecordingsByContactId](~~71532~~)     | 根据通话录音Id获取通话记录                                        |
| [GenerateAgentStatisticReport](~~73242~~)  | 获取坐席今日工作报表                                            |
| [LaunchShortMessageAppraise](~~88312~~)    | 发送短信满意度                                               |
| [SendPredefinedShortMessage](~~89915~~)    | 发送漏话短信提醒                                              |
| [CallOnlinePrivacyNumber](~~94807~~)       | 使用虚拟号码外呼                                              |
| [ModifyPrivacyNumberCallDetail](~~94928~~) | 虚拟号码外呼记录保存                                            |
| [GetRecordOssUploadParam](~~120936~~)      | 获取录音上传参数                                              |
| [CreateFault](~~120938~~)                  | 上报故障信息                                                |
| [AddAgentDevice](~~120933~~)               | 保存坐席设备信息                                              |
| [ModifyAgentDevice](~~120934~~)            | 修改坐席登录状态                                              |
| [ListAgentDevices](~~120935~~)             | 获取坐席设备信息                                              |
| [GetTurnCredentials](~~131786~~)           | 获取语音专线的用户名密码                                          |
| [GetTurnServerList](~~131791~~)            | 获取语音专线点列表                                             |
| [ResetUserStatus](~~134877~~)              | 重置坐席状态                                                |
| [CheckNumberAvaliable](~~163443~~)         | 外呼被叫号码是否设置了黑名单                                        |



七、开发错误和操作逻辑错误。 {#h2--7}
-----------------------

SDK会抛出两种类型的错误：开发错误、操作逻辑错误。

* 开发错误：简单的说就是可以通过修改您的代码来修复的错误，是稳定重现的，这一类型的错误常见的有`配置参数类型出错`、`调用sdk方法未按照状态约束表进行`。比如配置项onInit要求是一个方法，但是却传入了一个字符串，那么sdk会直接执行如下代码，遇到这样的错误js执行被打断，必须要根据错误提示先进行修复

      throw new Error("onInit must be a function");

  




<!-- -->

* 操作逻辑错误：这一类错误是用户使用呼叫中心过程中一些操作不当造成的错误，不一定是稳定重现的，这一类型的错误常见的有`未允许浏览器对本域名开启声卡权限`、`账号在别处登录`、`客服不在任何技能组中`、`呼叫中心网络错误`等。这类错误sdk会调用onErrorNotify方法通知外部系统，钩子函数onErrorNotify中的所有情况：

  




    以下参数格式为：errorCode：errorMsg/errorMsgTip
    当出现as错误码和event签出时，都建议重新刷新页面登录。
    {
    // as返回的错误码
        6001: '管理员不存在',
        6002: '管理员未登录',
        6003: '技能ID不存在',
        6004: '管理员ID不存在',
        6005: '当前状态忙碌，请求失败，请刷新页面后重试',
        6006: '当前状态忙碌，请求失败，请刷新页面后重试',
        6007: '当前状态忙碌，请求失败，请刷新页面后重试',
        6008: '当前状态不对',
        7001: '后端服务任务请求不对',
        7002: '您请求对应的电话已经不存在',
        8020: '该账号有人正在使用且在通话中',
        8021: '您的账号已在别处登录，如需登录请刷新页面', // 界面提醒，按钮不可点
        8022: '需重新加载配置', // 这个配置如何展示
        8001: '请检查声卡权限', // 提示设备异常的界面
        8002: '请检查声卡权限', // 提示设备异常的界面
        WSConnectSlowly: '当前WebScoket连接缓慢，请等待或刷新后重新上线',
    
        /* 以下为迁出的event事件 */
        AB_normal: '软电话正常签出',
        ASM_Private: '坐席管理服务连接超时，请检测网络连接情况', // '私协超时',
        ASM_SIP: '语音服务连接超时，请检测网络连接情况', // 'SIP 30秒超时',
        'ASM_Private&SIP': '坐席管理服务和语音服务连接超时，请检测网络连接情况', // '私协和SIP都超时',
        ka_unregister: '您的账号已在别处登录，如需登录请刷新页面', // ka发送的unregister签出
        KA_register: '您的账号已在别处登录，如需登录请刷新页面' // 'KA发送的register',
        WSConnectSlowly: '当前WebScoket连接缓慢，请等待或刷新后重新上线', // WS连接缓慢
        stream_local_refused: '浏览器无麦克风权限，请刷新页面',
        get_lo_failed: '无法获取本地媒体流，请切换接入点到上海',
        systemErrorNotInAnySkillGroup: '您尚未被加入到技能组中，暂时无法使用，请联系呼叫中心管理员添加',     // 坐席没有配置技能组
        'network error': '网络连接出现错误', // 调用sdk提供的方法出现浏览器或网络报错
        'browser error': ${浏览器的相关描述},
    
        // 调用方法进行呼叫参数设置及校验
        'caller outof range': '没有配置坐席个人外呼号码或外呼号码未被添加到该客服所在的技能组中',
        'no callee': '请输入被叫号码',
    }



**您应该通过某种方式把errorMsg告知给用户，方便用户解决问题后重新进行操作。我们推荐您在开发时配置onErrorNotify钩子并打印参数，方便排查问题。** 

八、状态对照表 {#h2--8}
----------------



| 状态码(getStatusCode) |     注释     | 描述(getStatus) |
|--------------------|------------|---------------|
| -1                 | 未注册        | off           |
| 0                  | 注册中        | off           |
| 1                  | 签出         | off           |
| 2                  | 签入         | logIn         |
| 3                  | 空闲         | ready         |
| 4                  | 小休         | break         |
| 5                  | 话后处理       | other         |
| 6                  | 振铃         | callComing    |
| 8                  | 拨号         | dialingCall   |
| 9                  | 呼入通话       | inCall        |
| 10                 | 呼出通话       | inCall        |
| 11                 | 内部通话       | inCall        |
| 12                 | 通话保持       | inCall        |
| 16                 | 发起三方       | other         |
| 17                 | 咨询通话       | other         |
| 18                 | 咨询通话，再切换通话 | other         |
| 19                 | 会议         | other         |
| 20                 | 被动求助       | other         |
| 21                 | 监听         | monitoring    |



九、各个状态下的sdk方法约束说明 {#h2--sdk-9}
------------------------------



|  状态  |                                                                                                                 具体描述                                                                                                                 |
|------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 未注册  | 状态值为-1，这时用户只能执行 `首次签入` （即首次上线）操作。                                                                                                                                                                    |
| 签出   | 状态值为1，这时用户只能执行 `签入` （即上线）操作。                                                                                                                                                                         |
| 签入   | 状态值为2，当用户 `签入` 后状态值变为2，签入成功后状态值又马上变为3（即空闲），状态值由2到3这个过程很快（几乎是同时进行）；也就是说用户在2的状态时来不及做任何操作就进入到空闲状态（状态值3）。                                                                                                |
| 空闲   | 状态值为3，空闲状态下用户可进行 `拨号` 、 `小休` 、 `退出组` （即下线）等操作，注：只有该状态下可收到外部打过来的电话（即振铃）。                                                              |
| 小休   | 状态值为4，该状态下可执行 `结束小休` 、 `退出组` 、 `拨号` （即下线）操作。                                                                                         |
| 话后处理 | 状态值为5，该状态下可执行 `退出组` （即下线）、 `小休` 、 `继续工作` （即开始接听）、 `拨号` 、 `再次拨打` 等操作。 |
| 振铃   | 状态值为6，该状态下只可执行 `接听` 操作。                                                                                                                                                                              |
| 拨号   | 状态值为8，该状态下只可执行 `挂机` 操作。                                                                                                                                                                              |
| 呼入通话 | 状态值为9，该状态下可执行 `挂机` （需要设置）、 `保持` （即通话保持）操作。                                                                                                                           |
| 呼出通话 | 状态值为10，该状态下可执行 `挂机` 、 `保持` （即通话保持）、 `二次拨号` 操作。                                                                                       |
| 话路保持 | 状态值为12，即通话保持，该状态下只可执行通话 `取回` （通话取回）操作。                                                                                                                                                               |
| 发起三方 | 状态值为16，即咨询转接时，从发起咨询到咨询通话建立之间的过程，该状态下可执行通话 `取回` （通话取回）操作。                                                                                                                                             |
| 咨询通话 | 状态值为17，即咨询转接的过程，该状态下可执行通话 `取回` （通话取回）操作和通话 `转移` （通话转接）操作。                                                                                                            |
| 监听   | 状态值为21，即监听坐席的通话的状态，该状态下只可执行 `挂机` 操作。                                                                                                                                                                 |
|      | 注：其他功能SDK暂未提供。                                                                                                                                                                                                                       |



十、 多标签页外呼使用要点 {#h2--10}
-----------------------

### 使用场景 {#h3-u4F7Fu7528u573Au666F}

    做了CRM系统集成的用户，可以使用我们的sdk界面进行外呼，但是也存在一些用户需要在其他页面，比如一些用户名单列表或用户详情页面通过点击按钮进行外呼，这时就需要在该页面进行sdk注册，但是我们的sdk是不支持多标签注册的，因此我们提供了这样的方案：在注册过sdk的标签页监听其他标签页localstorage的变化，在其他标签页设置localstorage来实现外呼。



### 使用方法 {#h3-u4F7Fu7528u65B9u6CD5}

1. 设置配置项useLocalStorageToCall为true

   

2. 首先所有标签页都要在一个浏览器中，要求只有一个标签页注册WorkbenchSdk，并保持该标签页的登录状态。

   

3. 在`其他标签页`拨打电话时设置一个localstorage（如果拨打电话页和注册页处于同一标签页，该方法将无法监听到，导致电话拨打不出去），key为workbenchSdkCall，value为{callee: '15588888888', caller: '057128236231', random: 0.234234234}。其中caller的值具体设置参照上面sdk方法中call(callee, caller)的规定，设置成功以后，当注册过WorkbenchSdk的标签页监听到localstorge的workbenchSdkCall变化时，便自动外呼电话：

        var value = {
            callee: '15588888888',
            caller:'057128236231',
            publicKey: '',
            useVirNumCall: true,
            random: Math.random()
        }
        localStorage.setItem('workbenchSdkCall', JSON.stringify(value))

   

4. 在其他标签页挂断电话时，需设置一个key为workbenchSdkHangup，value为一个随机数的localstorage，便自动挂断电话

        localStorage.setItem('workbenchSdkHangup',  Math.random())

   

5. 可通过localStorage.getItem('workbenchSdkStatus')来查询当前workbench状态码，当值为3,4,5时才可以外拨号码；当值为8,9,10,11,12,21时才可挂断电话。

   




十一、录音播放和下载使用说明 {#h2--11}
------------------------

/\*\*

* downloadRecord(contactId, onlyPlay)

  

* contactId\[String\] 话务id

  

* onlyPlay\[Boolean\] 是否仅可以播放，默认为true，只可以播放，不可以下载

  

* \*/\`

  




<!-- -->

* 提供了简单的录音播放和下载的方式，内部实现方式为根据contanceId调用[ListRecordingsByContactId](https://help.aliyun.com/document_detail/71532.html?spm=a2c4g.11186623.6.604.uIbPt7)获取到录音详细信息，再根据录音详细信息中的fileName去调用[DownloadRecording](https://help.aliyun.com/document_detail/65295.html?spm=a2c4g.11186623.6.603.S9YUMb)来获取录音播放的地址。所以如果您没有使用我们提供的java版crm-demo，需要您自行配置上面的两个API。

  

* contactId获取方式：

  * 根据[ListCallDetailRecords](https://help.aliyun.com/document_detail/65296.html?spm=a2c4g.11186623.6.606.5piH7j)获取；

    
  
  * 在呼入呼出时，根据onCallComing和onCallDialing两个钩子方法的参数中获取，自行存储起来。

    
  

  

* 在使用此方法时，对于坐席角色的用户，contactId所对应的通话记录的关联坐席必须是该当前登录用户；对于管理员角色，contactId则没有限制。

  

* 调用后，会出现如下图界面，自动播放第一条录音，

  ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/2639562061/p173057.png)
  




十二、常见问题解答 {#h2--12}
-------------------

* SDK中有来电弹屏功能吗？

  * 通过监听SDK中的onCallComing事件，每当有来电时，会携带来电号码，您根据该事件在您系统中做对应的来电弹屏即可。

    
  

  

* 可以不用SDK的页面吗？

  * 可以的，可以完全只调用SDK中的方法，实现坐席工作台的功能。

    
  

  

* 可以多个标签页初始化SDK，达到每个标签页都可以外呼的场景吗？

  * 不可以，目前一个浏览器中只能有一个标签页初始化SDK，多个标签页初始化，会将已上线的标签页踢出。但是可以保留一个标签页SDK只初始化注册一次，在配置项中添加useLocalStorageToCall为true，详情请参照第九条多标签页外呼使用要点

    
  

  

* 怎样可以实现初始化SDK后客服无感知的自动上线？

  * 可以在onInit中去执行register方法即可。

    
  

  

* 怎样在不刷新页面的情况下去重新加载sdk

  




    reloadWorkbench = function () {
      console.log('reload workbench');
      if (window.workbench) {
        var currentChild = document.getElementById('workbench-container').firstChild;
        document.getElementById('workbench-container').removeChild(currentChild);
        window._AgentBarSdk.DestroyPhoneSdk(); // 销毁_AgentBarSdk
        window.workbench = null; // workbench变量置为空
        window._AgentBarSdk = null; // _AgentBarSdk变量置为空
    
        window.workbench = new window.WorkbenchSdk({
          ...以下配置同第一次实例化参数
        });
      }
    }



十三、changelog {#h2--changelog13}
-------------------------------

* 1.0.6(July 10, 2020)

  * 修复话后处理afterCallRule配置首次不生效bug。

    
  
  * 增加自定义接口请求方法apiAxiosFunc。

    
  
  * 话后处理状态允许设置仅外呼方法。

    
  
  * 缩小面板设置手机接听功能以后，对按钮进行控制操作。

    
  
  * onBeforeCallDialing配置支持加入外呼号码前缀。

    
  
  * 坐席上线login方法支持传参，选择签入的技能组，详情见sdk方法。

    
  

  

* 1.0.0(Apr 09, 2020)

  * 号码数量过大，后端接口ListOutboundPhoneNumberOfUser返回部分号码，接口数据格式做了变化，详情见接口文档。

    
  
  * 修复小休状态断网以后自动上线。

    
  

  

* 0.9.6(Jan 15, 2020)

  * 修复只外呼状态拨打电话未接通的定时器bug。

    
  

  

* 0.9.5(Dec 19, 2019)

  * 增加坐席可以直连云呼服务器的参数。

    
  
  * 增加坐席websocket连接断了的事件统计信息。

    
  
  * 增加sip消息发送间隔超过10秒日志统计。

    
  

  

* 0.9.2(Oct 15, 2019)

  * 修复手工选择接入点情况下，如果接入点有问题，自动切换到直连模式。

    
  
  * 如果坐席因为workingMode=offline而无法上线，给出重置坐席状态界面，坐席可以自行重置坐席状态后上线。

    
  

  

* 0.8.8(Sep 16, 2019)

  * 修复接入点环境下，呼入电话30秒不接听坐席无小休bug。

    
  
  * 修复设备检测异常后，坐席发大量消息bug。

    
  

  

* 0.8.6(Sep 5, 2019)

  * 坐席签入时，所选择的技能组不能超过20个。由于后端数据库限制，签入技能组超过20个，会造成通话报表数据不准确。

    
  
  * 通话中，坐席可以将电话转接给指定技能组。

    
  
  * 提供会议中挂断第三方接口。

    
  

  

* 0.8.4(Aug 22, 2019)

  * 支持自动选择接入点，根据语音专线测速选择通话质量好的线路，提供切换坐席接入switchAccessPoint(accessPoint) 方法。

    
  
  * 当坐席状态为通话中或状态紊乱时，可调用云呼sdk提供的resetUserStatus方法进行重置或直接调用ResetUserStatus接口。

    
  
  * 未使用阿里云提供的java版demo的用户，需自行配置接口API，获取语音专线列表接口API：[GetTurnServerList](~~131786~~)、获取语音专线连接的用户名密码：[GetTurnCredentials](~~131791~~)、重置坐席状态（ResetUserStatus）

    
  

  

* 0.8.0(July 17, 2019)

  * 记录坐席上线时的公网IP和端口

    
  
  * 自动选择外呼号码API全部统一为PickGlobalOutboundNumbers ，请注意你们系统后端是否支持该接口的调用

    
  
  * 咨询转接和会议转接支持caller传'auto'，具体请查看SDK方法，按照归属地自主选择号码，本地号码优先

    
  
  * 新增杭州、青岛坐席接入点

    
  
  * 自动选择号码下支持使用虚拟号码外呼，根据被叫归属地查询对应虚拟号码归属地信息

    
  

  

* 0.7.4(July 5, 2019)

  * 坐席侧日志级别按照实例配置项等级级别进行记录

    
  
  * 支持浏览器消息提醒自定义样式，新增customizedNotification配置项

    
  

  

* 0.7.0(May 27, 2019)

  * 新增语音专线接入点华南区（深圳）功能

    
  
  * 优化通话质量异常保障流程

    
  
  * 修复0.6.9版本sdk最小化配置项reducePanel不生效、话后处理等bug

    
  
  * 修复面板正常呼叫状态下出现'转接中'的bug。（在通话状态下坐席侧断网，这个时候as（坐席服务）没有检测到挂机事件，没有清空坐席呼叫状态导致再次呼叫以为是发起三方，此时显示有误）

    
  

  

* 0.6.9(May 27, 2019)

  * 新增SDk面板最小化功能，默认展示，如果不需要这个功能可以修改配置项reducePanel为false

    
  
  * 增加自动接听参数校验逻辑，避免接口没有返回值业务逻辑判断不明确

    
  
  * 修复0.6.8版本设置手机接听弹框消失的bug

    
  

  

* 0.6.8(May 27, 2019)

  * 新增坐席通话过程中通话质量异常保障

    
  
  * 坐席双登等异常签出时增加坐席上线是的ip、时间等辅助信息帮助坐席排查原因

    
  
  * 增加设备检测功能

    
  
  * 坐席侧通话录音、坐席侧通话信息数据收集等功能及配置项增加，请看第四条config配置

    
  

  




<!-- -->

* 0.6.5(May 07, 2019)

  * 修复坐席工作台切换tab以后呼出面板号码列表下拉框数据不完整的bug

    
  
  * 抛出坐席因为网络断开导致下线的原因

    
  

  




<!-- -->

* 0.6.2(May 07, 2019)

  * 坐席非主动性签出页面进行统一展示，请查看文档中的第七条。

    
  
  * 支持通过外部调用方法进行选择技能组签入，register方法

    
  

  




<!-- -->

* 0.6.0(Apr 18, 2019)

  * 呼入电话增加随路数据信息：onCallEstablish、onCallRelease参数改变。

    
  
  * 支持坐席侧录音功能。

    
  
  * 坐席通话质量数据监控。

    
  

  




<!-- -->

* 0.5.7(Apr 03, 2019)

  * 修复多标签使用虚拟号码外呼功能。

    
  

  




<!-- -->

* 0.5.4(Mar 18, 2019)

  * 增加坐席测静音、坐席耳机音量大小调整、分技能组签入功能。

    
  

  

* 0.5.2(Feb 20, 2019)

  * 增加仅外呼功能。

    
  

  

* 0.4.7(Dec 20, 2018)

  * 增加exportErrorOfApi配置项，当出现接口报错时，便于及时定位问题，Toast提示增加显示ErrorMsg、ErrorCode、RequestId、ApiName。默认是不显示，集成对接时可根据需求是否展示。

    
  

  

* 0.4.5 (Nov 28, 2018 )

  * 解决查询慢而无法显示通话记录的问题，通话记录接口（ListRecentCallRecords）只在pageNumber为1的时候才显示totalCount，用到这个参数请一下处理逻辑。

    
  

  




<!-- -->

* 0.4.2(Otc 30, 2018)

  * 增加虚拟号码外呼功能，管理员给配置的坐席外呼号码绑定了虚拟号码，坐席选择使用绑定了虚拟号码的外呼号码进行外呼，用户侧显示的就是虚拟手机号。未使用阿里云提供的java版demo的用户，需自行配置使用虚拟号码在线呼叫接口API(CallOnlinePrivacyNumber)：[虚拟号码在线呼叫](~~92453~~)、更新话务ID（ModifyPrivacyNumberCallDetail）：[更新话务ID](~~94928~~)

    
  

  




<!-- -->

* 0.4.0(Sep 27, 2018)

  * 增加坐席个人外呼号码功能，管理员配置了坐席外呼号码，并在技能组中开启"允许使用个人外呼号码"功能，坐席在工作时，可以选择个人外呼号码进行外呼。未使用阿里云提供的java版demo的用户，需自行配置获取坐席外呼号码API(ListOutboundPhoneNumberOfUser)：[获取坐席外呼号码](~~92453~~)

    
  

  




<!-- -->

* 0.3.2(Sep 06, 2018)

  * 增加监听功能，技能组组长及管理员角色可以使用，坐席没有权限使用。可以监听当前已接通并正在通话中的通话，仅能听到双方的实时音频。使用监听时，请务必引用本文档第一节中的最新的静态资源。未使用阿里云提供的java版demo的用户，需自行配置获取坐席状态的API：[获取坐席状态](~~90007~~)

    
  
  * 增加发送漏话提醒短信功能，详情说明请查看本文档第五节中第22个方法

    **launchShortMessageMissedCall** 

    ，未使用阿里云提供的java版demo的用户，需自行配置以下两个API：[获取短信配置、](~~89914~~)[发送短信](~~89915~~)
    
  

  




<!-- -->

* 0.3.0(August 22, 2018)

  * 完善多标签页外呼所需的状态值（workbenchSdkStatus）的设置

    
  
  * 增加退出阿里云账号的方法logoutAliyunAccount

    
  
  * 添加监控，对于用户的上线、下线、小休和接口调用添加监控信息，这样用户出现错误的状态我们可以收到预警，方便为用户更好排查问题。

    
  
  * 修改通话记录接口，以前管理员可以查看所有人的通话记录，现在改成管理员也只能查看自己的通话记录。所以，未使用阿里云提供的java版demo的用户，需自行配置该 坐席工作台获取通话记录 接口（ListRecentCallRecords）：https://help.aliyun.com/document_detail/88589.html

    
  

  




<!-- -->

* 0.2.9(August 1, 2018)

  * 增加来电时自动接听，优先级为：集成版传入的配置项autoAnswerCall \> 云呼叫中心平台的设置

    
  
  * 根据客户是否使用openapi-sdk来统一转化接口的入参和出参，详情参照本文档第3条config必选配置

    
  
  * 网络异常、声卡异常抛出onErrorNotify

    
  
  * 麦克风有问题时按钮显示故障已排除请重新上线

    
  
  * 修复"呼出"界面，输入框的焦点问题

    
  
  * 增加发送短信满意度功能，使用此功能需要在云呼叫中心的设置页面设置开启，未使用阿里云提供的java版demo的用户，需自行配置该发送短信满意度的接口（LaunchShortMessageAppraise）：https://help.aliyun.com/document_detail/88312.html

    
  

  




<!-- -->

* 0.2.8(July 5, 2018)

  * 修复对于没有开通满意度的老实例无法上线问题

    
  

  




<!-- -->

* 0.2.7(July 4, 2018)

  * 修复话后处理状态时，切换路由组件重载后计时器显示问题。

    
  
  * 优化上线前的请求。

    
  
  * 添加"我的工作"版块，统计坐席人员今日工作概览

    
  
  * 添加外呼号码加密功能，参考sdk方法中的call(callee, caller, publickey)。未使用阿里云提供的java版demo的用户，需自行配置该加密接口（EncryptRequest）：

    https://help.aliyun.com/document_detail/75726.html
    
  

  




<!-- -->

* 0.2.6(June 14, 2018)

  * 添加withCredentials配置，用以跨域请求时是否需要使用凭证

    
  
  * 通话记录添加搜索条件

    
  
  * 添加网络检测功能

    
  
  * 优化关闭浏览器二次提示的条件

    
  
  * 添加ivr认证功能

    
  
  * 上线前合并请求，解决操作过快接口无法返回情况

    
  
  * 增加便捷的录音播放和下载方法，详情查看此文档第10条

    
  

  




<!-- -->

* 0.2.4(May 24, 2018)

  * 拨打电话时，技能组没有绑定号码给提示信息并抛错。

    
  
  * 麦克风异常界面点击后给2s的提示，并且在上线后、通话前监测麦克风失败，自动下线。

    
  
  * 修改发送满意度方法

    
  
  * 优化onErrorNotify

    
  

  




<!-- -->

* 0.2.3(May 3，2018)

  * 优化向外暴露的sdk方法中的call方法，call(callee, caller),caller为主叫号码，可以指定主叫号码，也可以不传，或者传''，不传时使用面板里选择的主叫号码或技能组所绑定外呼号码的第一个，为'auto'时，根据外呼的号码的归属地选择与与其同一归属地的主叫号码，若没有同一归属地的就随机在技能组里选择一个主叫号码；callee为被叫号码不可空，必传

    
  
  * 减少接口调用频率，优化转接功能

    
  
  * 实现多标签页外呼。

    
  
  * 添加满意度统计功能

    
  
  * 添加外呼号码和来电号码是否部分隐藏功能（隐藏号码中的四位数字）

    
  
  * 因本次增加了功能点，非java用户需自行配置以下接口

    * LaunchAppraise 发动满意度接口 

      https://help.aliyun.com/document_detail/71562.html
      
    
    * ListConfig 批量获取配置项接口 

      https://help.aliyun.com/document_detail/70128.html
      
    

    
  

  




<!-- -->

* 0.2.2(April 12，2018)

  * 新增转接功能，坐席在通话过程中，需要转接其他人来帮忙接待时，可以转接到其他坐席人员，也可转接到外部电话。转接分为咨询转接和直接转接，咨询转接是指正在通话坐席先与目标坐席通话，咨询是否可以转接到目标坐席，通话坐席可根据通话结果选择"取消转接"或"转移通话"；直接转接是指直接转接给目标坐席。

    
  
  * 改版坐席工作台UI界面，将横版的tab，改为左侧导航。

    
  
  * 将发送满意度的方法暴露出来，transferStatisfic(callee, connid)，外界可直接调用，其中callee参数通过GetServiceExtensions访问。

    
  
  * 因本次增加了许多功能，所以非java后端的用户，需自行配置以下四个接口：

    * GetNumberRegionInfo 获取号码归属地

      https://help.aliyun.com/document_detail/70127.html
      
    
    * PickLocalNumber 自动选择外呼号码

      https://help.aliyun.com/document_detail/70126.html
      
    
    * ListCallDetailRecords 通话记录及通话详单

      https://help.aliyun.com/document_detail/65296.html
      
    
    * ListRealTimeAgent 转接时获取实时坐席数据

      https://help.aliyun.com/document_detail/70131.html
      
    

    
  

  




<!-- -->

* 0.2.1(March 28, 2018)

  * 新增

    **通话记录** 

    功能，坐席可查看自己近30天内前100条通话记录。
    
  
  * 新增配置项

    **height** 

    ，用来配置面板高度，高度越高，通话记录显示的条数越多，根据您的实际使用情况来填写即可。
    
  
  * 新增

    **自动选择外呼号码** 

    功能，系统会在当前坐席可用的外呼号码列表中，自动匹配和外呼号码相同归属地的主叫号码进行外呼，当可用的外呼号码列表中没有相同归属地的号码时，降级匹配同省的主叫号码，如果依旧匹配不到，将随机选择；这样可以很大的提高外呼接通率；
    
  
  * 新增

    **号码归属地显示** 

    功能，呼入呼出时，都会显示主被叫号码的归属地信息；数据来源于阿里通信，数据库数据相对来说比较新，但无法保证100%显示归属地信息。
    
  

  




<!-- -->

* 0.1.9(March 14, 2018)

  * onInit的作用变更为：SDK对象初始化完成。

    
  
  * 新增

    **首次签入register** 

    方法，为上一个迭代（0.1.8）的深层次优化，通过此方法可实现首次登录sip服务注册以及自动签入的功能，不过该方法必须在onInit执行了之后才可以调用！
    
  
  * 新增onRegister钩子，

    **首次签入register** 

    完成后调用，携带的参数为呼叫中心配置项config。
    
  
  * 修复调用call方法时，面板没有自动切换到拨打界面的问题。

    
  

  




<!-- -->

* 0.1.8(March 5, 2018)

  * 将SDK注册sip服务的时间由加载时自动注册，改为点击上线按钮时进行注册，上线按钮做了以下几件事情：注册-签入-空闲；这样做是为了解决有些客服人员工作时需要通过多个标签页打开自有的CRM系统，但是每个标签页又都加载了SDK，造成了多个标签页都去注册sip服务引起的坐席状态异常。（请注意页面顶部的SDK静态资源均有更新）

    
  

  




<!-- -->

* 0.1.5(February 8, 2018)

  * 新增ajaxHeaders配置项，对象格式

    
  
  * 添加离线坐席功能，即离线后设置手机接听；使用方法offline()，返回坐席接听方法online()

    
  
  * 新增"来电桌面提醒"功能，可以解决坐席没有佩戴耳机无法听到来电振铃声音，并且呼叫中心页面最小化造成的漏接来电。在您初次登录坐席工作台时，需要您授权同意浏览器显示桌面提醒，强烈建议您开启此功能！如您误操作点击了拒绝，可查看文档 "href='

    https://help.aliyun.com/knowledge_detail/66728.html

    ' target='_blank'" 如何开启来电桌面提醒；
    
  

  




<!-- -->

* 0.1.2(January 25, 2018)

  * 设置loash全局变量隐藏。

    
  

  




<!-- -->

* 0.1.4(January 31, 2018)

  * 新增isAgentReady配置项，设置状态值为"8-5"时是否置空闲

    
  
  * 新增processorJSON配置项，设置json字符串是否再次解析

    
  
  * 解决OnAndOff组件下includes报错

    
  

  




<!-- -->

* 0.1.3(January 30, 2018)

  * 处理自动回到空闲的问题

    
  
  * 处理麦克风错误页面不能点击按钮的问题

    
  

  
  <!-- -->

  * 0.1.1(January 18, 2018)

    * 处理0.1.0版本不能"下线"和"小休"的bug;

      
    
    * 新增autoAnswerCall配置项，设置自动接听通话，单位秒，默认为手动接听。

      
    

    
  

  




<!-- -->

* 0.1.0(January 12, 2018)

  * 在onCallComing和onCallDialing钩子函数中输出录音id(contactId)

    
  
  * 修改logOut约束码

    
  

  




<!-- -->

* 0.0.9(December 28, 2017)

  * 新增afterCallRule配置项，可配置通话结束后自动进入ready状态的时间，默认为15（单位秒），afterCallRule接受量类型参数，一类为时间，一类为"manual"意思为手动控制，传manual时系统不会倒计时进入ready而是直接进入话后处理及时状态

    
  
  * 小休方法applyForBreak增加类型区分，具体参数参考上文

    
  
  * 修复reset样式不起作用导致的浏览器默认样式影响全局样式的bug

    
  

  




<!-- -->

* 0.0.8(December 21, 2017)

  * 新增onStatusChange(code, lastCode, context)的方法

    
  
  * 所有方法的调用增加了状态约束，当不能在该状态调用某个方法时会抛出错误信息

    
  
  * 修改通话中拨号键盘，和通话后再次拨打的弹出拨号层的交互方式

    
  
  * 修复全局reset样式对外部系统的影响

    
  
  * 修复号码删除Icon不显示的问题

    
  
  * 修复defaultVisible设置为false没有隐藏默认面板的问题

    
  

  

* 0.0.7(December 18, 2017)

  * 修复全局样式对外部系统的影响；

    
  
  * 添加二次拨号sendDtmf(number)、通话保持callHold()、通话取回callRetrieve()的方法；

    
  
  * 修改再次拨打的样式bug。

    
  

  



